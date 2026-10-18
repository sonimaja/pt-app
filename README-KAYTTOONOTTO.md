# Sofia PT 1.3 · Oura-treenit (kokeilu)

Sovelluksen osoite: https://sonimaja.github.io/pt-app/

## Päivitä

1. Avaa vanhassa Sofia PT:ssä Asetukset > Varmuuskopioi JSON ja tallenna se omaan iCloud Driveen.
2. Pura ZIP-paketti tietokoneella.
3. Avaa GitHubissa sonimaja/pt-app. Korvaa vanhat sovellustiedostot ZIP:n samannimisillä tiedostoilla: index.html, sw.js, manifest.webmanifest ja icon.svg. Valitse Commit changes.
4. Odota GitHub Pagesin julkaisua. Avaa sovellus uudelleen. Päivitä tarvittaessa Safarissa. Tarkista että versio 1.3 näkyy ylhäällä ja vanhat ruokakirjaukset ovat tallella.

## Ouran kirjautumisen valmistelu

1. Avaa https://developer.ouraring.com/ ja kirjaudu omaan Oura-tiliisi.
2. Luo uusi oma API/OAuth-sovellus (nimi esimerkiksi 'Sofia PT').
3. Website: https://sonimaja.github.io/pt-app/
4. Redirect URI: https://sonimaja.github.io/pt-app/ (täsmälleen tämä; lopun kauttaviiva on tärkeä).
5. Kirjautumisen jälkeen kopioi Client ID sovellukseen, EI Client Secret -arvoa. Client Secret -tunnusta ei tarvita client-side OAuth -menetelmässä, eikä sitä saa julkaista.
6. Sofia PT -> Treenit -> Oura -> liitä Client ID -> Yhdistä Oura -> hyväksy vain workout-käyttölupa.
7. Palaa sovellukseen ja paina Päivitä Oura-treenit.

Oura-dokumentaatio kuvaa selaimen client-side OAuth -menetelmän, jossa token on voimassa noin 30 päivää eikä refresh tokenia ole. Sivustolla ei ole erillistä palvelinpuolta. Rajapinnan CORS-tukea ja iPhonen kotinäyttösovelluksen OAuth-paluuta EI ole vielä voitu testata aidolla Oura-tilillä. Jos yhteys katkeaa tai paluu ei toimi, aloita kirjautuminen puhelimen Safarissa suoraan https://sonimaja.github.io/pt-app/ eikä kotinäyttökuvakkeesta.

## Turva ja yksityisyys

- Julkaistava ZIP ei sisällä henkilötietoja eikä Client Secret -tunnusta.
- OAuth-pääsytunnus säilytetään selaimen paikallisessa tallennuksessa, mikä on käytännöllinen mutta EI korkean turvatason salattu salaisuuksien säilytyspaikka. Käytä vain omalla lukitulla laitteella.
- Oura API -haut tehdään suoraan selaimesta Ouralle. Jos Oura estää selainhaun (CORS), sitä ei ohiteta turvattomalla kolmannen osapuolen välityspalvelulla.
- Oura-treenit tallennetaan paikalliseen Sofia PT -päiväkirjaan ja sisältyvät valinnaisesti vietävään JSON-varmuuskopioon; käyttöoikeustunnus EI sisälly varmuuskopioon.
- Päivitys käyttää samaa paikallisen päiväkirjan avainta kuin vanha versio; tiedot eivät saa kadota mutta varmuuskopio on suositeltava.
- Sovelluksen muiden samassa github.io-alkuperässä olevien sivujen skriptit voivat teknisesti lukea saman alkuperän localStoragea. Älä julkaise tai suorita epäluotettavaa koodia samalla alkuperällä.
