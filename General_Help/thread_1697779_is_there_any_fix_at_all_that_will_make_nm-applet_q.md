---
title: "is there any fix at all that will make nm-applet quit bailing out all the time???"
date: 2011-03-01
forum: General Help
---

### Post by jason.b.c on 2011-03-01
ok i get it , nm-applet has a memory leak , so how do ya fix it ???

i'm tired of leaving the screensaver going for only minutes just to come back to no internet =or= sitting here watching the applet die when downloading something....

---

### Post by mikewhatever on 2011-03-01
How do you know nm-applet has a memory leak?

---

### Post by jason.b.c on 2011-03-01
> **mikewhatever said:**
> How do you know nm-applet has a memory leak?

how do you not? lol

[https://bugs.launchpad.net/elementaryos/+bug/684599](https://bugs.launchpad.net/elementaryos/+bug/684599)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2649106.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2649106.html)

---

### Post by mikewhatever on 2011-03-01
If you have to ask, I am unaffected, apparently.

... and from the link you posted (#50)

> Ok there is just no point in keeping this bug open any longer : the issue is resolved in Natty, the remaining issues appear to be caused by users of some PPA which uses an outdated copy of nm-applet (elementaryart's elementary-desktop PPA, from what I can tell).

Marking Fix Released for Natty.

In Maverick, you can downgrade to the official package from the archive (sudo apt-get install network-manager-gnome/maverick).


---

### Post by jason.b.c on 2011-03-02
> **mikewhatever said:**
> If you have to ask, I am unaffected, apparently.

... and from the link you posted (#50)

well i'm pretty sure that's the one i have already , but to be sure , how do i check?

```
sudo apt-get install network-manager-gnome/maverick
```

i type that exactly?  i ask because the (/maverick) part confuses me slightly..

---

### Post by jason.b.c on 2011-03-02
> **mikewhatever said:**
> If you have to ask, I am unaffected, apparently.

... and from the link you posted (#50)

wait a minute , i already have that version , typed that command in the terminal and output was "already newest version"


why does it keep crashing?????

---

### Post by mikewhatever on 2011-03-02
You can check your version of the network-manager-gnome package with the following command:

```
apt-cache show network-manager-gnome | grep Version
```

...compare it to the one in the repositories:

[http://packages.ubuntu.com/search?keywords=network-manager-gnome&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=network-manager-gnome&searchon=names&suite=maverick&section=all)

---

### Post by jason.b.c on 2011-03-02
bump

---

### Post by matt_symes on 2011-03-02
Hi

```
sudo apt-get install network-manager-gnome/maverick
```

I think your better off using

```
sudo apt-get -t maverick install network-manager-gnome
```

If i remember correctly, this should insure it pulls all the libraries for network manager from maverick and not mix and match the libraries from both sources.

If i have remember incorrectly then hopefully someone will point it out.

Kind regards

---

### Post by jason.b.c on 2011-03-02
> **jason.b.c said:**
> bump

would it be possible to force upgrade to the natty version???

---

### Post by jason.b.c on 2011-03-02
update ...



so i get up and walk away for a few minutes , come back and the screen saver is going , i jiggle the mouse and sure enough - nm-applet died again....



i can restart it fine , but i shouldn't have to ....

---

### Post by matt_symes on 2011-03-02
Hi

If you disable the screen saver does it still crash when left alone ?

Kind regards

---

### Post by jason.b.c on 2011-03-02
> **matt_symes said:**
> Hi

If you disable the screen saver does it still crash when left alone ?

Kind regards

yes....:confused:

---

### Post by jason.b.c on 2011-03-03
bump

---

### Post by jason.b.c on 2011-03-04
bump again

---

### Post by jason.b.c on 2011-03-05
bump again...

wicd don't seem to work for me ..., indicator-network "Was" working but it locks up too much...


what should i do??

---

### Post by jason.b.c on 2011-03-07
bump...

---

