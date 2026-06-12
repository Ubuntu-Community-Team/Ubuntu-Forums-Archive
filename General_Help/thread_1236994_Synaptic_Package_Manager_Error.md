---
title: "Synaptic Package Manager Error"
date: 2009-08-10
forum: General Help
---

### Post by carolina on 2009-08-10
In the process of trying to download and install Adobe Flash 10 i get the following message from Package Manager . Can someone help me figure out what to do here ?

  	 	 	 	 	 	   [B]E: /var/cache/apt/archives/libnspr4-dev_4.7.5-0ubuntu0.8.10.1_i386.deb: trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev 
[/B]


[B]Thanks
[/B]

---

### Post by carolina on 2009-08-10
Update:

I tried to run install of Adobe 10 from Debian package installer and message says ;

" Your system has broken dependencies . To fix it run ' sudo synaptic ' or ' sudo apt-get install-f '. Terminal can not find commands ?

---

### Post by razorboy5 on 2009-08-10
ok go back to synaptic 

on ur left tab underneath "all" there should be a "broken" tab

click that and fix whatever package that is broken

i think (sry if this isn't much help)

---

### Post by carolina on 2009-08-11
Tried that but just get the same message .

[B]E: /var/cache/apt/archives/libnspr4-dev_4.7.5-0ubuntu0.8.10.1_i386.deb: trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev 

Tried removing Kompozer application but Add/Remove will not check for programs installed because of broken dependiences . And around and around we go .  :-)

Managed to make a screenshot of changes applied but don't know how to get the image into my post .  :-)





[/B]

---

### Post by carolina on 2009-08-11
**PROBLEM SOLVED**

Was able to delete Kompozer via Package manager and then re-install Adobe 10 . Good to Go .

Sorry for the hassle   :-)

---

### Post by carolina on 2009-08-11
**OOPS , MAYBE PROBLEM NOT SOLVED **

Package manager shows Adobe 10 installed . Firefox plugin shows Shockwave 10 installed . I can view stat graphs on my blog and can upload digital images . JPG images however when uploaded are blank . Dimensions of the image display but not the actual image . Any suggestions ?

---

### Post by zkriesse on 2009-08-11
In exact terms what did you do? I assume you know how to get to the terminal...if so enter this in the terminal.

sudo apt-get -f install

---

### Post by carolina on 2009-08-11
Yes , i did do that but the actual jpg image still does not display after uploading .

---

### Post by zkriesse on 2009-08-11
I assume you are using Jaunty? if so go here... [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download Adobe Flash for Ubuntu 8.04+.deb file. Save the file to your desktop and then enter this into your terminal.

sudo dpkg -i install_flash_player_10_linux.deb

or you could double click on the file...but if you do that then make sure that you opposite click on the file first/go to permissions tab/and click make executable.

---

### Post by zkriesse on 2009-08-11
sorry for what?

---

### Post by carolina on 2009-08-11
Got cut off by local provider ( common here ) . 

I am using 8.10 . The debian pkg i have installed is 10 . When i use the terminal i get the following message :

dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory

---

### Post by vixmusic01 on 2009-09-06
Hi all,

Just wanted to let you know I had the same problem and had to completely delete kompozer to install the update. Synaptic would not delete it until I fixed the broken dependencies.

Seems odd that a broken package cannot be deleted, but maybe it would leave orphaned files that would cause trouble later.

I did fix this problem and now hope the update will install and everything will work.

Thanks for the post.

Victoria

---

