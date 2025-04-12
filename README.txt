Un fichier README décrivant le projet, son installation, son fonctionnement, et les routes disponibles

Une collection Postman ou swagger pour tester l'API
API De gestions de stock


<!--INSTALLATION-->
voci les differents commandes pour l'installation du projet 

composer create-project --prefer-dist laravel/laravel nom_du_projet //Creation de nouveau projet
composer require laravel/sanctum //Systeme d'Authentification et protections des Route
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider" //Afficher les fichier de Sanctum

php artisan migrate //pour la migration des table 

<!--FONCTIONNEMENT-->

Liste des Routes test avec posman requette HTTP

1- Requete Inscription

//link: http://127.0.0.1:8000/api/rgister

//Exemple d'insertion de donnees format JSON

__POST /api/register avec :__ s'inscrire
{
  "name": "Admin",
  "email": "admin@example.com",
  "password": "secret1234",
  "password_confirmation": "secret1234"
}

1- Requete Connexion

__POST /api/login avec :__ se connecter
{
  "email": "admin@example.com",
  "password": "secret"
}

__Cela renverra un token que tu dois inclure dans les requêtes protégées :__  dans  Authorization: Bearer VOTRE_TOKEN_ICI

Avec le token vous pouvez gerer les differentes requetes telles que:

 __la Gestion des produits__
 Tester /api/produit avec le token 
 Authorization: Bearer 1|Xb32sdfiQo...nG78qv

-link: http://127.0.0.1:8000/api/produits


__GET /api/produits :__ Afficher la liste des produits

__POST /api/produits :__ Ajouter un produit la liste des produits
{
  "nom": "Clavier",
  "description": "Clavier hp zbook 14u",
  "prix": 17500,
  "quantite_initial": 10
}
__PUT /api/produits/{id}__ pour modifier le produit
{
  "nom": "Clavier",
  "description": "Clavier hp zbook 14u",
  "prix": 17500,
  "quantite_initial": 17
}

__DELETE /api/produits/{id}__   //pour Supprimer le produit

 __la Gestion des entrees__

 Tester /api/entrees avec le token
 Authorization: Bearer 1|Xb32sdfiQo...nG78qv
Exemple : POST /api/entrees
URL : http://localhost:8000/api/entrees

{
  "produit_id": 1,
  "quantite": 10,
  "date_entree": "2025-04-12T14:20:00Z"
}

 __la Gestion des sorties__

 Tester /api/sorties avec le token
 Authorization: Bearer 1|Xb32sdfiQo...nG78qv
Exemple : POST /api/sorties
URL : http://localhost:8000/api/sorties

{
  "produit_id": 1,
  "quantite": 10,
  "date_sorties": "2025-04-12T14:20:00Z"
}

 __la Gestion l'etat du stock du produit__

 Tester /api/produits/{is}/etat avec le token
 Authorization: Bearer 1|Xb32sdfiQo...nG78qv
Exemple : GET /api/produits/1/etat
URL : http://localhost:8000/api/produits/1/etat









