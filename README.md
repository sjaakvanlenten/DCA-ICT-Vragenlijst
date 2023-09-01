# Vragenlijst DCA-ICT

Lever de antwoorden in een git-repository aan; je kan deze repo 'clonen' en aanvullen indien gewenst.

## Wat is het verschill tussen 0, NULL, ‘’ en undefined

Leg dit uit in een (webdevelopment) taal naar keuze, bijvoorbeeld PHP of JavaScript.

```js

//de variabele heeft hier de numerieke waarde 0
const num = 0

//deze variabele is gedeclareerd, er is null als speciale waarde toegewezen die aangeeft dat er opzettelijk geen waarde is.
const noValue = NULL

//Deze bevat een empty string, ofwel geen tekst.
const myString = ''

//In dit geval is de variabele gedeclareerd, maar deze is niet toegewezen aan een waarde dus wordt deze "undefined"
const variable

```

## Maak deze implementatie af

In deze PHP-implementatie hebben we een 'vast' wachtwoord (`$wachtwoord`) en een pseudo ingevuld wachtwoord door een gebruiker (`$gebruikerinvoer`).
Uiteraard komen we in de exit; terecht, de variabelen ('wachtwoorden') zijn niet gelijk.

Herschijf deze implementatie; hash het `$wachtwoord` variabele en zorg dat deze gecontroleerd kan worden op basis van de plaintekst invoer (`$gebruikerinvoer`)

```php
<?php

#zorg dat deze variabele gehast is
$wachtwoord = password_hash("Welkom01!", PASSWORD_DEFAULT);

$gebruikerinvoer = 'Doei02!';

#deze vergelijking moet uiteraard blijven werken, eventueel in gewijzigde vorm
if(password_verify($gebruikerinvoer, $hash)) {
    inloggen();
} else {
    throw new Exception('Wachtwoord onjuist');
    exit;
}
?>

```

Het wachtwoord wordt eerst gehasht door middel van password_hash()
In het if statement wordt vervolgens het ingegeven wachtwoord gecontroleerd tegen de hash van het wachtwoord met password_verify().
Indien dit een true teruggeeft, wordt de gebruiker uiteraard ingelogd.

## CSS specificity hierarchy

Leg van elk element in de `<body>` uit welke kleur de tekst en de achtergrond krijgt.

**Doe dit uit je hoofd, draai deze code niet.**

```html
<style>
  div,
  span {
    background: #ff0000;
    color: white;
  }
  div.geel {
    background: #ffff00;
    color: #ff0000;
  }
  div#head {
    background: #0000ff;
  }
  div#wrapper * {
    background: #ffffff;
    color: black;
  }
</style>
<body>
  <div class="geel" id="head">
    <span class="titel">Hoi</span>
    <span class="body">DCA-ICT</span>
  </div>
</body>
```

De omringende div heeft een class "geel" en een id "head". de id krijgt hierbij de voorrang boven de class van deze div. Dus in dit geval heeft de div een blauwe achtergrond kleur. De beide span elementen krijgen hier de stijl van de generieke span css mee, omdat in dit geval de css classes "titel" en "body" niet bestaan. Dus deze krijgen beide een achtergrond kleur van rood en de tekst wordt wit.

## Recursie

Wat is recursie en geef een voorbeeld (of implementatie) waar dit nuttig kan zijn

Recursie is binnen het programmeren een functie die zichzelf aanroept om tot een bepaalde oplossing te komen.
Het optellen van een array met numerieke waardes kan bijvoorbeeld door middel van recursie:

```js
function sum(arr, n) {
  if (n <= 0) return 0; //zodra de base van 0 is bereikt stopt de recursie en kan de optelsom gemaakt worden

  if (n > arr.length) {
    // als er een n gegeven wordt die buiten de range is van de lengte van de array, dan wordt automatisch de maximale lengte voor n aangehouden.
    n = arr.length;
  }

  return sum(arr, n - 1) + arr[n - 1];
}

const a = [7, 5, 3, 10, 2];

console.log(sum(a, 4));
```

In dit geval worden de eerste 4 getallen van de array opgeteld, dus is de output: 25.

## Client-side vs server-side

Wat is het verschil tussen client-side code (denk aan JavaScript in de browser) en server-side code en geef aan hoe je interactie voorziet tussen die twee.

Client-side code wordt gerund op de computer van de gebruiker, meestal in een webbrowser. Dit omvat alle HTML, CSS en JavaScript.
Verder verzorgt deze de weergave en interactie van de webpagina op de computer van de gebruiker. Bijvoorbeeld klikken en typen. Deze code is direct beschikbaar voor de gebruiker en kan snel reageren op gebruikersacties zonder dat er communicatie met de server nodig is.

Server-side code wordt daarentegen uitgevoerd op een webserver. Dit kan bijvoorbeeld geschreven zijn in PHP, node.js, python enzovoorts.
Deze is code voornamelijk verantwoordelijk voor het verwerken van aanvragen van de client. Het uitvoeren van complexe berekeningen en het opvragen van gegevens uit een database. Ook omvat dit de beveiliging en autorisatie.

Hoe de interactie verloopt tussen deze 2 kan door middel van een http-verzoek die de client stuurt naar de server om gegevens op te halen. Dit gebeurt meestal met behulp van AJAX-verzoeken in JavaScript. De server kan ook API's aanbieden waarmee de client gegevens kan ophalen of bewerkingen kan uitvoeren op de server. De gegevens worde in gestructureerde formats als JSON verzonden.
Ook kan er door middel van Websockets een direct communicatiekanaal tussen de client en server worden opgezet, waardoor er realtime interactie plaatsvindt zonder dat de client telkens nieuwe verzoeken hoeft te sturen.

## Definitie van een loop

Geef drie voorbeelden van een loop en implementeer er een naar keuze;

Opmerking: Niet helemaal duidelijk deze vraag. Om nou 3 voorbeelden te noemen van loops zijn dit de for-loop, de while-loop en de do-while-loop.
Ik heb voor deze opdracht voor een for-loop gekozen met binnenin een if-else structuur om de diverse scenario's af te handelen.

```js
for (let i = 1; i <= 100; i++) {
  const isDivisibleBy3 = i % 3 === 0;
  const isDivisibleBy5 = i % 5 === 0;

  let output = "";

  if (isDivisibleBy3 && isDivisibleBy5) {
    output += "DCA-ICT";
  } else if (isDivisibleBy3) {
    output += "hoi";
  } else if (isDivisibleBy5) {
    output += "DCA";
  } else {
    output = i;
  }

  console.log(output);
}
```

- Toon de nummers 1 t/m 100
- Indien deelbaar door 3; toon de string "hoi" in plaats van het nummer
- Indien deelbaar door 5; toon de string "DCA" in plaats van het nummer
- Indien deelbaar door 3 en door 5; toon de string "DCA-ICT" in plaats van het nummer

## Lineair search

Implementeer een lineaire zoekfunctie in een webdevelopment taal naar keuze; bijvoorbeeld PHP.

```js
function lineairSearch(array, target) {
  for (let i = 0; i < array.length; i++) {
    if (array[i] === target) {
      return i; // Teruggeven van de index waarop het doel is gevonden
    }
  }
  return -1; // Teruggeven van -1 als het doel niet is gevonden
}

// Voorbeeldgebruik:
const a = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5];
const targetNum = 9;

const result = lineairSearch(a, targetNum);

if (result !== -1) {
  console.log(`Het doelgetal ${targetNum} is gevonden op index ${result}.`);
} else {
  console.log(`Het doelgetal ${targetNum} is niet gevonden in de array.`);
}
```
