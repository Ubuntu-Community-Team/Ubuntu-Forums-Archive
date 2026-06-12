---
title: "how to manually configure dpkg in ubuntu 11.10"
date: 2012-07-23
forum: General Help
---

### Post by jpr_iitbombay on 2012-07-23
Dear all,
I had used Ubuntu in the past and now I am switching back to Ubuntu. I am having Ubuntu 11.10. I installed many apps today. All went well except for installing gtalk. After that I thought of installing dropbox. 

I searched for dropbox in synaptic (I think its ok to use synaptic. I prefer it over Ubuntu software center as I can mark all I need and then just do my work so that every thing will get installed). It shoed me 3 options. 1. Drop box. 2. nautilus-dropbox and one more. I marked all of them.  After about 3 hrs when I came back it still said (in the view progress for individial files section)

"[COLOR=DarkOrange]downloading dropbox 29%[/COLOR]"
It was not improving for 30 more minutes. But my internet connection was fine as I can browse the web at usual speeds. So I closed the synaptic. It showed some error. I ignored it and then whatever I tried to install it didnot install. 

for example in terminal if i update by "sudo apt-get update"... it does something for 2 min and then it ends with 

"[COLOR=DarkOrange]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem[/COLOR]."says the following

[COLOR=DarkOrange]prithivi@prithivi-Inspiron-1545:~$ sudo dpkg --configure -a
Setting up nautilus-dropbox (0.6.8-1) ...

Dropbox is the easiest way to share and store your files online. Want to learn more? Head to [http://www.dropbox.com/](http://www.dropbox.com/)

Downloading Dropbox... 29%[/COLOR]

Means it goes directly to setting up nautillus-dropbox and then it goes to dropbox.com again [SIZE=3]ONLY UPTO 29%. [SIZE=2]This is the case all time. 

In software center if i try anything it says [COLOR=DarkOrange]"Waiting for dpkg to exit"[/COLOR] in the progress tab and it just keeps on waiting. 

In synaptic just after entering my login password it says 
[COLOR=DarkOrange]
" Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."[/COLOR]

if I start update manager
it first gives a warning on "Partial Upgrade"
and then it says 

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

I am not able to use wither terminal or synaptic or software center to install anything more. I tried few things in other forum threads but none are that specific to my problem. 

I tried restarting. Still the problem persists...

Kindly help. 
[/SIZE][/SIZE]

---

### Post by jpr_iitbombay on 2012-07-24
Kindly reply plz... I need this info... thanks...

---

### Post by shweta garg on 2012-07-28
Facing exactly same problem in Ubuntu 12.04... Someone plz help...
I am not able to install any software as it is saying 

"[SIZE=3][SIZE=2][COLOR=DarkOrange]Unable to get exclusive lock[/COLOR][/SIZE][/SIZE]"

---

### Post by raja.genupula on 2012-07-28
> Software index is broken

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

do them one by one in your terminal . 
for exclusive lock issue we need total terminal text . so paste it here .

---

