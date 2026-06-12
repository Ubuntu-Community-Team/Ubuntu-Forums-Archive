---
title: "Yahoo Messenger (ymessenger) and ubuntu?"
date: 2005-03-10
forum: General Help
---

### Post by frozenfroot on 2005-03-10
hello all

i run an internet cafe in nyc with a friend. we currently run 90% linux boxes in our cafe (mandrake 9.2) and would like to switch to ubuntu...

we will be running ubuntu on ibm thinkpad 600E computers (which works great sofar)

we are having one problem - yahoo.

we would prefer to just offer gaim (which we both love), but some of our customers are addicted to damn YAHOO!

i have tried to install the debian packages from the yahoo download site using dpkg - but i run into a problem with libssl0.9.6 (which is a missing dependency)

i tried to install libssl0.9.6 but can't get it to work. i used the ./configure then make then make install route on the library, but it is snagging on me.

any ideas, pointers, tips...

HELP

[email]meesh@freezepeach.org[/email]

---

### Post by bored2k on 2005-03-10
[QUOTE=frozenfroot]hello all

i run an internet cafe in nyc with a friend. we currently run 90% linux boxes in our cafe (mandrake 9.2) and would like to switch to ubuntu...

we will be running ubuntu on ibm thinkpad 600E computers (which works great sofar)

we are having one problem - yahoo.

we would prefer to just offer gaim (which we both love), but some of our customers are addicted to damn YAHOO!

i have tried to install the debian packages from the yahoo download site using dpkg - but i run into a problem with libssl0.9.6 (which is a missing dependency)

i tried to install libssl0.9.6 but can't get it to work. i used the ./configure then make then make install route on the library, but it is snagging on me.

any ideas, pointers, tips...

HELP

[email]meesh@freezepeach.org[/email][/QUOTE]
 GAIM has Yahoo support, it also has mIRC, MSN, AIM, Gabber, Napster, Gadu-Gadu, Groupwise and ICQ. So i think you're all set in that department.

[img]http://img111.exs.cx/img111/3222/yahoo4ma.jpg[/img]

**edit** - The compiling stuff: after ./configure and make, run sudo make install and input your password. Make install has to be made by a superuser. You wont need it with GAIM though .

By the way
>  $ apt-cache search libssl
libssl0.9.7 - SSL shared libraries

So would just do > apt-get install libssl0.9.7 or whatever version you have [I have Warty with multiverse universe main repositories].

---

### Post by frozenfroot on 2005-03-10
thanks for the quick response bored2k

also thanks for the extra tidbits on make and the 'apt-cache search libssl' tip. this will all come in handy.

ill try to get the ymessenger client to install using libssl0.9.7 and get back to the forum on my success or failure.

thanks

[email]meesh@freezepeach.org[/email]
***************************

NOW is the time

---

### Post by bored2k on 2005-03-10
Hey dude/gal, I might add, your [Freeze Peach Cafe](http://freezepeach.org/pictures.html) looks pretty cool ! Where is it located?

---

### Post by byourg on 2005-03-11
Do a search in Synaptic package manager for 'libssl' and the version your looking for should be there. I have Ymessenger installed and it works great. It doesn't have all the bells and whistles of the new versions for window$ but it works.

---

### Post by frozenfroot on 2005-03-12
this is a message in response to bored2k's question about the location of 'the cafe'

the cafe is located in Astoria, NYC.

thanks all.

ff

---

### Post by az on 2005-03-12
You can just do:

sudo dpkg -i y*.deb
sudo apt-get -f install 
 which will bring in the missing dependancies.

The software sucks.  They do not even give you a menu entry or documentation.  What licence does it use?  Do your customers really find gaim that much different?

---

### Post by ebtech on 2006-04-16
HI all, I tried this and it just gives me that libssl.... is already installed but when I try to install messenger it says that it isn't :(

same when I try to install cedega, says I don't have xlibs installed but I have the newest version.   please help

---

### Post by brentroos on 2006-04-22
_._

---

### Post by pmshirey on 2006-06-21
[QUOTE=brentroos]This way for sure, worked for me to install this program if anyone else wants to know.

[http://ubuntuforums.org/showpost.php?p=947743&postcount=5]("http://ubuntuforums.org/showpost.php?p=947743&postcount=5")[/QUOTE]
And the sad part is you said it will work for [QUOTE=brentroos]anyone else[/QUOTE].It didn't work for me though.
```
Reading package lists... Done
Building dependency tree... Done
Package libssl0.9.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libssl0.9.6 has no installation candidate
paul@paul-desktop:~$ wget http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb
--19:49:39--  http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb
           => `ymessenger_1.0.4_1_i386.deb'
Resolving download.yahoo.com... 216.252.106.75
Connecting to download.yahoo.com|216.252.106.75|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 668,580 (653K) [application/octet-stream]

100%[====================================>] 668,580      527.25K/s

19:49:40 (525.76 KB/s) - `ymessenger_1.0.4_1_i386.deb' saved [668580/668580]

paul@paul-desktop:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 72206 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
```

---

### Post by pmshirey on 2006-06-21
```
sudo dpkg -i y*.deb
sudo apt-get -f install
```
My Command Lines Response.
```
Selecting previously deselected package ymessenger.
(Reading database ... 72194 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

```

---

### Post by mshirey8 on 2006-06-22
Thank you to those who have been helping my 10 year old son (pmshirey) work on his ymessenger problems. He is a new convert to linux/ubuntu. I have him set up on an old P3 650 that runs linux like a charm. I just noticed that he is posting in a Warty forum. We are both using Dapper. I think we're going to stick with Giam for IM needs.

---

### Post by mcwolf on 2006-06-23
:) 
[http://www.linux-index.org/quicks.pl?ut=1151049331;tid=1256#11510493311256]("http://www.linux-index.org/quicks.pl?ut=1151049331;tid=1256#11510493311256")

---

### Post by mshirey8 on 2006-06-23
> **mcwolf]:) 
[URL="http://www.linux-index.org/quicks.pl?ut=1151049331 said:**
> http://www.linux-index.org/quicks.pl?ut=1151049331;tid=1256#11510493311256[/URL]

Thanks! Is that Russian????

---

### Post by stumps on 2006-06-25
[QUOTE=mshirey8]Thanks! Is that Russian????[/QUOTE]

No, that's Bulgarian ;) ... and Ubuntu is one of our favourite distros 8)

---

### Post by enyaw on 2006-06-25
[QUOTE=azz]You can just do:

sudo dpkg -i y*.deb
sudo apt-get -f install 
 which will bring in the missing dependancies.

The software sucks.  They do not even give you a menu entry or documentation.  What licence does it use?  Do your customers really find gaim that much different?[/QUOTE]

Hello![-(

---

