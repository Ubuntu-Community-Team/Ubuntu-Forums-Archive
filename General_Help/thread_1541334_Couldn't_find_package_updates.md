---
title: "Couldn't find package updates"
date: 2010-07-29
forum: General Help
---

### Post by siteregsam on 2010-07-29
Hi,

I had installed Ubuntu server 10.04 and i am trying to install [COLOR=Black]*** Webmin***[/COLOR] for GUI.
When i start with "[COLOR=Blue]sudo apt-get install update[/COLOR]" the following gets displayed...

[COLOR=DarkGreen][I]Reading package list... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package updates

[/I][COLOR=Black]I had configured correct IP address and i am connected with internet....
After googling for some time i figured out that missing repository could cause such problem, which i am not sure.

Kindly help me to troubleshoot this issue...
Thanks in advance...

[/COLOR][/COLOR]

---

### Post by P4man on 2010-07-29
you are telling it to install the package "updates", which doesnt exist. If you want to update your system run
```

sudo apt-get upgrade
```

---

### Post by siteregsam on 2010-07-29
What ever package i try ti install i get the following....

[COLOR=DarkGreen][I]Reading package list... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package [/I][B]<package name>

[/B][COLOR=Black]Do anyone know how to edit repository list in **Ubuntu Server**?
Hope that might work...(its a random guess) 
[/COLOR][/COLOR]

---

### Post by P4man on 2010-07-29
```
sudo nano /etc/apt/sources.list

```

But can you first report the output of
```

sudo apt-get update
```

If there is a problem with the software sources, then that should report it.

---

### Post by evstevemd on 2010-07-29
Didi you mean update manager?
sudo update-manager

---

### Post by evstevemd on 2010-07-29
> **siteregsam said:**
> Hi,

I had installed Ubuntu server 10.04 and i am trying to install [COLOR=Black]*** Webmin***[/COLOR] for GUI.
When i start with "[COLOR=Blue]sudo apt-get install update[/COLOR]" the following gets displayed...

[COLOR=DarkGreen][I]Reading package list... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package updates

[/I][COLOR=Black]I had configured correct IP address and i am connected with internet....
After googling for some time i figured out that missing repository could cause such problem, which i am not sure.

Kindly help me to troubleshoot this issue...
Thanks in advance...

[/COLOR][/COLOR]
Despite my previous post, I think you are supposed to do something like
[COLOR=Blue]sudo apt-get install webmin[/COLOR]

---

### Post by siteregsam on 2010-07-29
> **P4man said:**
> ```
sudo nano /etc/apt/sources.list

```But can you first report the output of
```

sudo apt-get update
```If there is a problem with the software sources, then that should report it.



*I finally found out how to get into a textual mode of "Package manager", but when i try to install packages the system expects a cd with package. I think i have to switch the system to get packages from Internet. How can i do that?*


if i run [COLOR=Blue]*sudo apt-get update*[/COLOR] i am getting the same problem as i mentioned above...

---

### Post by dino99 on 2010-07-29
look at synaptic repo tab: deactivate (uncheck) cdrom and choose to download from main server

---

### Post by siteregsam on 2010-07-29
hi [evstevemd]("http://ubuntuforums.org/member.php?u=1096988"), i am getting the same msg as

[COLOR=DarkGreen][I]Reading package list... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package[/I][/COLOR] [COLOR=SeaGreen][I]webmin


[/I][/COLOR]

---

### Post by dino99 on 2010-07-29
[http://www.webmin.com/](http://www.webmin.com/)

[http://ptgmedia.pearsoncmg.com/images/0131408828/downloads/0131408828.pdf](http://ptgmedia.pearsoncmg.com/images/0131408828/downloads/0131408828.pdf)

[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

---

### Post by siteregsam on 2010-07-29
> **dino99 said:**
> look at synaptic repo tab: deactivate (uncheck) cdrom and choose to download from main server


hi dino99,  

I don't have GUI boss... :(

---

### Post by P4man on 2010-07-29
> **siteregsam said:**
> 
if i run [COLOR=Blue]*sudo apt-get update*[/COLOR] i am getting the same problem as i mentioned above...

Can you post the output nonetheless? I have a hard time believing you'd get a "package not found" error when you run that.

---

### Post by pentegr on 2010-07-29
I have the same problems
> ~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (111: Connection refused)
Err [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_ZA
  Unable to connect to archive.canonical.com:http:
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid Release.gpg
  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111: Connection refused)
...etc ...
Network and internet tests don't pick up any errors, and I've got no problem connecting to any other sites

---

### Post by siteregsam on 2010-07-30
Hi,

 I had installed Ubuntu Server. The user interface is textual. I need to  install GUI(gnome). When i tried to install the package, the system  looks for it from cd rom. Actually i need to fetch the packages from  internet. 

If its a desktop edition of ubuntu then i can do so by removing mark  "Installable from CD-ROM/DVD".

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=ubuntusoftwarecd1.png[/IMG]

How to do the same using commands?
Thanks in advance....

---

### Post by P4man on 2010-07-30
Just edit /etc/apt/sources.list

```
sudo nano /etc/apt/sources.list
```

comment out the cdrom entry. But it being there afaik doesnt prevent you from installing anything from the online repo's. It will just look for the cdrom, not find it and proceed to query the online repositories.

---

