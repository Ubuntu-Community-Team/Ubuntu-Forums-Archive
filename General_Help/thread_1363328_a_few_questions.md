---
title: "a few questions"
date: 2009-12-24
forum: General Help
---

### Post by wwe9112 on 2009-12-24
So I'm new to this whole Linux world so I have a few questions dont judge me if they are dumb lol...

OK, what firewall and antivirus would I go about using?

Also, I had downloaded ubuntu for hosting my own website but I think I downloaded the wrong one I didn't download ubuntu server; is there a way I could easily upgrade it without having to reinstall, and burn to a disk, etc.? 

thank you

---

### Post by Matt__ on 2009-12-24
you dont need antivirus...thats a windows bugbear,
and firestarter firewall is available in synaptic package manager/add-remove

---

### Post by muteXe on 2009-12-24
I dont bother with either. I let my router do the firewalling and viruses dont concern me too badly on my linux machines.

---

### Post by wwe9112 on 2009-12-24
So I don't need an anti virus? And, so what about the server issue

---

### Post by muteXe on 2009-12-24
viruses wont effect your ubuntu at all, but your machine can still act as a carrier if you, for example, give some files to a mate.  If you want to scan for them have a look at clamav in repo's.

Regarding the server stuff, have a read of this first: [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-desktop-vs.-ubuntu-server-462043/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-desktop-vs.-ubuntu-server-462043/)

I dont think you need to reinstall at all.

---

### Post by Matt__ on 2009-12-24
Im sure you could apt-get add packages to make it run like server, but to be honest its probably simpler to burn another disc lol (but then Im a newb too..please someone prove me wrong)
heres the [server documentation]("https://help.ubuntu.com/9.10/serverguide/C/index.html")

---

### Post by wwe9112 on 2009-12-24
> **muteXe said:**
> viruses wont effect your ubuntu at all, but your machine can still act as a carrier if you, for example, give some files to a mate.  If you want to scan for them have a look at clamav in repo's.

Regarding the server stuff, have a read of this first: [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-desktop-vs.-ubuntu-server-462043/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-desktop-vs.-ubuntu-server-462043/)

I dont think you need to reinstall at all.

So where would I go to find the apche php, etc? Sorry if these are dumb I'm just fed up with hosting and would rather just set up my own server but it'll end up being my desktop for the first few weeks or two :P...

---

### Post by lewisforlife on 2009-12-24
> **wwe9112 said:**
> So where would I go to find the apche php, etc? Sorry if these are dumb I'm just fed up with hosting and would rather just set up my own server but it'll end up being my desktop for the first few weeks or two :P...

Here is an excellent guide to installing a LAMP (Linux, Apache, PHP, MySQL) server: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

You don't need server edition to do this.  Basically, Desktop Edition = Server Edition + Desktop Environment.  If you really don't want a desktop environment, then the easiest way to get the server edition would be to burn a disk of the server edition and do a re-install.

I recommend you keep your current install, and later on when you are more comfortable with Linux, and the Linux shell, you can go back and try Server Edition.

---

