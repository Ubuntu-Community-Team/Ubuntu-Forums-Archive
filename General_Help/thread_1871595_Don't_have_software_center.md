---
title: "Don't have software center"
date: 2011-10-29
forum: General Help
---

### Post by Mitchellcdck on 2011-10-29
Hi,
I have Ubuntu version 9.04 64 bit, and i've only recently installed it, yet, when i go to install something, it's impossible, BECAUSE I DON'T HAVE THE UBUNTU SOFTWARE CENTER
I've tried getting it to start up in the terminal using gksudo software-center,but that didn't work, and so i'm begging to think that i don't have it at all. It's not in my applications menu, and without it, i can't get wine or flash player to do all the windows things and more. Is there anyway of downloading it? I can't do a print screen bcoz it won't copy the screen. Please answer somebody A.S.A.P.!

---

### Post by westie457 on 2011-10-29
Hi Welcome to the Forum.

The Software centre did not appear with that name until Lucid Lynx was released. You should have Add/Remove... in your applications menu. The other way you can install software is via Synaptic Package Manager found in the System, Administration menu.

Having said that you will not be able to get any security updates and possibly any software without asking on here to enable the repositories. 9.04 went End of Life some time ago and is no longer supported.

Strongly suggest you download 10.04.3 which is a Long Term Support release and has support until some time in 2013.

There will probably be others who will suggest the same thing.

Hope this helps and good luck

---

### Post by Rubi1200 on 2011-10-29
+1 to the advice posted by westie457.

Choose a version with LTS (Long Term Support) and you will have both security and stability.

---

### Post by cgroza on 2011-10-29
Jaunty Jackalope is no longer supported. Even if you get the Software Center, there are no more repositories for it.

Upgrade to a supported Ubuntu Release and your problems will be fixed.

---

### Post by Mitchellcdck on 2011-10-29
where do i go to download a free upgrade that is just a download and don't require a disk or payment or anything?

---

### Post by Mitchellcdck on 2011-10-29
or can i please have the repositories enabled?

---

### Post by linuxuser12345 on 2011-10-29
I believe to update, go to:
System < Administration < Update Manager

---

### Post by oldtimer7777 on 2011-10-29
You can install synpatic package manager:

sudo apt-get install synaptic
sudo synaptic

If you want to check to find any missing parts of your Ubuntu:

sudo apt-get install ubuntu-desktop

If you want to upgrade your Ubuntu to the next version: 

update-manager -d

I truly recommend a fresh installation over an upgrade though:

[https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)


> **Mitchellcdck said:**
> Hi,
I have Ubuntu version 9.04 64 bit, and i've only recently installed it, yet, when i go to install something, it's impossible, BECAUSE I DON'T HAVE THE UBUNTU SOFTWARE CENTER
I've tried getting it to start up in the terminal using gksudo software-center,but that didn't work, and so i'm begging to think that i don't have it at all. It's not in my applications menu, and without it, i can't get wine or flash player to do all the windows things and more. Is there anyway of downloading it? I can't do a print screen bcoz it won't copy the screen. Please answer somebody A.S.A.P.!

---

