---
title: "cannot  run updates without major errors..."
date: 2009-12-10
forum: General Help
---

### Post by hockey97 on 2009-12-10
Hi, I am stuck with update manager. Out of nowhere I am getting errors spitting out when their is new updates out. I can't update anything... It fails in error.

The error the update manager or dpgk spits out this:

[IMG]http://i50.tinypic.com/2co2cl3.png[/IMG]

This happens when I try to install something or update something or upgrade. 

It seems to be a dpkg error. Not sure. 

How can I fix this cause it's annoying and I want to update to ubuntu 9.10

I currently have ubuntu 9.04 installed.

---

### Post by hockey97 on 2009-12-12
Is this the wrong place to post this?

I just wanted to know what I should do about this. I can't update anything and the updates are piling up.

Any suggestions? I don't want to reinstall the OS again.  I would like to upgrade to the new 9.10 version.

---

### Post by Primefalcon on 2009-12-12
try 

```
sudo apt-get reinstall -f lsb-release
```

---

### Post by wilee-nilee on 2009-12-12
I don't know if this matters but the wireless icon in the screen shot is off.

---

### Post by hockey97 on 2009-12-17
> **wilee-nilee said:**
> I don't know if this matters but the wireless icon in the screen shot is off.

It's not a wireless icon... it's a internet icon. It has a bug in it. I tried to setup the manager to use a hardware line. yet I never got it to function properly yet I still have internet running even when the icon shows it's not running. 

I can open firefox and surf the web... IF you look at the windows minimized you can see I used firefox to post messages on ubuntu fourms...lol so my internet works. 

I just never got to get that icon internet manager working properly. I don't have a wireless card. I only have a eternet card.

---

### Post by hockey97 on 2009-12-17
> **Primefalcon said:**
> try 

```
sudo apt-get reinstall -f lsb-release
```

I gave it a try and it spit out an error saying: E: Invalid operation reinstall.

that is what it spits out when I try that code.

---

### Post by hockey97 on 2009-12-17
Is their a way I could use the live cd to fix this issue?

I notice that even if I downloaded a deb package... when I try to install it I can't I would get the same error. So it's not the update manager it's just the installing the deb packages has this error. I even tried in terminal and I get the same results. I can't install anything. I do have hard drive space about 60gigs of space.

Any Ideas? I thought maybe I should try to use the live cd to try and reinstall that stuff...

just want to know how I could do this. If I used the live cd to reinstall that one file would it reinstall it on my hd? or would it temp reinstall it in memory just temp meaning once I reboot the pc the reinstall changes would disappear and I should have the same problems.

I want to fix this cuz it's bugging me.

---

### Post by kahlil88 on 2010-01-15
> **hockey97 said:**
> I gave it a try and it spit out an error saying: E: Invalid operation reinstall.

that is what it spits out when I try that code.
The proper syntax is:
```
sudo apt-get install --reinstall -f lsb-release
```

---

