Kort refleksion

I denne opgave har jeg arbejdet med at omsætte et Figma-design til et fungerende website bygget i Astro. Fokus har været på struktur, genbrugelige komponenter og et responsivt layout, der fungerer på tværs af skærmstørrelser.

Udfordringer

En af de største udfordringer var at holde koden simpel, samtidig med at designet havde mange detaljer som overlays, mønstre og komplekse layouts. Særligt arbejdet med grid-layouts og placering af dekorative elementer (fx pseudo-elementer ::before og ::after) krævede justeringer for at fungere både på desktop og mobil.

Derudover krævede det lidt ekstra arbejde at håndtere billeder dynamisk via import.meta.glob, så samme komponenter kunne bruges flere steder uden hardcodede paths.

Successer

Jeg er tilfreds med, at jeg har fået opbygget løsningen med genbrugelige komponenter, fx:

EmployeeCard.astro

Sektioner som Team, Vision og Services

Dynamiske single-view sider baseret på slug

Et eksempel på dynamisk data-håndtering er:

const images = import.meta.glob("/src/data/images/*.{webp,png,jpg,jpeg}", {
  import: "default"
});

og derefter matche billedet til JSON-data baseret på filnavn. Det gør løsningen mere fleksibel og nemmere at udvide.

Jeg har også arbejdet bevidst med semantisk HTML (section, article, header, nav) for bedre tilgængelighed og struktur.

CSS-struktur

CSS er opdelt i:

Global CSS (fx farver, typografi og generelle layout-regler)

Komponent-specifik CSS, som ligger direkte i Astro-komponenterne

Jeg bruger @layer components til at sikre, at komponent-styles ikke konflikter med hinanden, og til at holde koden mere vedligeholdelsesvenlig.

Responsivt design er primært løst med CSS Grid og media queries, fx:

.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

@media (max-width: 640px) {
  .cards {
    grid-template-columns: 1fr;
  }
}

Her tilpasses layoutet uden at ændre HTML-strukturen.

Konklusion

Samlet set har opgaven givet mig en bedre forståelse for, hvordan man strukturerer et større Astro-projekt, arbejder systematisk med komponenter og oversætter et visuelt design til robust, responsiv kode. Jeg har haft fokus på klar struktur, genbrug og læsbarhed frem for unødig kompleksitet.