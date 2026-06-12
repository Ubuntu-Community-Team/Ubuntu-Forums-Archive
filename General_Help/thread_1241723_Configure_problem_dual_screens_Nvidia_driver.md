---
title: "Configure problem dual screens Nvidia driver"
date: 2009-08-16
forum: General Help
---

### Post by errolgreer on 2009-08-16
Ubuntu 9.04

I have the Nvidia 7600 GS card with two screens. I installed the recommended driver for this card and went through the config as follows:
Selected X server Display Configuration. Clicked on right screen - configure, Select seperate X server. Set resolutions to 1280x1024 on both screens. Clicked on Enable Xinerama. Clicked on Apply, got message "will enable what is possible. Then clicked on Save to X configuration file. This showed /etc/x11/xorg.conf. Clicked on Save and got the message "Unable to create new X config backup file '/etc/x11/xorg.conf.backup' After quitting and rebooting, the second screen remains off. How can I get past this problem and actually get to save the new settings ? I had no problems doing this before with 8.10, after which both screens worked beautifully.

---

### Post by lessgov2007 on 2009-08-16
I don't know much about trouble shooting separate screens. But it may be it cannot write to xorg.conf without administrator privilege. Also since your using Nvidia, if I'm not mistaken, you can configure two screens with the nvidia-settings tool. Which is rather simple to do, and nvidia-settings can write the needed information to xorg.conf

Try Alt + F2

Type: gksu nvidia-settings

Good luck!

---

### Post by AmerNewbieInDE on 2009-08-16
system - preferences - x server config - x server display config

you can setup a second monitor there, by defalt, my second was turned off

but i didnt configure seperate x server

---

### Post by errolgreer on 2009-08-16
> **AmerNewbieInDE said:**
> system - preferences - x server config - x server display config

you can setup a second monitor there, by defalt, my second was turned off

but i didnt configure seperate x server

Hi, I used sudo nvidia-settings and was then able to save the conf file. However, I now want to select 'display' from the preferences menu, but it tells me "RANDR extension is not present". I want to set my own desktop background picture. How to I enable the RANDR extensions ?

---

### Post by scouser73 on 2009-08-16
Hi, you need to set up dual monitors as root, so paste this command into terminal: **gksudo nvidia-settings**, once you've got the X Server settings program running, configure it to your liking, then click **Apply**, then click **Save to X Configuration File**

---

### Post by lessgov2007 on 2009-08-16
> **scouser73 said:**
> Hi, you need to set up dual monitors as root, so paste this command into terminal: **gksudo nvidia-settings**, once you've got the X Server settings program running, configure it to your liking, then click **Apply**, then click **Save to X Configuration File**
Yeah that's what I also told him.

So I thought I would be helpful and hook up a second monitor to my computer. Well this ancient Compaq box doesn't quite give enough space near the grafix card to fit the second plug in. So I ended up nudging my graphix card out of socket and having to unhook everything, take cover off, and correct it. Damn it man. Then upon restore from hibernate it didn't ask me for a password. Arrg! haha Now I must go figure out why. See what you get when you try helping someone. Now I'm forced to get out my hammer and force this computer into submission. Just kidding... Wonder what the deal is with it not asking for a password.. Hmmmmmm

---

### Post by scouser73 on 2009-08-16
Strange that you've got that automatic login, perhaps it's just a case of unchecking the **Enable Automatic Login**.

---

### Post by lessgov2007 on 2009-08-16
> **scouser73 said:**
> Strange that you've got that automatic login, perhaps it's just a case of unchecking the **Enable Automatic Login**.
Yeah I dunno. It was a random thing too. I hibernated again and the second go around it began asking for the password. I changed absolutely nothing in the system. I'm trying to recreate it incase it's a bug, but so far it's not doing it again. I must have psychicly entered the password. :confused:

Okay enough about that, I don't want to derail the thread.

---

