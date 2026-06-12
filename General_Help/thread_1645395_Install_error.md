---
title: "Install error"
date: 2010-12-14
forum: General Help
---

### Post by Meistarin on 2010-12-14
When I try to install a program I get this message on Ubuntu software center. 

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

I get this message but don't know what it means. I use Ubuntu 10.10

Edit: I'm new to Ubuntu so I probably ask some stupid questions.

---

### Post by Rubi1200 on 2010-12-14
Hi and welcome to the forums :-)

There is no such thing as a stupid question.

Go to Applications > Accessories > Terminal

Copy/paste the following command into the terminal and run it. 
```
sudo apt-get update && sudo apt-get upgrade
```Report back if there are errors.

---

### Post by Meistarin on 2010-12-14
Well I still get the message :(

---

### Post by sikander3786 on 2010-12-14
> **Meistarin said:**
> Well I still get the message :(
As Rubi1200 mentioned, we need to see the exact error. In fact, it would be better to post the complete output of this command.

```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by Meistarin on 2010-12-14
Well I downloaded firstclass a mail client.

[http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4]("http://www.firstclass.com")

I downloaded it for debian. And I opened it in Ubuntu Software center and the I got the message. I tried to update as you guys said but I still get the error ?

I need that mail client for my school...

---

### Post by Rubi1200 on 2010-12-14
Meistarin,
one step at a time please ;)

In the terminal:
run the command ```
sudo apt-get update
```
When it is finished, highlight the entire contents and copy/paste and post it back here.

We need to see the error otherwise we cannot troubleshoot the problem.

Thanks.

---

### Post by Meistarin on 2010-12-14
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Reading package lists... Done

---

### Post by sikander3786 on 2010-12-14
So there is no error message in that apt-get update output. Can you please reproduce the initial error message you mentioned in your first post? Which package were you trying to install then? Try this,

```
sudo apt-get install package
```

Replace package with your desire package and post the output.

---

### Post by Meistarin on 2010-12-14
E: Unable to locate package fcc-10.009-Linux.i686.deb
E: Couldn't find any package by regex 'fcc-10.009-Linux.i686.deb'

I downloaded the package from a webpage. But I now tried the command you said in terminal. And then I got that error message.

---

### Post by sikander3786 on 2010-12-14
So that pacakge is not in the repositories. What happens when you double click the downloaded package files? We need to know about that error message actually that is occuring in Software Center.

Sorry, it is getting a bit long but I didn't know that you had downloaded it from the website and not from repositories.

---

### Post by Meistarin on 2010-12-14
I double clicked the package and then i opened the software center and then I got this:

There seems to be a programming error in aptdaemon, the software that  allows you to install/remove software and to perform other package  management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

---

### Post by sikander3786 on 2010-12-14
Try using dpkg.

Navigate to directory where your downloaded file lies. e.g, if it is in Downloads,

```
cd ~/Downloads
```

And then,

```
dpkg -i filename.deb
```

---

### Post by Meistarin on 2010-12-14
dpkg: requested operation requires superuser privilege

---

### Post by sikander3786 on 2010-12-14
> **Meistarin said:**
> dpkg: requested operation requires superuser privilege
```
sudo dpkg -i filename.deb
```

---

### Post by Meistarin on 2010-12-14
dpkg: error processing fcc-10.009-Linux.i686.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory

---

### Post by sikander3786 on 2010-12-14
> **Meistarin said:**
> dpkg: error processing fcc-10.009-Linux.i686.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
The link you provided previously is just redirecting to the homepage. Where can I download the package and test it on my own system?

---

### Post by Meistarin on 2010-12-14
[http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4](http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4)

Then I downloaded the debian client..

I tired the windows version too butthat can't download either.

---

### Post by sikander3786 on 2010-12-14
I've tried to download it 2 times but no success.

The only thing I can guess now is that it was packaged for Debian and is not compatible with Ubuntu. It is not necessary that every Debian package should be compatible with Ubuntu as well.

---

### Post by Meistarin on 2010-12-14
Ok weird. I had 10.04 and it worked there after lots of tries. But I thank for the help :)

---

### Post by sikander3786 on 2010-12-14
You are Welcome. I'll try to download it sometime later, may be in the morning and see if it reports any errors. In the mean time, Rubi1200 might be back with some better suggestions.

Thanks for your patience :-)

---

