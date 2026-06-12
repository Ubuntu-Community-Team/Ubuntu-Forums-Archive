---
title: "Is Medibuntu safe?"
date: 2010-11-16
forum: General Help
---

### Post by chippy_250 on 2010-11-16
Basically what it says on the title?

---

### Post by Verbeck on 2010-11-16
safe how?

helpful link 
[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by WorMzy on 2010-11-16
I would say so. It always has been in the past, and I haven't heard any reports to the contrary.

---

### Post by endotherm on 2010-11-16
from a malware perspective, probably. 
from a legal perspective, it depends. the affect on you of this risk however is nonexistent.

---

### Post by chippy_250 on 2010-11-17
Ok I've just installed Medibuntu on the sortware centre. 
I want to install the codec's basically for wma files so I can play wma songs in Mplayer. 

So I've found the 'Non-free codecs' installer but I'm confused about the add-ons that come with it?
Do I need these....
1. Installer for Microsoft TrueType core fronts 
2.  Installer for Microsoft TrueType core fronts
3. An Mp3 encoding library (frontend)
4.  Installer for Microsoft TrueType core fronts

Three of them are the same thing? What are they, do i need them for playing wma songs?

---

### Post by endotherm on 2010-11-17
not sure what you mean by the non-free installer. 

when I install the mediubuntu repos, this is what I run:

```

#add teh repos and the key  
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

#add sc integration 
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

#install libDVDcss2
sudo apt-get install libdvdcss2 

#install windows codecs (use w32codecs for 32bit ubuntu and w64codecs for 64bit)
sudo apt-get install w64codecs


```then after that i install the ubuntu-restricted-extras package to get a bunch of codecs, codec integration for totem, flashplayer, java, rar/unrar and a number of other small compatibility utilities. 

that is enough to play almost any video file you could want.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by chippy_250 on 2010-11-18
> **endotherm said:**
> not sure what you mean by the non-free installer. 

when I install the mediubuntu repos, this is what I run:

```

#add teh repos and the key  
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

#add sc integration 
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

#install libDVDcss2
sudo apt-get install libdvdcss2 

#install windows codecs (use w32codecs for 32bit ubuntu and w64codecs for 64bit)
sudo apt-get install w64codecs


```then after that i install the ubuntu-restricted-extras package to get a bunch of codecs, codec integration for totem, flashplayer, java, rar/unrar and a number of other small compatibility utilities. 

that is enough to play almost any video file you could want.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I don't really understand. I just did this.
**Adding the Repository**

 The following bash command adds Medibuntu's [repository]("https://help.ubuntu.com/community/Repositories") to Ubuntu. It also adds Medibuntu's [GPG]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") key to your keyring, which is needed to authenticate the Medibuntu packages. 


[LIST]
[*]This command should be run in the [Terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting%20a%20Terminal") (Applications &#8594; Accessories &#8594; Terminal): 
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[/LIST]
Medibuntu's repository is deactivated by [upgrading to a newer Ubuntu release]("https://help.ubuntu.com/community/UpgradeNotes"), so you should run this command again after the release upgrade. 
You  may also wish to add the following packages. The first will cause many  apps from the Medibuntu repository to appear in Ubuntu Software Center  (Ubuntu 9.10+) or Add/Remove Applications (versions prior to 9.10).  The  second will allow users to generate crash reports against Medibuntu  packages and submit them to the Medibuntu bugtracker. 
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntuPlease note you may have to use --force-yes instead of --yes in order for this command to succeed. 


Then after that I went to the Medibuntu software center and downloaded non-free codecs installer. 
It won't play any burnt songs using any of these players; Knome Mplayer, MoviePlayer or Rythembox.

I'm lost now and I really dont understand what i'm meant to do.

---

### Post by endotherm on 2010-11-18
> **chippy_250 said:**
> I don't really understand. I just did this.
**Adding the Repository**

 The following bash command adds Medibuntu's [repository]("https://help.ubuntu.com/community/Repositories") to Ubuntu. It also adds Medibuntu's [GPG]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") key to your keyring, which is needed to authenticate the Medibuntu packages. 


[LIST]
[*]This command should be run in the [Terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting%20a%20Terminal") (Applications &#8594; Accessories &#8594; Terminal): 
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[/LIST]
Medibuntu's repository is deactivated by [upgrading to a newer Ubuntu release]("https://help.ubuntu.com/community/UpgradeNotes"), so you should run this command again after the release upgrade. 
You  may also wish to add the following packages. The first will cause many  apps from the Medibuntu repository to appear in Ubuntu Software Center  (Ubuntu 9.10+) or Add/Remove Applications (versions prior to 9.10).  The  second will allow users to generate crash reports against Medibuntu  packages and submit them to the Medibuntu bugtracker. 
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntuPlease note you may have to use --force-yes instead of --yes in order for this command to succeed. 


Then after that I went to the Medibuntu software center and downloaded non-free codecs installer. 
It won't play any burnt songs using any of these players; Knome Mplayer, MoviePlayer or Rythembox.

I'm lost now and I really dont understand what i'm meant to do.

I've never noticed mediubuntu pushing out an mp3 codec, but your problems should go away if you install this metapackage:
```
sudo apt-get install ubuntu-restricted-extras
```

mediubuntu handles half the codecs/linkers/loaders and the restricted extras cover the rest. do you have that package installed?
not sure what you mean by "burnt songs". what file format are they?

---

### Post by chippy_250 on 2010-11-19
> **endotherm said:**
> I've never noticed mediubuntu pushing out an mp3 codec, but your problems should go away if you install this metapackage:
```
sudo apt-get install ubuntu-restricted-extras
```mediubuntu handles half the codecs/linkers/loaders and the restricted extras cover the rest. do you have that package installed?
not sure what you mean by "burnt songs". what file format are they?

I did what you said and it's says they're already installed. WMA files are what I'm trying to play. But they just don't work.

---

### Post by endotherm on 2010-11-19
> **chippy_250 said:**
> I did what you said and it's says they're already installed. WMA files are what I'm trying to play. But they just don't work.
with wma files, most of them will work, but if the specific file uses the MS "PlaysForSure" DRM, then it won;t work, and there is little we can do about it.

are you trying a wide array of files, or do you just have a few that won't work?

---

### Post by chippy_250 on 2010-11-20
> **endotherm said:**
> with wma files, most of them will work, but if the specific file uses the MS "PlaysForSure" DRM, then it won;t work, and there is little we can do about it.

are you trying a wide array of files, or do you just have a few that won't work?
I've noted down the specific codec for the songs I can't play. They are called: FFWMAV2

---

