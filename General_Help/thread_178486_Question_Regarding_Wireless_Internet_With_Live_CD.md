---
title: "Question Regarding Wireless Internet With Live CD"
date: 2006-05-17
forum: General Help
---

### Post by Glass Casket on 2006-05-17
So I'm going to boot up later on tonight with the live Kubuntu CD to checka  couple things out. I was simply wondering how, if possible, to get my wireless internet up and running. Because if I change anything in the kernel, I'll have to reboot, but that does on good on the live CD. 

I have a Linksys WRT54G router, and Linksys WMP54GS PCI card.

Thanks!

---

### Post by gitargr8 on 2006-05-17
You need to use ndiswrapper, and the windows driver for your card. You can follow the instructions on [this]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") page, as they worked fairley well for me.

---

### Post by Glass Casket on 2006-05-17
Thanks!

So I'm assuming I need to burn it onto a CD before I boot into the live CD since I won't be able to download it while logged in at first.

Correct?

---

### Post by elamericano on 2006-05-18
It may be useful to have your ndis driver available. With regards to rebooting, you shouldn't need to for any reason. On Kubuntu there is a KWiFiManager pre-installed. Your card might run as soon as you activate it.

---

### Post by xen on 2006-05-19
I am having similar problems after using a LiveCD to make an install, I was expecting linux-wlan-ng or ndiswrapper to be included in the install, but they are NOT, unlike Breezy installs.

So basically i'm stuck!

---

### Post by blakamin on 2006-05-19
[QUOTE=xen]I am having similar problems after using a LiveCD to make an install, I was expecting linux-wlan-ng or ndiswrapper to be included in the install, but they are NOT, unlike Breezy installs.

So basically i'm stuck![/QUOTE]


Are you using Dapper?

---

### Post by Luke on 2006-05-19
to me, it is very bad that dapper liveCD does not include ndiswrapper. anyone know why this was done?

---

### Post by xen on 2006-05-19
[QUOTE=blakamin]Are you using Dapper?[/QUOTE]

Yeah I am, i'm extremely impressed with the results (wanted to do clean install rather than an upgrade from Breezy), only i'm now stuck with no internet.

I have a connection on another PC which I could use but any attempts to find the right files etc has failed, any help is appreciated! (sorry to go off topic)

---

