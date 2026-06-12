---
title: "Adobe flash not installing"
date: 2012-04-23
forum: General Help
---

### Post by isaac12345 on 2012-04-23
Hi all!

I have been recently having problems on youtube where the videos dont run properly. I then tried grooveshark and it said that I needed to update my flashplayer. So I went to the adobe website and downloaded the APT from there. It opened in ubuntu software centre. I clicked on install and then it gave me an error saying "Failed to download  package files. Check your internet connection",even though my internet was working just fine. It gave the following details for the error :

Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.228-0oneiric1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.228-0oneiric1_i386.deb) 404  Not Found [IP: 91.189.92.191 80]
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.228-0oneiric1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.228-0oneiric1_i386.deb) 404  Not Found [IP: 91.189.92.191 80]

Any idea why its doing so and how to fix it?

---

### Post by growingneeds on 2012-04-23
Hi.

The common practice for a new user of Ubuntu is to install the package ubuntu-restricted-extras. Amongst other useful multimedia options, it enables the installation of Adobe Flash. Please try this in terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Good luck.

---

### Post by techsupport on 2012-04-23
> **isaac12345 said:**
> Hi all!

I have been recently having problems on youtube where the videos dont run properly. I then tried grooveshark and it said that I needed to update my flashplayer. So I went to the adobe website and downloaded the APT from there. It opened in ubuntu software centre. I clicked on install and then it gave me an error saying "Failed to download  package files. Check your internet connection",even though my internet was working just fine. It gave the following details for the error :

Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.228-0oneiric1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.228-0oneiric1_i386.deb) 404  Not Found [IP: 91.189.92.191 80]
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.228-0oneiric1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_11.2.202.228-0oneiric1_i386.deb) 404  Not Found [IP: 91.189.92.191 80]

Any idea why its doing so and how to fix it?

Also if that doesn't work you can try Flash Aid for Firefox plugin. That sometimes helps.

---

### Post by Gyokuro on 2012-04-23
Hi,

or you can download flash*.tag.gz unpack it and copy the flashplugin.so file to ~/.mozilla/plugins/ (you have to make this directory in case you do not have it).

---

### Post by Gremlinzzz on 2012-04-23
I needed to update my flashplayer:popcorn:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
get the one with tar.gz on the end
in download folder right click flashplayer choose extract here
open folder right click on libflashplayer.so choose cut or copy
go to Home folder at the top you will see file / edit / view
click on view and check show hidden files
find the folder .mozilla open folder 
inside there should be a plugins folder open and paste libflashplayer.so
inside plugins folder this will update flashplayer
if the plugins folder is not there create a folder and name it plugins
:popcorn:

How to create a folder once inside .mozilla folder right click anywhere and choose create folder name it plugins

---

### Post by Gremlinzzz on 2012-04-23
That should cover updating Flashplayer. will flashplayer work better with the update? I don't know ,I've never had any problems with the newer flashplayer plugin:popcorn:

---

### Post by Gremlinzzz on 2012-04-23
> **Gremlinzzz said:**
> That should cover updating Flashplayer. will flashplayer work better with the update? I don't know ,I've never had any problems with the newer flashplayer plugin:popcorn:

Good thing about updating flashplayer plugin this way.is that if the new update creates problems! just delete what you did and you will have your old plugin back.:popcorn:

---

