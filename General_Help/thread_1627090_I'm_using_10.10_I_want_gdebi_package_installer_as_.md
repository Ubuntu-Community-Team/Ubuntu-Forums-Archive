---
title: "I'm using 10.10 I want gdebi package installer as default?"
date: 2010-11-21
forum: General Help
---

### Post by echoman74 on 2010-11-21
I like using Gdebi package installer instead of ubuntu software center.For one it's too clumpy and slow and takes forever over the web. I had to reinstall Gdebi package installer because i'm used to it! It's simple and fast.My problem is when i want to make it default, I don't see an option and try finding the location. 
I'm pretty much still new to linux but am learning day after day. So to end this post how do i make Gdebi package installer run over the web when installing a new program from the internet?

---

### Post by wilee-nilee on 2010-11-21
If it is a deb package gdebi works automatically, any other type it wont, that is why you can't set it as a default package manager, think for a second doesn't this make sense.;) G**deb**i=deb packages managed. You could right click on a deb package though then set gdebi to be the default.

---

### Post by echoman74 on 2010-11-21
Thank you for your reply I tried that it works but only when I go to the package itself if I save it to my downloads folder.Let me say for example i download real player for Linux.
I go ahead and install and I'm on Firefox. 
The Window comes up an tells me i can install using ubuntu software center, but when i click to try and get page installer to be default i see noting so i click others.from there I'm pretty much stuck. So excuse me if I'm not making sense it's past 2:30 am time for sleep :P

---

### Post by wilee-nilee on 2010-11-21
> **echoman74 said:**
> Thank you for your reply I tried that it works but only when I go to the package itself if I save it to my downloads folder.Let me say for example i download real player for Linux.
I go ahead and install and I'm on Firefox. 
The Window comes up an tells me i can install using ubuntu software center, but when i click to try and get page installer to be default i see noting so i click others.from there I'm pretty much stuck. So excuse me if I'm not making sense it's past 2:30 am time for sleep :P

Get some sleep.;) I think gdebi is for downloads it is not meant to install software center or apt-get or synaptic packages.

I like gdebi as well I always look for a deb if I need a not provided by the OS install.

You really don't want to do anything but download a package if your given the option of, or using a package unpacker. You then have the actual package and can save it if needed. Web loading of a 3rd party I just don't do I download the package.

I see windows users doing web installs of third party stuff and I just chuckle, any third party in windows gets scanned by at least two different av programs for malware, by me. And I'm a open source user I know the safety drill all to well.

---

### Post by oldos2er on 2010-11-21
> **echoman74 said:**
> I'm pretty much still new to linux but am learning day after day. So to end this post how do i make Gdebi package installer run over the web when installing a new program from the internet?

Right-click on a deb file, Properties, Open With, choose gdebi.

If by "over the web" you mean Firefox, Click menus Edit, Preferences, Applications, search 'deb' and change its association to /usr/bin/gdebi-gtk

---

### Post by coffeecat on 2010-11-21
I believe gdebi is not included in a default install with effect from 10.10/Maverick because Software Centre can handle installing downloaded deb packages. However, you can still install gdebi from the repository using SC or Synaptic. You can then set gdebi as the default app for debs in the usual way with a right-click.

---

### Post by mc4man on 2010-11-21
As far as firefox - 2 small points, -  if you want to be asked but have gdebi-gtk (or gdebi, in this case same thing), listed first then do the edit -> preferences -> applications deal twice. first to add/set gdebi-gtk or gdebi, the close/reopen to move back to 'ask'

It's also possible "search 'deb'" won't always produce a result, if not just search software instead

---

### Post by kuric on 2010-12-14
I also prefer Gdebi as default package installer because Ubuntu Software Center is heavy and slow.
I always prefer LIGHTER solutions. **Ubuntu must be light.**

---

