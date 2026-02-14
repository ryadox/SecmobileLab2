# SecmobileLab2

Objectif : "Comprendre rooting et impacts" ;
Données : "Fictives" ;
Réseau : "Test" ;

utilisation de AVD :: Android Virtual Machine :
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/20c777e6-deb5-47a2-a81b-8071a70fef93" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/f5227122-fb94-4bc6-be9e-09d56ef3ef46" />


Comme dans l'image la commande #adb devices montre a machine android virtuelle ;

..> une errure est servenue :  ( par Gemini LLM : you must create a new AVD using a "Google APIs" system image instead of a "Google Play" one. )
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/509467b1-6208-47e3-ab3a-16844594cb1c" />

On change vers une machine Open Source :

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/f0d3c76a-bb0f-4106-96c0-8a396e251bf0" />

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/c3ad8b65-8300-4c5e-b472-e954b8d3ca93" />

les commandes adb root et adb remount are workingg :: 

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/6f3e29fc-e328-41f1-80d0-cd1daca73447" />

Verification : 

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/ee6ac2a9-6a9f-4df7-afb8-5851baa4a28c" />

Option premessive : 

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/f3c4edd7-7bbe-44d2-b586-3331cf562d75" />

La bonne pratique de journalisation :

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/2e1d9960-3aad-4d8b-b5d4-a178a02a3122" />

L'App utiliser : version : -- final 6 years ago --

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/28eba7a2-9cea-4849-8d85-03b1e225018e" />

Installation (Tricky) : 

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/cb3542a2-39ee-44df-9488-60be8175548a" />

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/32e4d9b5-0ba8-48d1-a567-32e90903adc2" />

Senarios de l'application :: 

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/a09e16dc-abdf-43ab-8d0a-5456672d2c4f" />

<img width="1917" height="1191" alt="image" src="https://github.com/user-attachments/assets/d87e479b-3ff1-4ced-ade6-9d2b03fbd30b" />

Sandboxing des Apps :: 

The Android App Sandbox is a security mechanism that isolates applications from one another and from the system. Each app runs in its own controlled environment with:

A unique Linux user ID (UID)
A separate process
A private file system directory
Restricted access to system resources
By default, one app cannot access another app’s data, memory, or files.

No permissions?
No access.

Permessions :: 

Explain in simple terms:

Normal permissions → granted automatically (e.g., internet).
Dangerous permissions → need user approval (e.g., location, camera, storage).
Introduced from Android 6.0 (API 23) → Runtime permissions.


Isolation :: 

<img width="1023" height="657" alt="image" src="https://github.com/user-attachments/assets/d77c5c2c-5514-4580-97d0-f1e1cdafb16c" />

Le Mécanisme de Verified Boot (AVB)
Concept Simplifié : > Le Verified Boot agit comme un système d'alarme de haute sécurité pour votre appareil. Il vérifie si une entité tierce a altéré les "serrures" ou les "portes" (les partitions système) pendant que l'appareil était éteint. Si la moindre altération non autorisée est détectée, le système déclenche une alerte ou refuse purement et simplement de démarrer.


Fondamentaux Théoriques :: 
Objectif principal du Verified Boot :
Garantir que le système d'exploitation qui s'amorce est strictement celui prévu, compilé et signé par le fabricant (OEM). Cela assure une protection robuste contre l'exécution de modifications malveillantes (telles que les bootkits ou rootkits persistants).

La "Chain of Trust" (Chaîne de confiance) :
Il s'agit d'une série de vérifications cryptographiques séquentielles où chaque composant valide l'authenticité et l'intégrité du composant suivant avant de lui déléguer le contrôle (ex: Bootloader -> Kernel -> OS). C'est analogue à une chaîne de gardiens de sécurité où chaque individu vérifie formellement l'identité du suivant avant de lui faire confiance.

Criticité de l'intégrité au démarrage :
Si le processus d'amorçage est compromis à la racine, toutes les protections logicielles ultérieures (sandboxing, gestion des permissions, mécanismes de l'OS) peuvent être contournées de manière invisible. C'est l'équivalent d'une forteresse imprenable dont la porte principale aurait été compromise avant même le déploiement des gardes.
.
.
.
. 
Etape suivante :: L'Évolution vers AVB (Android Verified Boot)
Concept Simplifié : > AVB (Android Verified Boot) est la version 2.0 du mécanisme de Verified Boot. C'est une évolution majeure, plus moderne et flexible. Concrètement, c'est l'équivalent de passer d'une simple serrure mécanique à un système de sécurité électronique programmable.

Apports Majeurs d'AVB
L'implémentation d'AVB modernise la chaîne de confiance à travers trois points fondamentaux :

Vérification d'intégrité moderne : AVB standardise et centralise la validation cryptographique en regroupant les signatures et les hachages de toutes les partitions au sein d'une seule partition dédiée (nommée vbmeta).

Protection contre le Rollback : L'architecture introduit des compteurs matériels sécurisés (Rollback Indexes) qui lient de manière irrévocable la version de l'OS au matériel physique de l'appareil.

Pérennisation des correctifs : Cette combinaison technique garantit qu'une vulnérabilité corrigée par une mise à jour logicielle est définitivement neutralisée et ne pourra pas être réintroduite.

Focus sur la Protection Anti-Rollback
La protection anti-rollback (ou protection contre la rétrogradation) est une défense critique contre les attaques physiques ou locales persistantes.

Le mécanisme : Cette protection empêche catégoriquement l'installation ou le démarrage d'anciennes versions du système d'exploitation. Si le compteur matériel détecte une version d'OS inférieure à celle attendue, le processus d'amorçage est immédiatement interrompu.

L'enjeu de sécurité : Les attaquants tentent fréquemment de réinstaller d'anciens firmwares (downgrade attacks) dans le but d'exploiter des failles de sécurité connues (CVE) qui ont été corrigées dans les versions récentes.

L'analogie : Pour reprendre l'image précédente, l'anti-rollback agit comme un mécanisme qui empêcherait physiquement quelqu'un de remplacer votre serrure électronique moderne de haute sécurité par un ancien modèle obsolète et facilement crochetable.


Got a problemmm :: 
<img width="1908" height="1200" alt="image" src="https://github.com/user-attachments/assets/0ef48ab7-ac14-4b3f-948e-514cc2699eff" />



Root = privilèges super-utilisateur :: C'est un acces totale au systeme ;
Cela modifie les protections et la confiance du système (rwx for user , group , others )
Utile en laboratoire pour observer certains comportements (pas de restriction par manifacture comme google , samsung , xiaomi , ...)
Risqué, donc nécessite isolement + traçabilité + reset 


"En labo, un environnement privilégié peut aider à…" Observer des artefacts système normalement inaccessibles ;;; 


Matrices des risques ::

<img width="783" height="600" alt="image" src="https://github.com/user-attachments/assets/769169e9-0753-4f58-985b-33b3362f95cc" />


L'OWASP MASVS est le standard méthodologique mondial de référence pour évaluer et certifier la sécurité des applications mobiles.
L'exigence MASVS-STORAGE-1 cible la protection des données au repos et interdit tout stockage local en clair.
Elle impose le chiffrement systématique des données sensibles (tokens, mots de passe) via des composants natifs comme l'Android Keystore.
L'exigence MASVS-NETWORK-1 sécurise les données en transit pour contrer les attaques d'interception de type Man-in-the-Middle.
Elle rend obligatoire l'utilisation de canaux TLS chiffrés avec une validation stricte de la chaîne de certificats du serveur.









