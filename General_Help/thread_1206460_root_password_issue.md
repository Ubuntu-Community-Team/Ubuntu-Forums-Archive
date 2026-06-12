---
title: "root password issue"
date: 2009-07-07
forum: General Help
---

### Post by roschell on 2009-07-07
I just successfully installed Xubuntu on Dell C400 from Ubuntu mini .iso through download, however I seem to have problem with root password.

The only password I remember selecting was for a first user. When I want to add another user I cant get into the root shell for making advanced changes.

Following I tried these:

1. 
- restart system with kernel added command **rw init=/bin/bash**
  then **passwd root** which moved on to retype your password just after first letter input. So I assumed the password is set to ¨r¨ as I got password successfully changed 
- after restart this proved to be wrong, still no root access

2.
- restart as a single user by adding **, single** to the kernel,
  situation went similarly to the case 1. but resulting in password   unchanged 
- after this attempt I am unable to get into the system even with first user account

I should mention also the pc has debian and xp still on it as I was interested to see if xubuntu will run well. 

Thanks for your help

---

### Post by nothingspecial on 2009-07-07
See [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by roschell on 2009-07-07
it seems this is only information on How to sudo and perhaps its difference to root account in comparison to other OSs.

The commands I did exercise are commands related to Ubuntu, Xubuntu respectively. Which for some reason, even after agreeing, still do not work. 

Therefore I am asking for help to resolve my issue if possible...? 
I do use Mandriva for my work however that OS does not run on the discussed C400 laptop. This being the reason I am giving a go to xubuntu on my sisters laptop

---

### Post by roschell on 2009-07-07
Further, the policy you referencing to does not provide commands I am confident to use in relation to their relevance and results.

More help would be greatly appreciated.

---

### Post by CrazyMonkeyFox on 2009-07-07
Look dude, on these forums I'm 99.9% sure you aren't gonna get the command you want. Its against the policy to post it. If you're really desperate, and I don't advise this, just google it, it does come up.

---

### Post by mcduck on 2009-07-07
You don't need root for anything, and if you are counting on getting help on these forums you shouldn't enable it even if you know how to do it (as the forum policy is to support Ubuntu's security model which doesn't use direct root access). Anything you need to do with root permissions can be done with "sudo" (or "gksudo" & "kdesu" for graphical applications). If you need a root terminal, run "sudo -i".

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

Anyway, to fix your problem and get you back where you started, can you select recovery mode from the Grub menu? If that works, select root terminal when prompted for what you wish to do, and then run "passwd -l root" to lock the root password again.

---

### Post by nothingspecial on 2009-07-07
```
sudo adduser yoursister
```

If you want to give her admin privaledges
```

sudo adduser yoursister admin
```

Now she can use sudo too

---

### Post by kerry_s on 2009-07-07
root is locked for a reason, using it cuts security in half, a cracker will only have to crack the password. with a user using sudo, they must guess the log in name & the password.
if you have to be root you can> **sudo su**

---

### Post by roschell on 2009-07-07
perhaps I meant sudo password and used root term since coming from Mandriva. About the differences on Ubuntus family I should be aware since I used to use Ubuntu for awhile. This for some reason at that moment possibly dropped of my mind. 

Anyway..
I am trying to input some of the commands now...

---

