---
title: "Installing Flash layer for firefox"
date: 2011-12-03
forum: General Help
---

### Post by udunwanan0 on 2011-12-03
ive tried everything and nothing seems to work.... i cant find adobe flash layer on my ubuntu software center.. i installed the .deb file extracted from a .rm file from the site and that still doesnt work. 
HEl LEASE..

as you can see my keyboard is missing a letter...

---

### Post by collisionystm on 2011-12-03
Install Firefox addon flash aid

---

### Post by digithal on 2011-12-03
I would recommend you to install [**FlashVideoReplacer**]("http://www.webgapps.org/add-ons/flashvideoreplacer").

---

### Post by drs305 on 2011-12-03
+1 on Flash Aid. Just a note: I chose the Beta Flash and it's working fine. My wife tried Beta but it didn't work but has had no problems with the stable Flash version offered by Flash Aid.

Machines vary, but I wanted to state that if you try the Beta but it doesn't work for you don't give up without trying the stable version.

---

### Post by oldtimer7777 on 2011-12-03
> **drs305 said:**
> +1 on Flash Aid. Just a note: I chose the Beta Flash and it's working fine. My wife tried Beta but it didn't work but has had no problems with the stable Flash version offered by Flash Aid.

Machines vary, but I wanted to state that if you try the Beta but it doesn't work for you don't give up without trying the stable version.

Flash Aid plug-in for Firefox  +2

Best one out that that solves this kind of issue.

Try to configure it to use the "stable" version of flash.

---

### Post by udunwanan0 on 2011-12-03
I installed flash aid. On my web browser there's the icon for it and everything. I stabled insytalled it but when I restarted firefox but I still can't stream anything on YouTube..

---

### Post by oldtimer7777 on 2011-12-03
> **udunwanan0 said:**
> I installed flash aid. On my web browser there's the icon for it and everything. I stabled insytalled it but when I restarted firefox but I still can't stream anything on YouTube..

You need to go down this following checklist and make sure you have your system correctly installed:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Take your time with it, that is my advice for now.

---

### Post by collisionystm on 2011-12-03
> **udunwanan0 said:**
> ive tried everything and nothing seems to work.... i cant find adobe flash layer on my ubuntu software center.. i installed the .deb file extracted from a .rm file from the site and that still doesnt work. 
HEl LEASE..

as you can see my keyboard is missing a letter...


okay so question is, where did you extract the files to?

The flash plugin is located in

/usr/lib/mozilla/plugins

or for 64 bit

/usr/lib64/mozilla/plugins


it can also be in /usr/lib/firefox/plugins

/usr/lib64/firefox/plugins


the file is called libflash.so

---

### Post by beew on 2011-12-03
> **udunwanan0 said:**
> I installed flash aid. On my web browser there's the icon for it and everything. I stabled insytalled it but when I restarted firefox but I still can't stream anything on YouTube..

What do you mean by "stabled installed it"?  What did you install?

It may be a stupid question but did you run the flash-aid script? (Press the icon, choose wizard mode and then check the boxes, you can choose between the stable version of flash or the beta, right now the beta is working much better for me with accelerated decoding)

---

### Post by udunwanan0 on 2011-12-04
Yeah I did, thats what the stabled installed meant. I stable installed it and restarted firefox but youtube still doesnt work...

---

### Post by lovinglinux on 2011-12-04
> **udunwanan0 said:**
> Yeah I did, thats what the stabled installed meant. I stable installed it and restarted firefox but youtube still doesnt work...

There is an issue in the current version of Flash-Aid, that prevents form installing the stable version. Install the Beta and make sure to disable HWVideo Decode in the tweaking options.

A new version of Flash-Aid is on the works. It should probably be released today.

---

### Post by udunwanan0 on 2011-12-04
How/Where do I tweak the HW thing?

---

### Post by lovinglinux on 2011-12-04
> **udunwanan0 said:**
> How/Where do I tweak the HW thing?

When you launch Flash-Aid Wizard, the Tweaking options will be displayed in the 3rd screen. If there isn't any HWVideo Decode option listed there, is because your card doesn't support it or because you haven't installed vdpau. Then don't worry about it.

Try to install the Beta version anyway.

I am experiencing issues at Mozilla site, so I am unable to upload the new version, but I will upload it to my site soon.

---

### Post by lovinglinux on 2011-12-04
Try version 2.2.2 from [http://www.webgapps.org/add-ons/flash-aid/download-firefox](http://www.webgapps.org/add-ons/flash-aid/download-firefox)

Let me know if it works well or not.

---

