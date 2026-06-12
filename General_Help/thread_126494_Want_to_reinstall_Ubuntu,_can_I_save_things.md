---
title: "Want to reinstall Ubuntu, can I save things?"
date: 2006-02-06
forum: General Help
---

### Post by Protex on 2006-02-06
Hi guys,

I want to reinstall Ubuntu as Xubuntu, is there a way I can save my settings now and programs now? Like my Cedega, Thunderbird, etc etc? Would I just save my home folder? It's too big for me to just save, can I move it onto another partition? How? Thanks guys!

---

### Post by Leif on 2006-02-06
why don't you just install xubuntu alongside ubuntu ? you know you can do that, right ?

---

### Post by leveliv on 2006-02-06
I dont see why u wouldnt be able to make another partition...but I may be wrong but isnt Xubuntu jsut ubuntu with XFCE :S ....u could just install XFCE or go with the way u are doing...do you have another HD you can use instead of making another partition?

---

### Post by gatorbait on 2006-02-06
tar.gz the directories you wish to save.

---

### Post by sandyeggoboy on 2006-02-07
I have a question .... I want to install one of the new Dapper-Drake releases, adn I ALSO wnt to keep my data intact, but how to do this without formatting the drive? can i just UPGRADE somehow?

---

### Post by nanotube on 2006-02-07
hey protex
you can just install the "xubuntu-desktop" package from synaptic
and that way when you log in in gdm, you can choose xubuntu/xfce session from the list. no need to reinstall.

---

### Post by rock freak on 2006-02-07
[QUOTE=sandyeggoboy]I have a question .... I want to install one of the new Dapper-Drake releases, adn I ALSO wnt to keep my data intact, but how to do this without formatting the drive? can i just UPGRADE somehow?[/QUOTE]

you want to upgrade from breezy to dapper well as far as i no 

sudo apt-get update-distrobution

sud do it and sorry if ive spelt tht rong not my strong point!!!!

---

### Post by Global Havok on 2006-02-07
To upgrade to dapper:

1) Open up a terminal and type "sudo gedit /etc/apt/sources.list" and replace every occurance of the word breezy with 'dapper'.
(This assumes you have just a standard sources.list.  No extra repository's added.

2.) 'sudo apt-get update' in the terminal you opened.

3.) sudo apt-get dist-upgrade (Prepare for a lot of downloading/reconfiguring.)

There is alot more detailed information about upgrading to dapper in the forums (Try the Dapper Drake Development Forum).   But this is the basics of what needs to be done.

---

### Post by BLTicklemonster on 2006-02-07
What will upgrading to dapper in this manner break? I'm ready to take the plunge. Been a while since I totally screwed anything up...

---

### Post by Statik on 2006-02-07
I would like to re-install Breezy over top of my breezy, or something like that. I've had to replace my motherboard, and I have a couple other issues I think will be cleared up, but I don't want to loose my Evolution mail or firefox setup. Everything else can go. Anyone have a quick how-to?

Statik

---

