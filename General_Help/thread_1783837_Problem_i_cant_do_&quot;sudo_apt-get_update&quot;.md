---
title: "Problem i cant do &quot;sudo apt-get update&quot;"
date: 2011-06-16
forum: General Help
---

### Post by kazastyle on 2011-06-16
hi i have a problem after i open software sources i cant do anything and neither open software update manager!Plz Help Me 

Look and the foto:

[http://i200.photobucket.com/albums/aa319/shoce/kkkk.jpg](http://i200.photobucket.com/albums/aa319/shoce/kkkk.jpg)

[IMG]http://i200.photobucket.com/albums/aa319/shoce/kkkffk.jpg[/IMG]

---

### Post by TBABill on 2011-06-16
May have to have a look in /etc/apt/sources.list and see if one of the entries has an error in how it was typed into the file.

---

### Post by coffeecat on 2011-06-16
You have a malformed line in your /etc/apt/sources.list.d/gdm2setup-gdm2setup-natty.list.

Open a terminal and post the output of:

```
cat /etc/apt/sources.list.d/gdm2setup-gdm2setup-natty.list
```What is gdm2setup? I can see it's a 3rd-party repository, but how did you enable it? Link?

By the way, when posting output from a terminal, don't use a screenshot. Highlight the terminal output, right-click and "copy" to copy it into the clipboard. Then paste it into your post with right-click > paste or simply use the ctrl-v keyboard shortcut.

---

### Post by kazastyle on 2011-06-16
i put that out put and it says:

```
cat /etc/apt/sources.list.d/gdm2setup-gdm2setup-natty.list
deb http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu natty main
deb-src http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu natty main
ain
```

---

### Post by coffeecat on 2011-06-16
> **coffeecat said:**
> What is gdm2setup? I can see it's a 3rd-party repository, but how did you enable it? Link?

It's good to get all my questions answered. :wink:

Anyway...

> **kazastyle said:**
> 
```
cat /etc/apt/sources.list.d/gdm2setup-gdm2setup-natty.list
deb http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu natty main
deb-src http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu natty main
ain
```

Open a terminal, and:

```
gksudo gedit /etc/apt/sources.list.d/gdm2setup-gdm2setup-natty.list
```Remove the last line that says only "ain". Don't change any of the first two lines. Now save the file and close gedit. Re-run 'sudo apt-get update'. It should run OK now.

---

### Post by kazastyle on 2011-06-16
Thx Very much its done!! :PPPPP

---

### Post by coffeecat on 2011-06-16
Excellent! Enjoy your Ubuntu. :)

---

