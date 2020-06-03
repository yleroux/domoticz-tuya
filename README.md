# Domoticz Tuya [FR]

Une autre solution pour intégrer des objets Tuya dans Domoticz.

[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)

## Comment ça marche ?
### Step 1 - Obtenir des clés et lié son compte
A force de recherche je suis tombé sur une nouvelle méthode pour récupérer les fameuses Local Key sur cette page [Tuyapi Repo](https://github.com/codetheweb/tuyapi/blob/master/docs/SETUP.md) et la page officiel sur le [Tuya](https://docs.tuya.com/en/iot/open-api/quick-start/quick-start1?id=K95ztz9u9t89n). 
Malheureusement malgré plusieurs essais, je n'ai pas réussi à intégrer de manière fonctionnelle mes prises dans Domoticz.
J'ai fini par trouver une autre solution. Cela existe peut être déjà mais ici c'est ma solution.


1. Créez un compte sur ce site [iot.tuya.com](https://iot.tuya.com). 
2. Enregistrez vos prises dans l'application via votre téléphone  ([Android](https://play.google.com/store/apps/details?id=com.tuya.smart&hl=fr) or [IOS](https://apps.apple.com/fr/app/tuyasmart/id1034649547)). 
3. Une fois le compte validé, cliquez sur "**Cloud Development**" dans la barre en haut puis cliquez sur  "**Create**".  Après avoir créé l'application cliquez dessus pour obtenir vos clés.
4. A partir d'ici ma solution diffère un peu. Dans le menu de gauche cliquez sur "**Linked Devices**". Sélectionnez l'onglet "**Link devices by App Account**". Sur votre téléphone allez dans  "**Profil**" cliquez sur l’icône  "**Scan**". Dans la page web cliquez sur  "**Add App Account**" and scannez le QR code. Votre compte est maintenant lié "_Tuya Cloud_".

### Step 2 - Configure the application
Dans le dossier du script vous trouverez `code.json.model`. Renommez le en `code.json` et complétez le avec les informations Client ID et Client Secret.

![Get Ids](assets/1.jpg)

`{
   "devices":{
      "prise_a":"",
      "prise_b":""
   },
   "client_id":"",
   "app_id":""
}`

La liste des devices est totalement optionnelle pour le moment. Je l'ai ajouté afin de garder en mémoire les ids des prises. Ces derniers se trouvent dans l'application dans les informatins du Device à la ligne ID Virtuel.


### Step 3 - Play with it
Ce script envoi des requêtes au Cloud Tuya pour envoyer des commandes aux prises.


`Options available
main.py --switch <ID> <True|False>
main.py --status <ID>
main.py --toggle <ID>`

## Installation 

Dans votre dossier de scripts Domoticz clonez le repo.

`git clone https://github.com/BreizhCat/domoticz-tuya.git `

Ajoutez le mode éxecutable au fichier main.py.
`chmod a+x main.py`


Dans Domoticz créez un dummy device et sur les actions On & Off appeller le script avec l'option switch True or False.

![Dummy Switch](assets/2.png)



# Domoticz Tuya [EN]

Another way to integrate your switch Tuya to Domoticz

[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)

## What is it?
### Step 1 - Get Keys & Link your account
I have discover this method on [Tuyapi Repo](https://github.com/codetheweb/tuyapi/blob/master/docs/SETUP.md) and also information from [official Tuya website](https://docs.tuya.com/en/iot/open-api/quick-start/quick-start1?id=K95ztz9u9t89n).
Unfortunatly this tutorial did not work well for me and even if I was able to add the devices on my Domoticz server I was not able use them.
After digging a bit I have found few clues and I work on my own solution. 
Perhaps it exists already something like mine.

1. This method requires you to create a developer account on [iot.tuya.com](https://iot.tuya.com). 
2. Register the devices within the Tuya App ([Android](https://play.google.com/store/apps/details?id=com.tuya.smart&hl=fr) or [IOS](https://apps.apple.com/fr/app/tuyasmart/id1034649547)). 
3. After you've created a new account, click "**Cloud Development**" in the top nav bar and click "**Create**".  After you've created a new application, click into it.  The access ID and access key are equivalent to the API key and API secret values need.)
4. From there the solution is a bit different. On the left pan you can see a menu. Click on "**Linked Devices**". On the new page, click on tab "**Link devices by App Account**". Grab your phone and go to "**Profil**" select the "**Scan**" icon on the top rigth. On the web page click on "**Add App Account**" and scan the QR code. Your account is now linked to the "_Tuya Cloud_"

### Step 2 - Configure the application
In the folder you will find a file `code.json.model`. You have to rename it in `code.json`and add your application id and your client id.

![Get Ids](assets/1.jpg)

`{
   "devices":{
      "prise_a":"",
      "prise_b":""
   },
   "client_id":"",
   "app_id":""
}`

Devices is an option added just for memory at this moment. Because to call the script you will need to use these values to toggle the correct switch. These ids are available within the application in Information > Virtual ID. You have to do it on each device.

### Step 3 - Play with it
This python script send request in Tuya Cloud and allow you to switch the device and also to get status of the device.

The python script is just a wrapper and allow you to send the request. 

`Options available
main.py --switch <ID> <True|False>
main.py --status <ID>
main.py --toggle <ID>`

## Installation 

Go to script folder of your installation and clone the repo.

`git clone https://github.com/BreizhCat/domoticz-tuya.git `

Change authorization
`chmod a+x main.py`

Update the configuration file as expected (cf. Configure Application above).

In Domoticz, create dummy switch and add the action on and off on it.

![Dummy Switch](assets/2.png)


