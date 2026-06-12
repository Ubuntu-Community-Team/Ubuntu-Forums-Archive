---
title: "Firefox page zoom gives poor image quality"
date: 2010-08-02
forum: General Help
---

### Post by __guppy on 2010-08-02
One of my favorite features of fire fox is the page zoom ( ctrl + / ctrl - ) that zooms the entire page retaining the layout how ever when I installed 10.04 on my main desktop firefox started scaling the images very poorly ( ie no smoothing, leaving the image looking extremely pixelated ).

All threads I've found on the subject seems to related to ubuntu 8, and suggest that a bug fix was underway... hopefully this means there is an easy fix - but what?


info;
Same computer it worked fine on ubuntu 9.xx and windows 7 - when doing desktop zoom (meta + mouse scroll ) the images also scales as expected.
I'm using the 64bit version if that makes a difference.

---

### Post by xpluto on 2010-08-02
did u installed your graphic card ? 
if don't know check:
click on the panel 
system >>administration>> hardware drivers

---

### Post by __guppy on 2010-08-03
> **xpluto said:**
> did u installed your graphic card ? 
if don't know check:
click on the panel 
system >>administration>> hardware drivers


yes I installed the gfx drivers ( nvidia version "current" ), as far as I know desktop effects wont even work with out them.

---

### Post by anishd on 2010-09-09
Same with me. I am attaching a picture of chrome and firefox side-by-side. Left one is chrome right one is firefox, with same zoom level. Firefox image rendering is significantly worse.

---

### Post by BelovBlok11c on 2010-10-17
same prob here :(

---

### Post by ivarn on 2010-10-17
Use the compiz zoom instead. super + mouse scroll

---

### Post by halcyonz on 2010-10-28
Also having this problem, even after doing a fresh reinstall (unrelated). Chrome works well and scales properly but firefox will not. I'm also not partial to using compiz...

---

### Post by jabuci on 2010-11-04
I had the same problem but I could solve it. There is a PPA called  [firefox-smooth-scaling]("https://launchpad.net/%7Efirefox-smooth-scaling/+archive/ppa") which contains a patched version of Firefox. This a [known bug]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908") and it's due to the incorrect EXTEND_PAD implementation in several video drivers. I wrote a more detailed post [here]("https://ubuntuincident.wordpress.com/2010/11/04/firefox-scales-images-poorly/").

---

### Post by littlebuntu on 2011-10-31
[SIZE=3]**Upgrading Firefox to latest version** solved my problem as even after installing my graphic card drivers didn't work. 

Here are the steps that i followed and it worked for me  

[/SIZE][SIZE=3]Step 1. sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]Step 2. sudo add-apt-repository ppa:mozillateam/firefox-stable [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]Step 3. sudo apt-get update [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]Step 4. sudo dpkg -P -a  [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]Step 5. sudo apt-get clean [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]Step 6. sudo apt-get autoclean  [/SIZE]
[SIZE=3] Step 7. sudo apt-get install firefox -$en[/SIZE]
[SIZE=3]
You can replace 'en' in step 7 to any other locale for custom language.

 
[SIZE=2]( credit for the steps goes to [http://www.ubuntugeek.com/how-to-install-firefox-5-on-ubuntu.html/comment-page-1#comment-106434 )]("http://www.ubuntugeek.com/how-to-install-firefox-5-on-ubuntu.html/comment-page-1#comment-106434")[/SIZE]


cheers
[/SIZE]

---

