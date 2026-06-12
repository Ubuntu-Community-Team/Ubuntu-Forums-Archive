---
title: "Recommended way to install new themes in 12.4"
date: 2012-05-05
forum: General Help
---

### Post by jcobban on 2012-05-05
What is the recommended way to install new themes in Ubuntu 12.4?  The Ubuntu web-site has nothing since 8.4!  The wider web requires installing some 3rd party tool to muck around.

By the way I do not **want** to change my theme.  But I have been told that is the only way to get Firefox to stop mangling web-sites because the new widget set does not have the same dimensions as the pre Gnome3 widget set.

---

### Post by JRV on 2012-05-05
Install ununtu-tweaks, it makes it easy.
Open a terminal and run these commands:```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```
Run the program,select Tweaks=>Theme.

---

### Post by jcobban on 2012-05-06
> **JRV said:**
> Install ununtu-tweaks, it makes it easy.


Thank you.

I am uncomfortable with using a tool which I have to obtain from an outside repository in order to customize my desktop.

[LIST=1]
[*]Some appropriately knowledgeable volunteer should update the Ubuntu web-site with the recommended procedure, since the web-site is currently **four years** out of date in a highly volatile technology.
[*]It would be appreciated if there were an official, integrated, technique for installing themes.
[/LIST]

---

### Post by JRV on 2012-05-06
> **jcobban said:**
> Thank you.

I am uncomfortable with using a tool which I have to obtain from an outside repository in order to customize my desktop.


ununtu-tweak is a high quality, well maintained tool, it is safe.

---

### Post by kyfho23 on 2012-07-12
I will second that. Tulatrix, the developer, is VERY dedicated, has a Twitter feed, and has been very responsive (even eager) to get bug reports, and fix them. 

I was using the "experimental" version of Ubuntu-Tweak for a while, and have used the stable version for about 3-4 yeas, since the project was first announced. 

Ubuntu-Tweak also includes a way of installing some recommended PPAs. THESE ARE SAFE. I have added others. Sometimes, (most of Ubuntu-Tweaks) are repositories maintained by the developer or team that first wrote the code. There is a team that provides updates and new editions of Transmission, the file-sharing app ( you can contribute to Ubuntu by sharing the latest version, it's completely legal). There is also a team that works on LibreOffice.

The advantage is that you can get newer versions and bug & security fixes quicker than waiting for the next release. Ubuntu has attracted a lot of very good people who are creating and adapting software. 

Incidentally, I've never had a security problem with anything I've downloaded from a PPA.

---

### Post by caspbent on 2012-07-12
I understand your hesitation, but I've got full faith in Ubuntu Tweak and I would not hesitate to recommend it. :D

---

