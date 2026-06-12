---
title: "Regaining Network Manager"
date: 2010-01-27
forum: General Help
---

### Post by Cunnilingus on 2010-01-27
I deleted network manager while I was hastily attempting to make Ubuntu run faster on my old laptop. I did not realize that I need network manager in order to connect to the internet and now I am in way over my head as I cannot get it back. I tried running "sudo apt-get install network-manager" in terminal but I can't connect to the internet so that won't work. I also tried putting my Ubuntu CD in and then running "sudo apt-cdrom add"
then "sudo apt-get update" and then "sudo apt-get install network-manager network-manager-gnome" but that didn't work either. I'm stumped.

---

### Post by MooPi on 2010-01-27
Go to  ```
etc/apt/source.list
``` comment all of the online sources. Then try to use the CD to install network-manager-gnome. You will need to edit this list after your done so updating will work.

---

### Post by Cunnilingus on 2010-01-27
When I enter ```
sudo gedit /etc/apt/sources.list
``` a window entitled "sources.list" opens up but it is blank.

---

### Post by Cunnilingus on 2010-01-27
Sorry, I just figured it out. How do I comment all of the online sources?

---

### Post by MooPi on 2010-01-27
Try navigating with nautilus to /etc/apt and open sources.list with a right click and gedit.
Comment each line that is an online source with> #

---

### Post by Cunnilingus on 2010-01-27
I'm in sources.list with gedit, but I don't know what to do, it appears to be a load of text that I can't do anything with.
EDIT: Nevermind! I didn't see your post.

---

### Post by efflandt on 2010-01-27
Insert the Ubuntu install CD for your version.  If Synaptic is still installed, open that and add the install CD as a repository (there should be a checkbox for that).  Hit the refresh button in Synaptic (swirling arrows).  Install network-manager-gnome package.

Once Network Connections is back up and working, uncheck the install CD in Synaptic and refresh it (which should grab internet sources again).

---

### Post by Cunnilingus on 2010-01-27
Alright, I just commented all of the online sources. Do I exit the window now?

---

### Post by MooPi on 2010-01-27
```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```Notice the "#" symbol before line that is an online source. You need one on each source.
```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

#deb http://security.ubuntu.com/ubuntu karmic-security main restricted
#deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
#deb http://security.ubuntu.com/ubuntu karmic-security universe
#deb-src http://security.ubuntu.com/ubuntu karmic-security universe
#deb http://security.ubuntu.com/ubuntu karmic-security multiverse
#deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

---

### Post by Cunnilingus on 2010-01-27
MooPi - Do I just exit the window now? Thanks for your help so far!

efflandt - When I try to add the install CD as a repository I get an error saying "failed to fetch:" then it lists a URL.

---

### Post by MooPi on 2010-01-27
Yes , Save and exit. sorry for the delay .

---

### Post by Cunnilingus on 2010-01-27
"Could not save the file /etc/apt/sources.list. You do not have the permissions necessary to save the file. Please check that you have typed the location correctly and try again." ?

---

### Post by MooPi on 2010-01-27
I'm sorry I assumed that you were using admin privileges.

---

### Post by Cunnilingus on 2010-01-27
Well I'm the only one using the computer, I thought I had admin privileges but I guess not. How do I get them? Sorry for putting you through with all this, but I really appreciate your help!

---

### Post by MooPi on 2010-01-27
No problem, I know you tried this once already but lets do it again. ```
sudo gedit /etc/apt/sources.list
```Edit and save. Then try to install network-manager from CD.

---

### Post by psoulocybe on 2010-01-27
```
gksudo gedit /etc/apt/sources.list
```

gksudo for gui applications
sudo for terminal applications

---

### Post by Cunnilingus on 2010-01-27
"Package network-manager is not available, but is referred to by another package."

---

### Post by MooPi on 2010-01-27
Try ```
network-manager-gnome
```
This may sound silly but if I'm helping you online then how are you connected and why can't you just use that connection to update  ?

---

### Post by Cunnilingus on 2010-01-27
I'm not getting anything. Nothing seems like it will work, should I reinstall Ubuntu with the CD?

---

### Post by Cunnilingus on 2010-01-27
I'm using a different computer right now to access the internet..

---

### Post by MooPi on 2010-01-27
Seems like so much waste to just give up. But if you don't loose anything by a reinstall then by all means. Good luck

---

### Post by Cunnilingus on 2010-01-27
I decided to reinstall Ubuntu Karmic 9.10 on my computer because I've only been running it on Ubuntu for a short while (I just installed it about a week ago) so I didn't really have anything major to lose. Thanks for your help though, it's much appreciated and I have ended up learning a great deal more about Ubuntu through my stupid mistake.

---

