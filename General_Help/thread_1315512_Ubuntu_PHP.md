---
title: "Ubuntu PHP?"
date: 2009-11-05
forum: General Help
---

### Post by forensics man on 2009-11-05
[COLOR=black][FONT=Arial][SIZE=3]Some software I was looking at needs me to have [COLOR=#333333][FONT=Arial][COLOR=red]PHP (4-> 2.02, 5-> 2.03)[/COLOR][/FONT][/COLOR][FONT=Times New Roman] installed. I then looked to see if I could download PHP and the site said they dident offer a linux version because most linux distros come with php on them. Does the latest Ubuntu have PHP built in? if so is it up to that version?[/FONT][/SIZE][/FONT][/COLOR]

[FONT=Times New Roman][FONT=Arial][COLOR=black]Thanks[/COLOR][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][COLOR=black]ps I know ...I know.... I am a noobe[/COLOR][/FONT][/FONT]

---

### Post by Giblet5 on 2009-11-05
PHP doesn't install by default.

Use the Synaptic Package Manager. It has a search feature.

If the package is at all popular, it's probably already in Synaptic and will install properly with a mouse click or three.

---

### Post by forensics man on 2009-11-05
> **Giblet5 said:**
> PHP doesn't install by default.
 
Use the Synaptic Package Manager. It has a search feature.
 
If the package is at all popular, it's probably already in Synaptic and will install properly with a mouse click or three.
 
 
I know this is dumb but is Synaptic Package Manager built into Ubuntu? If not no big deal I have found the main site for it , but i thought i would ask.
 
Update.... I found it......sorry please ignore this!!!

---

### Post by forensics man on 2009-11-05
I went in a installed what i think is the PHP 5 package. How can I be sure that was it?

---

### Post by thescubadude on 2009-11-05
As far as I am aware, and I could be wrong, but I think you would want to run php on a webserver like apache. the easiest is to install the entire lamp server. Just make sure you set up a good password for the MySQL.

Apache, php, mysql. 

In terminal type:

[B]sudo tasksel install lamp-server

[/B]Here is a link to the info:[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

