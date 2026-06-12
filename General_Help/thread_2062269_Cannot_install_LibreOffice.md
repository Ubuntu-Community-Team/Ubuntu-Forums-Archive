---
title: "Cannot install LibreOffice"
date: 2012-09-24
forum: General Help
---

### Post by thelugnut on 2012-09-24
Strange...My computer crashed after an electrial outage. When I got it up again I reinstalled Ubuntu 10.04. Then I tried to install LibreOffice. I removed OpenOffice, as required, and took the steps necessary to install it. Steps that I have taken a few times before. But I get this output each of the three attempts to install.
> [QUOTE]The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.5.4-0ubuntu1~lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.5.4~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Broken packages
[/QUOTE]

Jus in case the dowload was bad, I downloaded it three different times.
I get this on each attempt. I never had a problem installing this before. Any suggestions?

---

### Post by jerrrys on 2012-09-24
Is [this]("http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html") how you did it?

---

### Post by thelugnut on 2012-09-25
Thanks for the reply...
Absolutely, step by step. Remember I have, in the past, installed this program before with no problems. As I mentioned, I downloaded three separate times and tried to install three times, and I always get the failure as I posted. Oh, one more thing. I dual boot Ubuntu with Windows XP. I installed LibreOffice on Windows XP with no problems. I might mention that I am sticking with Ubuntu 10.04 because the new versions won't run on my computer.

---

### Post by TenPlus1 on 2012-09-25
Rather that sticking with old versions which will soon be unsupported, why not try and figure out WHY Ubuntu 12.04 will not run on your system ?  Have you tried other flavours like Xubuntu or even Lubuntu for a lighter environment ?

What happens when you try to install ubuntu 12.04 ???

---

### Post by jerrrys on 2012-09-25
Have you tried

sudo apt-get install -f

Edit:  better idea

sudo apt-get clean

sudo apt-get update

first

---

### Post by thelugnut on 2012-09-26
Hi all,
Thanks for the replies.
TenPlus1 - I took your sage advice and spent a couple of days trying to get 12.04 to load. Well, I was finally successful, and that is what I am running now. Now here's the bad news. I haven't a clue as to why it would not install before. Sorry about that, because the answer might have been of some benefit to others.
But I am happy that I have it installed now, on my laptop. 
The disk refuses to do anything at all on my HP All-in-One. So that one stays with Ubuntu 10.04 till I get it cornered. Not a problem as my wife uses that machine. I will try the suggestion given in the reply as soon as I have a little time.  
Again thank you all for your inputs. I really appreciated them. ):P

---

### Post by gusig on 2012-09-29
Here is the solution that did the trick for me:   [http://www.unixmen.com/libreoffice-3-5-has-been-released-install-ubuntu-fedora-debian-linuxmint-ppa/](http://www.unixmen.com/libreoffice-3-5-has-been-released-install-ubuntu-fedora-debian-linuxmint-ppa/)

I used the **Installation using Debian Package **and installed the LibreOffice 3.5.7.1  with the Icelandic lang. and help packs.  Works like charm!!

---

