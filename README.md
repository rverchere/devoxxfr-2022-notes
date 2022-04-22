# Devoxxfr 2022

## Jeudi

### 10:45 - 11:30 Développer des applications observables pour la production

**Salle :** Maillot

**Lien programme :** https://cfp.devoxx.fr/2022/talk/PFT-6511/Developper_des_applications_observables_pour_la_production

**Speaker(s) :**
- Pierre Zemb

**Notes :**

Point sur l'observabilité:

- Retour d'XP sur comment faire de l'astreinte, et changer la manière de développer
- Software is eating the world!
- Le logiciel génère de la valeur quand il tourne en prod, pas quand on le dev
- Que fait le code quand il tourne ?
- Quand on dev, on a une représentation mentale de ce qu'on fait, mais elle peut etre fausse
- Tant qu'on ne mesure pas les algos, on ne peut pas savoir ce qui est le mieux
- Monitoring : est-ce que ça marche ? Oui/Non
- Architecture par service -> distribution des problèmes
- Observabilité: a quel point notre système fonctionne bien ?
- Papillon -> Hurricane : trouver le papillon = debugging

Debugging

- Process qui permet de comprendre le systeme, doit pouvoir se faire en production
- Debugger c'est 3 étapes: se poser des questions, faire des observations, revenir au 1)
- En tant que dev, écrire du code qui permet de répondre aux questions de debug
- code "prod-ready" = code observable

3 méthodes pour debugger : USE, RED, 4 Signals
 - Usage, Latency, Saturation, Errors

 Comment instrumenter:

 - 2 moyens: statique (logs, metrics, traces) & dynamique (ebpf, strace)
 - Logs
  - si possible, mettre la mitigation
- Métriques

Opentelemetry

- merge entre OpenTracing & OpenCensus
- agnostique
- librairie qui commence a être vraiment pas mal
- plus orienté traces pour le moment

Meilleur outil pour détecter les patterns : notre cerveau

Flame graph: utile pour savoir comment s'enchainent les fonctions, et prennent en %CPU

**A voir**
- flamegraph

### 11:45 - 12:30 Dans les coulisses du "Cloud"

**Salle :** 251

**Lien programme :** https://cfp.devoxx.fr/2022/talk/RBN-3952/Dans_les_coulisses_du_%22Cloud%22

**Speaker(s) :**
- Cécile MORANGE

**Notes :**

- Partage sa passion, n'a pas connu le bug de l'an 2000
- Travail chez Aquaray (18 pers), infogérance LAMP. Propre DC, fibre, etc.
- Raconte son quotidien
 - L1 au L3, cablage, etc...
- Explication de ce qu'est un DC : tout et n'imp', tant que ça héberge de la data
- Comment on juge la qualité ? cf TIER
 - tolérance aux pannes
 - redondance
 - clim

Comment on est certifié TIER4?
- Systèmes de regroidissement redondants, topologie cold corridor
- 2 voies électriques
- Redondance réseau (DC propre + redondance sur 2 autres DC - TH2 et Interxion)

Redondance réseau ? On enchaine sur Internet!
- Meme si réseau maillé, y a qd meme une hiérarchie (tier1)
- Qui gère les IP ? RIPE, en EU RIPE NCC

BGP
- 2x plus vieux qe la speakeuse ;)
- Pas de sécurité par défaut (historique, seulement géré par la confiance)
- RFC 7454 donne less bonnes pratiques

Pour sécuriser BGP : RPKI
- Ajout de clé privé pour prouver l'identité de l'AS

Le cas cloudfare: mauvaise annonce BGP

### 13:00 - 13:15 Simplifiez vos revues de code avec le rebase interactif

**Salle :** Maillot

**Lien programme :** https://cfp.devoxx.fr/2022/talk/YOC-8839/Simplifiez_vos_revues_de_code_avec_le_rebase_interactif

**Speaker(s) :**
- Sonia SEDDIKI

**Notes :**

- Merge Request: toujours laborieux car on n'a pas le temps de vérifier que tout est bon
- Niveau 0 "strict minimum": strict minimum (convention, propreté)
- Niveau 1 "historique": trace des développements, contexte

Le rebase interactif : rendre en 1 commit plusieurs commits

plusieurs mots clés:
- pick (par défaut)
- reword: renommer le message de commit
- edit: 
- fixup: reorganiser l'historique

### 13:30 - 14:15 Protéger son organisation des attaques par le système de build

**Salle :** 252AB

**Lien programme :** https://cfp.devoxx.fr/2022/talk/ZWH-7741/Proteger_son_organisation_des_attaques_par_le_systeme_de_build

**Speaker(s) :**
- Louis JACOMET

**Notes :**

- supply chain n'est plus une hypothèse
- exemples de corruption via supply chain : ccleaner, homebrew, solarwinds
- le hack se fait maintenant toujours par manière détournée, via les fournisseurs de soft
- voir "confusing dependencies at scale in 2020 (alex.birsan sur medium)
- Contexte sur l'ensemble des attaques possibles

- Gestion des PR: Attention, il peut meme y avoir des pb lors des jobs de CI sur l'infra lors des tests de PR
 - Seulement build sur l'infra interne après review humaine
- Pull Request Acceptance: CLAs, vérification de l'auteur de la PR, vérif "à la main", ou bien run sur environnement isolé
- Signer les commits!

Améliorer la CI:
- disposable containers, voir build cache

Sur les artfacts: voir l'intégrité  + checksum -> récupérer le binaire d'un côté, le checksum d'un autre !

voir **sigstore** pour la signature des binaires

### 14:30 - 15:15 Cloud public, mais données privées !

**Salle :** 251

**Lien programme :** https://cfp.devoxx.fr/2022/talk/YKJ-2069/Cloud_public,_mais_donnees_privees_!

**Speaker(s) :**
- Gilles SEGHAIER
- MICODE

**Notes :**

- Accélération des "cloud outage"
- Quand 1 cloud provider tombe, si tout les outils sont liés, grosse dépendance, à faire attention
- outage: quand c'est "down" c'est la partie émergé de l'iceberg (gestion des données non dispo)
- leak des données: important aussi

Demo astrachain

### 15:30 - 16:15 Eliminez la complexité de Kubernetes avec LENS !

**Salle :** 241

**Lien programme :** https://cfp.devoxx.fr/2022/talk/RAX-2612/Eliminez_la_complexite_de_Kubernetes_avec_LENS_!

**Speaker(s) :**
- Daniel VIRASSAMY
- Lee NAMBA
- Stéphane MONTRI

**Notes :**

- IDE Kubernetes numero 1
- plus de 100K utilisateurs
- Utiliser k8s pour un dev c'est difficile -> Lens facilite tout cela

- 95% des utilisateurs trouvent que Lens facilite l'adoption et l'apprentissage

- Développé en Electron, facilite les plugins

- tour du propriétaire de l'outil

- voir k0s pour cluster local
- extension debug pod!

### 16:45 - 17:30 Montée de version sans interruption

**Salle :** Amphi Maillot

**Lien programme :** https://cfp.devoxx.fr/2022/talk/DKU-3342/Montee_de_version_sans_interruption

**Speaker(s) :**
- Nelson DIONISI

**Notes :**

- Avant 2017, interruption de service lors d'upgrade : 1h = 125K€ de perte
  1 release tous les 3 mois, grosses montées de version
  Trop de pbs -> migration sans interruption !! Use case de la BDD

- Règle primordiale: version N+1 de la BDD doit etre **retro-compatible** avec la version N de l'application
- En fait, un upgrade se fait en plusieurs étapes, pas d'un seul coup 

- Exemples dans les divers frameworks
- jamais de "select *"

- Sur les applis en fort trafic -> attention aux locks de la BDD
 - Identifier les opérations SQL lentes vs rapides pour optimiser les upgrades
 - ! Foreign key

- mieux vaut casser la migration que l'application

### 17:45 - 18:15 Git, back to the future

**Salle :** Amphi Bleu

**Lien programme :** https://cfp.devoxx.fr/2022/talk/LXE-2783/Git,_back_to_the_future_

**Speaker(s) :**
- Antoine CEOL

**Notes :**

- utilisation de "demo magic"
- git reflog : permet d'avoir les logs mmême après des append
- utilisation de rebaise -i

### 18:30 - 19:00 REX: TDD avec TestContainers

**Salle :** Amphi Bleu

**Lien programme :** https://cfp.devoxx.fr/2022/talk/OCB-6800/REX:_TDD_avec_TestContainers

**Speaker(s) :**
- Julien DURILLON

**Notes :**

- Mise en place du système de facturation
 - zookeeper
 - pulsar
 - postgresql

 Testcontainers: lib java s'intégrant à JUnit et qui pilote du Docker.
 
 - voir sbt


### 20:00 - 20:50 BOF Docker & Kubernetes

**Salle :** 242AB

**Lien programme :** https://cfp.devoxx.fr/2022/talk/ITQ-7092/BOF_Docker_&_Kubernetes

**Speaker(s) :**
- Adrien BLANC

**Notes :**
- Ce qui est dit au BOF reste au BOF ;)

### 21:00 - 21:50 Il y a des cloud en Europe ?

**Salle :** 242AB

**Lien programme :** https://cfp.devoxx.fr/2022/talk/EWW-6942/Il_y_a_des_cloud_en_Europe_%3F

**Speaker(s) :**
- Quentin ADAM
- Horacio GONZALEZ

**Notes :**

## Friday

### 09:00 - 09:20 Futurospective digitale : le futur est-il encore ce qu’il était ?

**Salle :** Amphi Bleu

**Lien programme :** https://cfp.devoxx.fr/2022/talk/BMV-7373/Futurospective_digitale_:_le_futur_est-il_encore_ce_qu%E2%80%99il_etait_%3F

**Speaker(s) :**
- Ludovic CINQUIN (CTO Accenture, ancien PDF Octo)

**Notes :**
- Boule de crystal pour essayer de voir les technos de l'avenir
- L'IA et le cloud sont des sujets 

3 scénarios
- World tech companies
  Puissance des GAFAM, qui font tout pour qu'on le reste chez eux
- Digital Cold Ware
  Chine: population, start up & régime centralisé
  UE: marché et régulation
  USA: domination culturelle & pure players
  Cyber-guerre mondiale ? Avantage à la Chine
- Digital Detox
  Manque de matière première : de plus en plus compliqué d'avoir du matériel

- Vers le right techs -> respet de l'objet, usage, environnement, humain

Le GROS sujet : limites de ressources qui vont changer les usages

Le développeur a une responsabilité: le code écrit aujourd'hui sera l'usage de demain

Hacker : réutiliser les ressources dispos
### 09:25 - 09:45 LesBonsclics, une plateforme pédagogique au service du 1er réseau européen d'aidants numériques.

**Salle :** Amphi Bleu

**Lien programme :** https://cfp.devoxx.fr/2022/talk/SAL-7677/LesBonsclics,_une_plateforme_pedagogique_au_service_du_1er_reseau_europeen_d'aidants_numeriques.

**Speaker(s) :**
- Thomas VANDRIESSCHE

**Notes :**
- WeTechCare : technologie au service de l'inclusion sociale
- 1/6 personnes n'utilise pas Internet
- 68% de Français déclarent avoir des pb pour l'usage du numérique
- Voir le rapport "Monde social et numérique"

- Les bons clics : plateforme pour l'inclusion numérique, avec des howtos, bonne pratiques
 - de la data dispo pour améliorer les usages et etre acteur dans la société

- lien avec les Right Techs

### 09:50 - 10:10 La quête d'une gouvernance collaborative du web

**Salle :** Amphi Bleu

**Lien programme :** https://cfp.devoxx.fr/2022/talk/FHP-4644/La_quete_d'une_gouvernance_collaborative_du_web

**Speaker(s) :**
- Lê Nguyên HOANG (science4all sur youtube)

**Notes :**
- Sujet sur la désinformation ?
- Le problème: on s'informe par ce que les algos leur suggèrent
- voir tournesol (plateforme de fakenews)
- AI est vulnérable: il ne ressort que ce qu'il a appris, et donc si les "entraineurs" donnent de mauvaises infos, l'AI amplifie ces erreurs.
- Plus de faux comptes, c'est plus de fausses voix pour alimenter les IA.
- Notion de vallée parabolique pour ne pas trop forcer les votes

### 10:45 - 11:30 Comment OpenTelemetry peut transformer votre monitoring en unifiant vos logs/metrics/traces

**Salle :** Maillot

**Lien programme :** https://cfp.devoxx.fr/2022/talk/QEB-2923/Comment_OpenTelemetry_peut_transformer_votre_monitoring_en_unifiant_vos_logs%2Fmetrics%2Ftraces

**Speaker(s) :**
- Vincent BEHAR

**Notes :**
- Bosse chez Ubisoft pour proposer une infra interne de services managés
- Implémentation Opentelemetry

- Rappel de ce qu'est un log, métriques, traces
- Jaeger pour visualiser ces traces
- Les 3 piliers de l'observabilité c'est bien, mais ça reste 3 silots car les 3 technos ont leur propres "règles"
- Voir cela comme un cube

Opentelemetry:
- Beaucoup de contributeurs
- couche commune pour tous les acteurs de solutions d'observabilité
- specs, implementations, collecteurs
- OpenCensus service, collecteur - killer feature --> à voir

Collecteur: plateforme de "routage", type logstash
 - permet de récupérer logs, métriques, traces, et les renvoyer vers loki, tempo, prometheus, ...

- Grace aux traces, génération de métriques et logs, mais avec de la corrélation
  Comment choisir entre les métriques classiques & celles générées par le tracing ? Ca dépend


### 11:45 - 12:30 À la découverte des Docker Dev Environments

**Salle :** 252AB

**Lien programme :** https://cfp.devoxx.fr/2022/talk/UQC-0994/A_la_decouverte_des_Docker_Dev_Environments

**Speaker(s) :**
- Guillaume LOURS
- Djordje LUKIC

**Notes :**
- pb git / dépendance de dev, dur d'avoir un environnnement "propre"
- docker est local first, agnostic, le plus simple possible, utilise compose
- Setup : clone d'un code source dans un volume docker, détection de language pour une utilisation d'une image prédéfinie, et ça ouvre dans vscode
- Possibilité de partager les environnements entre devs
- /!\ attention images arm/i686
- Injection du conteneur dans la stack compose

### 13:00 - 13:15 Profiler un pod dans Kubernetes avec kube-flame

**Salle :** 252AB

**Lien programme :** https://cfp.devoxx.fr/2022/talk/XWG-5167/_Profiler_un_pod_dans_Kubernetes_avec_kube-flame

**Speaker(s) :**
- Loïc MATHIEU (Zenika)

**Notes :**
- kubectl flame: profiling de conteneurs en prod, qui génère des flame graphs (projet de yahoo)
- s'installe avec krew
- de branden gregg

- automatise le lancement de profilers, et génère les flames graph au format svg


### 13:30 - 14:15 Les lois universelles de la performance

**Salle :** Maillot

**Lien programme :** https://cfp.devoxx.fr/2022/talk/SLG-6688/Les_lois_universelles_de_la_performance

**Speaker(s) :**
- Raphaël LUTA

**Notes :**
- On parle de système qui est trop lent
- bcp de maths
- Loi d'amdhal
 - faire un calcul, avoir les résultats avant/après parallélisation, on a alors un modèle pour prédire la charge nécessaire
- Anatomie d'une file d'attente (FIFO, etc)
 - Possible aussi de modéliser cela: nb d'élément dans la file, temps d'attente, de traitement, ...
 - Loi de Little
- Loi d'extensibilité universelle, qui prend en compte les perturbations entre les requêtes

- mesure de latence avec wrk2 (ou gatling, ou autre)

### 14:30 - 15:15 Qu'avons nous appris après un an passé à développer des opérateurs Kubernetes ?

**Salle :** 241

**Lien programme :** https://cfp.devoxx.fr/2022/talk/VKR-1767/Qu'avons_nous_appris_apres_un_an_passe_a_developper_des_operateurs_Kubernetes_%3F

**Speaker(s) :**
- Etienne COUTAUD

**Notes :**
- Artifakt : fait un PaaS multicloud
- Sur le PaaS, ajout d'une couche d'asbtraction pour permettre de deployer sur plusieurs types de cloud provider
- Utilisation de k8s pour utiliser les CRDs afin de permettre avoir un point d'entrée de pilotage
- Plusieurs controleurs dans k8s, sur GCP, qui pilotent les CRDs
- En gros, pour déployer des trucs chez Artifakt, on crée un manifest yaml, et basta
- Kubernetes, c'est ni plus ni moins que des boucles de réconciliations

- status: état observé, spec: état désiré

Enseignements:
1) bien définir sa CRD
2) utiliser un framework pour construire le controller
3) mutating webhook: permet de modifier l'objet avant d'intégrer le cluster (ex istio qui ajoute des sidecar containers)

Ils utilisent Terraform à la fin ;)

### 15:30 - 16:15 CI/CD, le divorce serait-il prononcé ?

**Salle :** Maillot

**Lien programme :** https://cfp.devoxx.fr/2022/talk/HBX-3082/CI%2FCD,_le_divorce_serait-il_prononce_%3F

**Speaker(s) :**
- Nicolas GIRAUD
- Yann SCHEPENS

**Notes :**

### 16:45 - 17:30 La fin des architectures en couches avec l’approche hexagonale

**Salle :** Amphi Bleu

**Lien programme :** https://cfp.devoxx.fr/2022/talk/BTP-8595/La_fin_des_architectures_en_couches_avec_l%E2%80%99approche_hexagonale

**Speaker(s) :**
- Benjamin LEGROS

**Notes :**
- orienté pour les juniors, pour ne pas se faire avoir avec les concepts appris à l'école, avec l'approche 3-tiers
- gestion des jsonViews, jsonIgnore, etc... 
- contraintes sur la couche de présentation, service & persistences... donc le modèle 3-tiers n'est plus valide
- de manière empirique, on arrive à faire du DTO

"Ports & Adapters", ancêtre de l'archi hexagonale

- le coeur de l'archi: le domaine
- des ports et des adapters
