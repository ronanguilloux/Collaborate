Prérequis pour l’hébergement et de déploiement de Drupal 
===============================================

Éléments non exhaustifs,  configuration définitive laissée à l’appréciation de l’Hébergeur

* version : 1.0
* auteurs : Ronan Guilloux, Les Polypodes SARL (Nantes, France)
* licence : http://creativecommons.org/licenses/by-sa/3.0/fr/ 


1. But
-----

Pour l’hébergement de sites web ou d’’applications web basées sur le CMS Drupal version 7.x, l'agence Les Polypodes propose un document non exhaustif de pré-requis techniques, à l’intention de l’Hébergeur retenu par le Client.

2. Rôles et vocabulaire 
-----------------------

* L'Agence Les Polypodes est l’agence qui conçoit l’application web,
* l’Hébergeur est responsable de l’hébergement et de l’infogérance éventuelle de l’application livrée,
* le Client final est l'entité qui réalise la commande et la recette l’application et son hébergement.

3. Prérequis généraux liés à l'OS : 
--------------------------------

* OS Linux, dernière version stable (LTS optionnel, pas formellement demandée). Préférence de l'équipe pour Debian ou Ubuntu, nous laissons l’Hébergeur juger de la meilleure distribution à utiliser.
* 1 Core + 8 Giga RAM *minimum*
* architecture 64 bits
* 1 utilisateur linux "polypodes" avec des droits nécessaires pour reloader Apache2 et éditer une crontab ; ajouter si possible cet utilisateur au usergroup utilisé par Apache2 (:www-data)
* un accès FTP
* un accès SSH, idéalement `sudoer` (pas obligatoire)
* une stack LAMP décrite ci-dessous

4. Configuration générale du serveur
---------------------------

La date et l'heure du serveur doivent être configurées sur le fuseau “Europe/Paris”

Version et configuration d'Apache2, PHP et MySQL : La configuration de PHP doit se conformer en tout point aux pré-requis du CMS Drupal version 7.x, dernière version stable de la version 7, y compris tous les pré-requis optionnels. Pour cela, se conformer strictement aux prérequis listés dans ces pages, en retenant les solutions Apache2, PHP et MySQL, en suivant les indications des URL suivantes :

* https://drupal.org/requirements
* https://drupal.org/requirements/webserver
* https://drupal.org/requirements/php
* https://drupal.org/requirements/database
* https://drupal.org/requirements/pdo

Configuration complémentaire de PHP :
PHP (pour apache2 et pour cli)

```
#/etc/php5/apache2/php.ini et /etc/php5/cli/php.ini
(...)
error_reporting = E_ALL
(...)
date.timezone=Europe/Paris
```

Attention à bien achever la *configuration* de certains modules comme APC pour la production, si ces modules ont été installés.

MySQL
-----

L'Hébergeur est responsable de la backup des bases de données et de la bonne configuration des ressources allouées à MySQL.

Prévoir la création et la bonne configuration des droits pour un utilisateur MySQL dédié à Drupal

Logiciels en ligne de commande utiles aux développeurs
------------------------------------------------------

Dans le cadre d'un accès SSH, logiciels à installer :

```
imagemagick rsync git tig vim curl tree lynx ack-grep most exuberant-ctags manpages-fr manpages-fr-extra manpages-dev
```

Logiciels web utiles aux développeurs
-------------------------------------

Applications à installer :

* `phpmyadmin` : L'Hébergeur est responsable de la bonne protection de l'accès à PhpMyAdmin (choix du mode de protection de l’accès à PhpMyAdmin laissé au jugement de l’Hébergeur)

Apache2 
-------

Créer un vhost par environnement (production), en permettant la ré-écriture d'URL (`mode_rewrite`) et en incluant la directive `AllowOverride All`.


2. Limites, conseil et assistance
---------------------------------

En-dehors des points indiqués comme optionnels, tous ces points sont importants et peuvent devenir bloquants pour le succès du déploiement de l’application web basée sur le CMS Drupal 7.x. Sur ces points, l'Agence Les Polypodes demande a être prévenue dès qu'une incompréhension ou un doute survient du côté de l'Hébergeur qui doit livrer l’hébergement et éventuellement assurer l’infogérance de l’application, et se tient prête à expliquer le détail et la raison de chaque pré-requis. 

Il revient au Client Final de créer les conditions et les occasions de dialogues entre l’hébergeur et l'Agence pour la bonne conduite et le succès du projet. 

L'Agence Les Polypodes se tient prêt à planifier des jours supplémentaires de conseils et d'assistance à maîtrise d'ouvrage pour aider le Client Final dans la conduite de ce projet, sur la base d'une prestation de régie de XXX € jour / homme, frais de déplacement non inclus.