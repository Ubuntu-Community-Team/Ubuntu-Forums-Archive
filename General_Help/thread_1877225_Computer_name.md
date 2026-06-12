---
title: "Computer name"
date: 2011-11-07
forum: General Help
---

### Post by jmacx81 on 2011-11-07
Does anyone know how to change the computer name from the generic one that you set when installing Ubuntu?

---

### Post by lykwydchykyn on 2011-11-07
Edit (with sudo) /etc/hostname and /etc/hosts, and change any instances of your old hostname to the new one.

Then restart.

---

### Post by ballantony on 2011-11-07
Just edit  /etc/hostname and restart your computer

---

### Post by haqking on 2011-11-07
> **lykwydchykyn said:**
> Edit (with sudo) /etc/hostname and /etc/hosts, and change any instances of your old hostname to the new one.

Then restart.

> **ballantony said:**
> Just edit  /etc/hostname and restart your computer

or just

```
hostname <newname>
``` temporarily

if you want permanent then edit the config files above

---

### Post by ballantony on 2011-11-07
Ooh, I didn't know that one.  Thanks, haqking

---

### Post by jmacx81 on 2011-11-07
so in the terminal type sudo /etc/hostname

Is that all?

---

### Post by haqking on 2011-11-07
> **ballantony said:**
> Ooh, I didn't know that one.  Thanks, haqking

no worries, it is useful for a quick fix if you dont want to edit files and restart or for whatever reason you are in a rush, but if you want a permanent solution then you need to edit the correct config files.

Cheers

---

### Post by haqking on 2011-11-07
> **jmacx81 said:**
> so in the terminal type sudo /etc/hostname

Is that all?

no you need to edit those files and you can do that in a number of ways.

gksudo gedit /etc/hostname

sudo nano /etc/hostname

etc or whatever option you choose.  If you dont know how to edit files be careful, as you may mess things up especially doing things as sudo.

cheers

---

### Post by jmacx81 on 2011-11-07
so when I do it am I right by assuming that the /hostname is what I want to change it to?

---

### Post by haqking on 2011-11-07
> **jmacx81 said:**
> so when I do it am I right by assuming that the /hostname is what I want to change it to?

no the /hostname is a file you need to open and edit.

so you use one of the above like

gksudo gedit /etc/hostname

that will open the hostname file in gedit to be edited

there will be a single entry in there which is your hostname, change it and save the file

be careful messing with system files if you dont know how to edit them

---

### Post by jmacx81 on 2011-11-07
well maybe I'll just stick with the generic 78 character name that it has from the setup. I was just wanting something easier.

---

### Post by haqking on 2011-11-07
> **jmacx81 said:**
> well maybe I'll just stick with the generic 78 character name that it has from the setup. I was just wanting something easier.

the name shouldnt be that long ?

type hostname from the terminal

it should show you what your hostname is.

as mentioned above you can change it if you want, just be careful with config files if you are unsure that is all i am saying.

---

### Post by jmacx81 on 2011-11-07
maybe not 78 characters but it is mac@mac-HP-Pavilion-dv7-Notebook-PC:~$

---

### Post by haqking on 2011-11-07
> **jmacx81 said:**
> maybe not 78 characters but it is mac@mac-HP-Pavilion-dv7-Notebook-PC:~$

ahh ok well 31 then, yeah it is a little long i guess.

How often do you need to enter it ? if you want to change your prompt you can with $PS1 ?

if you want your prompt to look different then:

```
PS1="enter name here : "
```

then your prompt will say what you asked it to

but if you want to edit the hostname then as mentioned above.

cheers

---

### Post by jmacx81 on 2011-11-07
Honestly I never need to enter it. Just trying to make it more stylish :) 

Thanks!

---

### Post by haqking on 2011-11-07
> **jmacx81 said:**
> Honestly I never need to enter it. Just trying to make it more stylish :) 

Thanks!

well no one ever sees it unless you have other machines on the LAN, if it is just you then you are likely to only see it at the prompt, which you can change whilst leaving the hostname alone ;-)

---

### Post by jmacx81 on 2011-11-08
Honestly I would have changed it but I opened the editor and had no clue what anything was and it scared me.. ;)

---

