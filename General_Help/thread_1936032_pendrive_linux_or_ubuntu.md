---
title: "pendrive linux or ubuntu?"
date: 2012-03-05
forum: General Help
---

### Post by qwertyjjj on 2012-03-05
Is it possible to install Ubuntu on a USB stick?
If so, what is the best way?
Also, does it have to boot from the USB or is  there a way to run Linux from within a running Windows OS?

---

### Post by seawolf167 on 2012-03-05
> **qwertyjjj said:**
> Is it possible to install Ubuntu on a USB stick?

[UNetbootin]("http://unetbootin.sourceforge.net/"), [Ubuntu]("http://www.ubuntu.com/download/ubuntu/download") (see #2)

> **qwertyjjj said:**
> Also, does it have to boot from the USB or is  there a way to run Linux from within a running Windows OS?

Use a [Wubi install]("http://www.ubuntu.com/download/ubuntu/windows-installer"). Wubiguide [here]("https://wiki.ubuntu.com/WubiGuide"). Or install within a virtual machine, like [VirtualBox]("https://www.virtualbox.org/").

---

### Post by snowpine on 2012-03-05
Easy 1-2-3-4 instructions with screenshots: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by ajgreeny on 2012-03-05
> **qwertyjjj said:**
> Is it possible to install Ubuntu on a USB stick?
If so, what is the best way?
Also, does it have to boot from the USB or is  there a way to run Linux from within a running Windows OS?
Do you want to install the OS to the USB or just use it as a live system, like a Ubuntu Live CD?  Both are possible.

Probably it is best to run it as a live USB system, but with persistence, so any changes you make to the GUI and any files you download or make new will be retained.  The ubuntu **startup-disk-creator** allows you to include persistence in a live system but I am not sure if unetbootin also gives that option; it doesn't appear to do so in my version for ubuntu 10.04.

---

### Post by seawolf167 on 2012-03-05
> **ajgreeny said:**
> I am not sure if unetbootin also gives that option; it doesn't appear to do so in my version for ubuntu 10.04.

At least in the Windows USB creator version it does, they call it "Space used to preserve files across reboots (Ubuntu only)". The max is 4GB if I remember correctly.

---

### Post by ajgreeny on 2012-03-05
> **seawolf167 said:**
> At least in the Windows USB creator version it does, they call it "Space used to preserve files across reboots (Ubuntu only)". The max is 4GB if I remember correctly.
Yes, Ive just searched for the info, and now found a ppa repository for unetbootin in Lucid 10.04 which does have that option; the standard version in Lucid does not, but of course, mine now does have the option, having just updated the version to the ppa's.

---

### Post by holycow131415 on 2012-03-05
Use virtual box for a virtual machine. if you are installing on a pen drive, make sure to use persistence.

---

### Post by qwertyjjj on 2012-03-05
> **holycow131415 said:**
> Use virtual box for a virtual machine. if you are installing on a pen drive, make sure to use persistence.

It's more to try and run it in internet cafes so I don;t have to use the virus ridden Windows OS system that runs in many internet cafes.

---

### Post by idoitprone on 2012-03-05
> **qwertyjjj said:**
> It's more to try and run it in internet cafes so I don;t have to use the virus ridden Windows OS system that runs in many internet cafes.


i recommend puppy linux [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm) lower resources and faster since it runs in ram only
one more thing the security is not the greatest because it always run in root but it does not use much space. You can access ubuntu repos but it takes awhile to set up

---

### Post by seawolf167 on 2012-03-05
> **qwertyjjj said:**
> It's more to try and run it in internet cafes so I don;t have to use the virus ridden Windows OS system that runs in many internet cafes.

In order to boot off the USB drive you need to be able to select a different boot device then the Windows drive after restarting the computer. They will probably have this locked down through BIOS, as I doubt they would want you to be able to modify their computer(s), etc.

---

### Post by snowpine on 2012-03-05
For an internet cafe, you probably want non-persistent (just like a Live CD) so that none of your personal data is stored from session to session.

Also it is good etiquette (in my opinion) to ask the cafe manager's permission before doing this. :)

---

### Post by qwertyjjj on 2012-03-05
> **snowpine said:**
> For an internet cafe, you probably want non-persistent (just like a Live CD) so that none of your personal data is stored from session to session.

Also it is good etiquette (in my opinion) to ask the cafe manager's permission before doing this. :)

I'm starting to think it might be easier just to run Portbale FF and portable Thunderbird...

---

