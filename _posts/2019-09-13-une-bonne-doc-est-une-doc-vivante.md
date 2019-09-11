---
layout: post
title: Une bonne doc est une doc vivante
date: 2019-09-13 12:00:00
image: '/images/bonne-documentation/default-activity-diagram.png'
description: Des principles simple s'appliquent aussi à la documentation
category: 'bonne-pratique'
tags:
- documentation
- bonne pratique
twitter_text: Des principles simple s'appliquent aussi à la documentation
introduction: Des principles simple s'appliquent aussi à la documentation
github_username: worming004
linkedin_username: mathieu-scolas-1a048484
twitter_username: worming4
---

# Un article réaction

J'adore reddit, et j'adore [r/ProgrammerHumor](https://www.reddit.com/r/ProgrammerHumor). Mais un [post cette semaine](https://www.reddit.com/r/ProgrammerHumor/comments/d29xjn/documentation/) m'a soulevé une réflexion. Est-ce que swagger est une documentation ? Et si oui, est-ce une bonne documentation ?

De cette réflexion, l'envie de partager sur cette base des bonnes pratiques simple de documentation.

![swaggerdoc](https://i.redd.it/frm61ch4lsl31.png)

# Une documentation

Penchons-nous sur la définition de la documentation selon L'association Association française de normalisation (ISO).
_la documentation est l'ensemble des techniques permettant le traitement permanent et systématique de documents ou de données, incluant la collecte, le **signalement**, l'analyse, le stockage, la recherche, la **diffusion** de ceux-ci, **pour l'information des usagers**.<sup><a href="#reference1">1</a></sup>_

La documentation n'est pas seulement du texte qui décrit votre application. Il est aussi sa manière de le partager, où est-il situé, etc ...
Une [exemple](https://automapper.readthedocs.io/en/latest/Getting-started.html) est une documentation, un [réponse à une question](https://stackoverflow.com/questions/37251043/automapper-throwing-stackoverflowexception-when-calling-projecttot-on-iquery) est une documentation, une [sandbox](https://play.golang.org/) est une documentation.

Aujourd'hui je ne vais pas me pencher sur la rédaction de la documentation (=le contenu), ni même du format d'écriture (= texte, UML), mais de sa position et de ses formes.

## Code as Documentation

Le principe Code as Documentation est uniquement destiné aux développeurs actuels et futures qui améliorent et maintiennent votre application.

Dans le monde réel, la meilleure documentation sont les faits eux-même. Ils ne sont pas discutable car les faits sont intrasèques. Ils ne peuvent être altérés.
En informatique, ça se traduit que le code définit lui même comment la production agit. Le code n'est capable de faire plus ou moins que ce qui est écrit. Il est juste et correcte via sa propriété intrasèque.

Un Code as Documentation se doit être lisible. Il est extrêment important de savoir écrire un code lisible pour faciliter la compréhension **général et détaillé** de l'application. Pas de code spaghetti, de variable incompréhensible, ni de fonctions kilométrique. Je vous renvoie vers les principes Clean Code et Clean Architecture pour atteindre ces objectifs.

Nous sommes très proche d'un concept comme la Production as Documentation. Nous utilisons l'application réel, son design, son intégration en production pour connaitre son état.

Un exemple concret est [Automapper](https://github.com/AutoMapper/AutoMapper). Que fait-il ? Il mappe automatiquement. Pas besoin d'aller plus loin, le nom de projet est suffisant.

_Tip: À chaque fois qu'une discussion commence par "**si** la production agit ainsi", il est nécessaire **d'immédiatement** de levé tous les doutes en effectuant un test ou en lisant le code_

### Implémentation du DRY

Code as Documentation respecte le principe DRY (=Don't Repeat Yourself). Ce principe permet d'assurer que toute information sont sans ambiguité car unique.

Un scénario banal:

* 2017, le développeur sénior développe et documente via une page web son application.
* 2018, le développeur travaille maintenant sur un autre projet.
* 2019, un développeur junior, ne connaissant pas la documentation, met à jour l'application. Sa mise à jour est sans bug, ce bougre est félicité de son travail.

Vous l'avez sûrement pointé du doigt, la documentation n'a pas été mis à jour. Peut-on blâmer ce développeur junior ? Absolument pas. Il n'était pas conscient de l'existence de la documentation, et personne n'était là pour l'épauler dans cette tâche.
Au final, nous avons une **documentation mensongère**. L'application à évolué sans sa documentation.

Cet exemple est simplifié. Je suis sur qu'à un moment ou à un autre, vous suiviez un tutorial ou un documentation non maintenue et que malheureusement votre premier exercice se solde par un échec car la librairie que vous testiez à subit un breaking change.

Nous verrons plus tard comment guider ce développeur junior vers la documentation externe.

## Les documents externes. Diagrammes et textes

Le Code as Documentation seul ne peut suffire. Il y a toujours besoin d'expliquer les communication inter-services, les fail-over strategy, pourquoi les choix ont été pris, etc ...

C'est pourquoi des documents externes au code sont rédigés, et qu'ils sont **indispensable**.
Voici encore quelques principes à respecter pour ses documents externes.

### Keep physically close what is related

Plus un élément est proche de ses relations, plus les probabilités de le retrouver sont grande.

Imaginez github sans fichier readme. Vous ouvrirez le code, et chercherez pendant de nombreuse heures que fait l'application dans ses grande lignes.
La solution serait une documentation externe. Mais elle ne serait jamais atteinte car le repository ne contient aucun lien vers cet doc.

Heureusement, le readme est là. Il a pour double but de:

* Nous expliquer dans les grandes ligne à quoi sert le repository.
* Nous diriger vers les resources externes.

Un exemple concret ? [Automapper](https://github.com/AutoMapper/AutoMapper) nous redirige vers les liens externe.

Les projets open source sont des contre-exemple: les moteur de recherche sont des liens entre la documentation et les librairies. Je pense à la majorité des développeurs qui utilisent google pour rechercher la documentation officiel d'Automapper au lieu de retrouver sa documentation officiel depuis le git.

_Tip: n'hésitez pas à insérer dans votre code un lien vers la documentation qui lui est lié._

#### Pour la petite histoire

Nous sommes aujourd'hui en 2019, la technologie **web facilite grandement la mise à disposition** de n'importe quel resource.
Ça n'était pas le cas précédemment où la diffusion était critique pour n'importe qui. 20 ans plus tôt nous avions dans nos CD de jeu un readme pour nous aider à l'installation ou qui nous donnait des directives. Maintenant, le premier réflexe de n'importe qui est de taper sur google les symptômes du problème. Le liant entre produit et doc est délégué aux moteurs de recherche.

### Outil web pour la documentation

Le web offre toute sa puissance au service de la documentation.

* Facilité de mise à disposition
* Toute le temps à jour
* Au moins 1 navigateur est installé sur un OS moderne. Rien à installer, tout fonctionne.

Finit la documentation versionnées sur clé USB ou sur mail perdue. La seule source de trust est une web app qui n'existe que décrire la dernière version de votre app.

## Sandbox as Documentation

Nous revenons enfin à swagger.

La meilleure façon de comprendre un produit, c'est de l'utiliser.
C'est pourquoi une sandbox ou un environnement d'acceptance est une forme de documentation.

Swagger est aujourd'hui populaire pour compléter la documentation sous forme de sandbox. Il est en quelque sorte un excellent mélange de tout les paragraphes précedents.

* Il est proche du code car c'est une instance du code qui délivre un endpoint swagger. **Keep physically close what is related.**
* Il est intégré au code. Il lit votre API pour délivrer une version simple. **Code as Documentation.**
* Il est généré depuis votre code. c-à-d que votre code reste l'unique point d'information de votre API. **DRY principle.**
* Il est facile d'accès. **Outil web pour la documentation.**

Faites un tour sur leur [démo](https://petstore.swagger.io/#/pet/getPetById). Juste en essayant chaque action vous comprendrez ce que l'on attend dans la requête.
Il est aussi facile à prendre en main, il vous aide via des exemples concret comment intégrer l'API. Ou même vous permet d'immédiatement tester les cas d'erreurs.

En vrai, swagger est une sorte de mix de la documentation moderne.

### Mais le meme est faux ? Swagger est la documentation ultime ?

Pas pour autant. Swagger UI offre une excellente documentation. Mais comme nous l'avons vu précedemment, des ressources plus complètes sont importantes.
Swagger ne peut pas expliquer explicitement les stratégie d'API que vous mettez en place. Ni ses dépendences. Ou encore n'aide pas franchement à l'utilisation de token d'authentification, de sa stratégie de génération, etc ...

J'aimerai profiter de ce paragraphe pour vous donner un retour d'expérience sur l'API Spotify et de sa [console](https://developer.spotify.com/console/).
Ce mode remplit les même objectif que Swagger UI. Mais ça n'est pas tout. Il permet une navigation vers les resources externes, les descriptions sont complètes, ... Bref, Swagger UI mais en mieux :)

## Test as Documentation / Behavior Driven Development

Je voulais aussi parler d'un format spécial de documentation, le BDD.

Le BDD définit le comportement espéré d'une application. Le développeur a pour condition d'acceptance de faire tourner ce test 'en vert'.
Une fois accompli, ce test devient un test de régression. Il assure que les développements futures ne cassent pas les fonctionnalités passés.

Mais ils sont aussi une source de documentation. Il suffit de **lire les cas d'utilisation pour connaitre les comportement de l'application**.

L'exercice est d'une certaine manière renversée. La doc n'est plus rédigé en réponses aux attentes, et decrivent les attentes. C'est aussi une certaine manière de respecter le principe DRY pour la rédaction de cahier des charges. Un test BDD vert décrira toujours la réalité production.

Il n'est toutefois pas facile a exploiter en tant que documentation. Il n'y a pas de moyen hyper pragmatique des les classifier, trier, etc ... Il n'empêche qu'elles sont une bonne source d'information.

# la doc parfaite ?

Il n'y a malheureusement pas de documentation parfaite. C'est une conséquence aux besoins de partage de connaissance: il est nécesaire de documenter tous les niveaux et dimensions d'une application.

Le Code as Documentation sert le détail, la sandbox son intégration, les diagrammes et textes ses stratégies, les tests pour les comportements unique, etc ...

En tant que développeur, nous avons la responsabilité d'assurer que la qualité de la documentation soit au niveaux de notre public.

---

<div class="gratitude">
    <span>MERCI</span>
    <p>d'avoir pris le temps de lire cet article</p>
</div>

---

<div id="toc"></div>
**Table des matières**
1. TOC
{:toc}

#### References

* <p id="reference1"> Accart, Jean-Philippe, Réthy, Marie-Pierre,Le métier de documentaliste, Paris, Éditions du Cercle de la Librairie, 3e édition, 2008, pages 403</p>