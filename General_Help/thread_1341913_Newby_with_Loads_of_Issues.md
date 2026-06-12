---
title: "Newby with Loads of Issues"
date: 2009-11-30
forum: General Help
---

### Post by toxicblogger on 2009-11-30
Hi everyone.


I hope this is the right place to be.


I have 3 major problems with ubuntu as i speak


1 - Update manager is giving me the following problem


'E:Type '*' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'



How do i rectify this?

2 - Some windows applications do not install very well on wine for instance media monkey or my accounting software. How do i overcome this problem?


3 - Zekr installed from Ubuntu Software centre does not work.


Look forward to yourprompt and friendly assistance

---

### Post by pi4r0n on 2009-11-30
> **toxicblogger said:**
> 
'E:Type '*' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


Remove incorrect line (56) from sources.list 

> **toxicblogger said:**
> 
2 - Some windows applications do not install very well on wine for instance media monkey or my accounting software. How do i overcome this problem?


Read Wine forum whether these applications are fully supported.

> **toxicblogger said:**
> 
3 - Zekr installed from Ubuntu Software centre does not work.


Need more info. What does not work, what error message etc..

---

### Post by ed-koala on 2009-11-30
In order to help please supply the following things:

1. The contents of your /etc/apt/sources.list file
2. The name of your accounting software
3. Exact info on what is going wrong with Zekr, including any error messages.

I'll check into Media monkey issue for ya.

---

### Post by ed-koala on 2009-11-30
What version of media monkey are you using?  Here is a link to Wine's info on that program:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5519]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5519")

---

### Post by toxicblogger on 2009-11-30
Hi and thanks for the feedback

> **pi4r0n said:**
> Remove incorrect line (56) from sources.list 


How do i remove the incorrect line?



> Read Wine forum whether these applications are fully supported.

Ah i see. Ok i will check up.



> Need more info. What does not work, what error message etc..


No error message. It just doesnt run.

---

### Post by toxicblogger on 2009-11-30
> **ed-koala said:**
> What version of media monkey are you using?  Here is a link to Wine's info on that program:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5519](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5519)


Version 3 point something. But thanks for the link. Let me check up on that.

---

### Post by toxicblogger on 2009-11-30
> **ed-koala said:**
> In order to help please supply the following things:

1. The contents of your /etc/apt/sources.list file
2. The name of your accounting software
3. Exact info on what is going wrong with Zekr, including any error messages.

I'll check into Media monkey issue for ya.


1 - Like i said i am a newby so i how do i source this list and give it to you.


2 - Tas Books - They dont have any info on their site.


3 - No error message. Just doesnt run.

---

### Post by ed-koala on 2009-11-30
I wouldn't just delete the line in sources.list just yet, let's see what it says first.

Go to Places and navigate to File System - /etc/apt/sources.list ... open it with gedit and copy and past the contents here please.

Try opening a terminal a running Zekr from there by typing zekr and seeing if it says anything then, and if so list it here.

I'll get back to ya on Tas books. A couple of different solutions for that but it'll take a few mins to type em out :)

---

### Post by toxicblogger on 2009-11-30
> **ed-koala said:**
> I wouldn't just delete the line in sources.list just yet, let's see what it says first.

Go to Places and navigate to File System - /etc/apt/sources.list ... open it with gedit and copy and past the contents here please.

Try opening a terminal a running Zekr from there by typing zekr and seeing if it says anything then, and if so list it here.

I'll get back to ya on Tas books. A couple of different solutions for that but it'll take a few mins to type em out 


1 - Ok the sources list is as follows and i havent the foggiest idea whats going on:


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


    *

      Add the GPG key

wget -q [http://siahe.com/zekr/apt/zekr.debian.gpg](http://siahe.com/zekr/apt/zekr.debian.gpg) -O- | sudo apt-key add -

    *

      Run the following commands in the terminal:

sudo apt-get update

sudo apt-get install zekr ttf-me-quran ttf-scheherazade

sudo apt-get install ttf-farsiweb ttf-arabeyes

    *

      To install all the Quran translations available for zekr:

sudo apt-get install zekr-quran-translation-extras

You will then be prompted with a warranty disclaimer.

Agree to the terms by clicking Yes.

You can launch Zekr from the Applications Menu under Accessories.

    *

      If you are upgrading from a previous installed version of zekr, to use the new font configuration of zekr run the following command in the terminal:

mv ~/.zekr ~/zekr-backup

    * Share/Bookmark

Tags | General, Linux, Ubuntu
Leave a Reply

You must be logged in to post a comment.

    * POPULAR
    * FEATURED
    * TAG CLOUD

    * Computing Without The Price - Microsoft Azure vs Amazon EC2
    * Use Gmail Offline
    * How To Download Videos From Youtube
    * How to install VLC Media Player in Ubuntu

    * Mac OS X Snow Leopard - User Experience Release
    * Windows 7 Themes
    * Install Linux From USB
    * Slow Tab Opening in Internet Explorer 8
    * Restore Start Menu Internet Search in Windows 7
    * Map Windows Music to Ubuntu
    * Use Gmail Offline
    * Google’s New Oh eS
    * Welcome to GoITExpert.com 3.0
    * Show PID Process Identifier

7 8 Apple chosos chrome Databases Disaster Recovery explorer gears General gmail Google install internet Linux Microsoft Mobile Netware Networking new offline os Other Security Servers snow_leopard Tech News Ubuntu upgrade usb vista Web 2.0 welcome windows Windows 7 Windows Vista Windows XP wordpress xp
Categories

    * Apple (24)
    * Databases (20)
    * Disaster Recovery (40)
    * General (310)
    * Google (29)
    * Linux (181)
    * Microsoft (103)
    * Mobile (35)
    * Netware (12)
    * Networking (106)
    * Other (3)
    * Security (78)
    * Servers (36)
    * Tech News (26)
    * Ubuntu (149)
    * Web 2.0 (9)
    * Windows 7 (3)
    * Windows Vista (275)
    * Windows XP (182)

Archives

    * September 2009 (2)
    * July 2009 (7)
    * March 2009 (5)
    * February 2009 (9)
    * January 2009 (22)
    * December 2008 (2)
    * November 2008 (2)
    * October 2008 (3)
    * September 2008 (1)
    * January 2008 (10)
    * December 2007 (11)
    * November 2007 (
    * October 2007 (24)
    * September 2007 (15)
    * August 2007 (12)
    * July 2007 (33)
    * June 2007 (54)
    * May 2007 (3
    * April 2007 (50)
    * March 2007 (80)
    * February 2007 (139)
    * January 2007 (50)
    * December 2006 (1)


    *

      Add the GPG key

wget -q [http://siahe.com/zekr/apt/zekr.debian.gpg](http://siahe.com/zekr/apt/zekr.debian.gpg) -O- | sudo apt-key add -

    *

      Run the following commands in the terminal:

sudo apt-get update

sudo apt-get install zekr ttf-me-quran ttf-scheherazade

sudo apt-get install ttf-farsiweb ttf-arabeyes

    *

      To install all the Quran translations available for zekr:

sudo apt-get install zekr-quran-translation-extras

You will then be prompted with a warranty disclaimer.

Agree to the terms by clicking Yes.

You can launch Zekr from the Applications Menu under Accessories.

    *

      If you are upgrading from a previous installed version of zekr, to use the new font configuration of zekr run the following command in the terminal:

mv ~/.zekr ~/zekr-backup

    * Share/Bookmark

Tags | General, Linux, Ubuntu
Leave a Reply

You must be logged in to post a comment.

    * POPULAR
    * FEATURED
    * TAG CLOUD

    * Computing Without The Price - Microsoft Azure vs Amazon EC2
    * Use Gmail Offline
    * How To Download Videos From Youtube
    * How to install VLC Media Player in Ubuntu

    * Mac OS X Snow Leopard - User Experience Release
    * Windows 7 Themes
    * Install Linux From USB
    * Slow Tab Opening in Internet Explorer 8
    * Restore Start Menu Internet Search in Windows 7
    * Map Windows Music to Ubuntu
    * Use Gmail Offline
    * Google’s New Oh eS
    * Welcome to GoITExpert.com 3.0
    * Show PID Process Identifier

7 8 Apple chosos chrome Databases Disaster Recovery explorer gears General gmail Google install internet Linux Microsoft Mobile Netware Networking new offline os Other Security Servers snow_leopard Tech News Ubuntu upgrade usb vista Web 2.0 welcome windows Windows 7 Windows Vista Windows XP wordpress xp
Categories

    * Apple (24)
    * Databases (20)
    * Disaster Recovery (40)
    * General (310)
    * Google (29)
    * Linux (181)
    * Microsoft (103)
    * Mobile (35)
    * Netware (12)
    * Networking (106)
    * Other (3)
    * Security (78)
    * Servers (36)
    * Tech News (26)
    * Ubuntu (149)
    * Web 2.0 (9)
    * Windows 7 (3)
    * Windows Vista (275)
    * Windows XP (182)

Archives

    * September 2009 (2)
    * July 2009 (7)
    * March 2009 (5)
    * February 2009 (9)
    * January 2009 (22)
    * December 2008 (2)
    * November 2008 (2)
    * October 2008 (3)
    * September 2008 (1)
    * January 2008 (10)
    * December 2007 (11)
    * November 2007 (8)
    * October 2007 (24)
    * September 2007 (15)
    * August 2007 (12)
    * July 2007 (33)
    * June 2007 (54)
    * May 2007 (38)
    * April 2007 (50)
    * March 2007 (80)
    * February 2007 (139)
    * January 2007 (50)
    * December 2006 (1)


    *

      Add the GPG key

wget -q [http://siahe.com/zekr/apt/zekr.debian.gpg](http://siahe.com/zekr/apt/zekr.debian.gpg) -O- | sudo apt-key add -

    *

      Run the following commands in the terminal:

sudo apt-get update

sudo apt-get install zekr ttf-me-quran ttf-scheherazade

sudo apt-get install ttf-farsiweb ttf-arabeyes

    *

      To install all the Quran translations available for zekr:

sudo apt-get install zekr-quran-translation-extras

You will then be prompted with a warranty disclaimer.

Agree to the terms by clicking Yes.

You can launch Zekr from the Applications Menu under Accessories.

    *

      If you are upgrading from a previous installed version of zekr, to use the new font configuration of zekr run the following command in the terminal:

mv ~/.zekr ~/zekr-backup

    * Share/Bookmark

Tags | General, Linux, Ubuntu
Leave a Reply

You must be logged in to post a comment.

    * POPULAR
    * FEATURED
    * TAG CLOUD

    * Computing Without The Price - Microsoft Azure vs Amazon EC2
    * Use Gmail Offline
    * How To Download Videos From Youtube
    * How to install VLC Media Player in Ubuntu

    * Mac OS X Snow Leopard - User Experience Release
    * Windows 7 Themes
    * Install Linux From USB
    * Slow Tab Opening in Internet Explorer 8
    * Restore Start Menu Internet Search in Windows 7
    * Map Windows Music to Ubuntu
    * Use Gmail Offline
    * Google’s New Oh eS
    * Welcome to GoITExpert.com 3.0
    * Show PID Process Identifier

7 8 Apple chosos chrome Databases Disaster Recovery explorer gears General gmail Google install internet Linux Microsoft Mobile Netware Networking new offline os Other Security Servers snow_leopard Tech News Ubuntu upgrade usb vista Web 2.0 welcome windows Windows 7 Windows Vista Windows XP wordpress xp
Categories

    * Apple (24)
    * Databases (20)
    * Disaster Recovery (40)
    * General (310)
    * Google (29)
    * Linux (181)
    * Microsoft (103)
    * Mobile (35)
    * Netware (12)
    * Networking (106)
    * Other (3)
    * Security (78)
    * Servers (36)
    * Tech News (26)
    * Ubuntu (149)
    * Web 2.0 (9)
    * Windows 7 (3)
    * Windows Vista (275)
    * Windows XP (182)

Archives

    * September 2009 (2)
    * July 2009 (7)
    * March 2009 (5)
    * February 2009 (9)
    * January 2009 (22)
    * December 2008 (2)
    * November 2008 (2)
    * October 2008 (3)
    * September 2008 (1)
    * January 2008 (10)
    * December 2007 (11)
    * November 2007 (8)
    * October 2007 (24)
    * September 2007 (15)
    * August 2007 (12)
    * July 2007 (33)
    * June 2007 (54)
    * May 2007 (38)
    * April 2007 (50)
    * March 2007 (80)
    * February 2007 (139)
    * January 2007 (50)
    * December 2006 (1)


Part 2 - next post

---

### Post by toxicblogger on 2009-11-30
2 - Zekr on terminal message


Launching Zekr...
java.lang.NullPointerException
    at org.apache.velocity.context.InternalContextAdapterImpl.put(InternalContextAdapterImpl.java:269)
    at org.apache.velocity.runtime.parser.node.ASTSetDirective.render(ASTSetDirective.java:213)
    at org.apache.velocity.runtime.parser.node.SimpleNode.render(SimpleNode.java:336)
    at org.apache.velocity.Template.merge(Template.java:328)
    at org.apache.velocity.Template.merge(Template.java:235)
    at net.sf.zekr.engine.theme.TemplateEngine.getUpdated(TemplateEngine.java:115)
    at net.sf.zekr.common.config.VelocityInputStream.<init>(VelocityInputStream.java:29)
    at net.sf.zekr.common.config.ResourceManager.<init>(ResourceManager.java:30)
    at net.sf.zekr.common.config.ResourceManager.getInstance(ResourceManager.java:40)
    at net.sf.zekr.ui.splash.AbstractSplachScreen.<init>(AbstractSplachScreen.java:16)
    at net.sf.zekr.ui.splash.AdvancedSplashScreen.<init>(AdvancedSplashScreen.java:31)
    at net.sf.zekr.ZekrMain.startZekr(ZekrMain.java:41)
    at net.sf.zekr.ZekrMain.main(ZekrMain.java:79)

---

### Post by toxicblogger on 2009-11-30
> I'll get back to ya on Tas books. A couple of different solutions for that but it'll take a few mins to type em out 


I could kiss you if you can sort this one out. :P


:D

---

### Post by ed-koala on 2009-11-30
Wow, that's messed up, no wonder zekr isn't working and you get an error on sources.list!

Open a terminal and type sudo gedit. Put in your password (it won't echo anything back on the screen). Browse to /etc/apt/sources.list and open the file. Delete *everything* from the first

```
*

Add the GPG key
```

onward and save the file. Close the terminal.

Go here [http://zekr.org/wiki/Installation]("http://zekr.org/wiki/Installation") and follow the instuctions under 3.1.

Enjoy Zekr.

---

### Post by ed-koala on 2009-11-30
Media Monkey solution:

There are many many different apps for playing media files in Ubuntu. You may want to research this and consider switching apps, probably your best bet as it is always preferred to use native programs over Windows apps for whatever you want to do.  That being said, see the solution below for Tas Books for another idea.


Tas Books solution:

There are not many accounting apps out there for Ubuntu that I noticed. Wine didn't even kist the app in their database, so how it'll run, if at all, if a mystery. However, all is not lost.  VirtualBox to the rescue!  VirtualBox will run Windows as a guest environment within your Ubuntu install, and you can install Windows programs into it and run them there.  Not really a great solution for cutting edge games, but Tas Books should work fine this way.

You can install VirtualBox from Synaptic Package Manager, but you will need a Windows install disk to set up your Windows guest system.  A google seach will turn up several pages on how to set it up.

---

### Post by toxicblogger on 2009-11-30
> Browse to /etc/apt/sources.list and open the file. Delete *everything* from the first

Ok i get to um sudo gedit and gedit does open but it looks blank. so how do i browse for the stuff?


> Media Monkey solution:

There are many many different apps for playing media files in Ubuntu. You may want to research this and consider switching apps, probably your best bet as it is always preferred to use native programs over Windows apps for whatever you want to do. That being said, see the solution below for Tas Books for another idea.\


Gotcha. I am with rhythmbox which works just fine but real player linux version doesnt. I dont why. 


> Tas Books solution:

There are not many accounting apps out there for Ubuntu that I noticed. Wine didn't even kist the app in their database, so how it'll run, if at all, if a mystery. However, all is not lost. VirtualBox to the rescue! VirtualBox will run Windows as a guest environment within your Ubuntu install, and you can install Windows programs into it and run them there. Not really a great solution for cutting edge games, but Tas Books should work fine this way.

You can install VirtualBox from Synaptic Package Manager, but you will need a Windows install disk to set up your Windows guest system.



Cheers mate. I will certainly look into the option. The data is all on Tas Books and with a new software it means running two systems parallel until i am sure of the Linux software. Sourceforge has one which looks the part. 


[http://sourceforge.net/projects/turbocash/reviews/](http://sourceforge.net/projects/turbocash/reviews/)


I will try this.

---

### Post by ed-koala on 2009-11-30
It'll be blank til we open the file we want. Go to Open up near the top left. A file browser window will open. On the left side will be a list of things, one of em should be File System. Click that, then double click etc, apt, sources.list. Continue as stated before.

---

### Post by toxicblogger on 2009-11-30
Thanks so much for your help. The update issue is sorted. The only thing remaining now of some urgency is Zekr. I removed it using Software Center and re installed using the same Center and there is no activity.

---

### Post by ed-koala on 2009-11-30
We'll get Zekr fixed now ... First, go into Software Center and uninstall it again. I always use Synaptic to install packages myself, easy and specifically designed for the job.

Second, open System - Administration - Synaptic Package Manager ... search for zekr ... if it has a green box on it, right click and select mark for complete removal. Also get rid of the translations if it's there.

Let's make sure it's gone ... probably overkill but do this ... open a terminal and type

```
sudo apt-get remove -purge zekr
```

Now, if you *really* want to be safe, lets do something that's almost never needed ... reboot.  A fresh running session never hurts.

After you are running again, go into Synaptic and install zekr.  It should work fine now.

---

### Post by toxicblogger on 2009-11-30
Ok rebooted and before i rebooted, the zekr purge command gave me this answer


*E: Command line option 'p' [from -purge] is not known.*


So i suppose its not there at all. Now on the synpatic software installation, I marked Zekr for installation and some 40 odd files were downloaded with this error message

[I]Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2](http://ke.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.[/I]


So where do we go from here?

---

### Post by ed-koala on 2009-11-30
ok, next step. Open Synaptic again, click edit, select Fix Broken Packages.

After that's done, assuming it did anything (mine doesn't cause nothing is broken here), then open a terminal and run this command:

```
apt-get --purge remove zekr
```

I may have had the syntax wrong last time, I know it's right this time.

Let me know if all that goes well, and also click on the reload button in Synaptic if all goes well.

---

### Post by toxicblogger on 2009-11-30
apt-get --purge remove zekr


It couldnt perform this and the reason for that was 


E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by ed-koala on 2009-11-30
oops!  My bad. You need to add sudo before the command, like this:

```
sudo apt-get ......
```

---

### Post by ed-koala on 2009-11-30
How's it going?  Hopefully repairing broken packages fixed things, if not, I'm out of ideas.  Let us know if zekr is working for you and if so, please mark this thread as solved :)

---

### Post by toxicblogger on 2009-11-30
Sorry mate for the delay, something came up. Yup it worked like a charm.

Now the next step assuming it will be the last. Also would you recommend the Ubuntu Muslim edition? Cos all of the packages come in preloaded. And if so, is there anyway to migrate from this version to muslim edition sabily with minimum fuss?

---

### Post by ed-koala on 2009-11-30
On that, I have no idea.  Try starting another post asking about migrating to a muslim edition of ubuntu.  Also, please use the thread tools to mark this thread solved.  Glad we got you up and running!!

---

### Post by toxicblogger on 2009-11-30
Hi and good morning.


I am sorry its not resolved. I successfully managed to purge the package using terminal and your instructions. Then i went to synpatics and marked the software for installation and reloaded. 


Still nothing.

---

### Post by ed-koala on 2009-11-30
I'll assume you repaired the broken packages. Hmmm. Did Synaptic install go ok?  If so, I'll do a web search to see what I can find, but I'm not sure what the problem is.  I've never had a package that appears in Synaptic, and installs ok, not run.  It just shouldn't happen.  Of course, that doesn't mean it can't, because obviously it's happening to you.

---

### Post by ed-koala on 2009-11-30
I think you are gonna like this ... found The Zekr FAQ! It has specific instructions for making it work with Ubuntu.

[http://zekr.org/faq.html]("http://zekr.org/faq.html")

Here is another page that may be needed. Has some Java stuff that you might or might not have to do.

[http://zekr.org/wiki/Installation]("http://zekr.org/wiki/Installation")

If those don't get you running, nothing will. (Just kidding, I hope)!

---

### Post by toxicblogger on 2009-11-30
This is the error message i am getting


Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2](http://ke.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.bz2](http://ke.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by toxicblogger on 2009-11-30
RESOLVED


Thanks everyone for your hard work and patience. Much appreciated.

---

### Post by ed-koala on 2009-11-30
The installation wiki link I gave you has info about your /etc/apt/sources.list file, and what EXACTLY should be there as regards zekr, make sure that part is correct, as well as follow the instructions carefully.

I'd read both pages before doing anything, then go from there.  The wiki looks really detailed and good.

---

### Post by toxicblogger on 2009-11-30
Will do Ed. I really appreciate your service. Now to create a thread for anti virus

---

### Post by ed-koala on 2009-11-30
Antivirus? in Ubuntu?  What's that?  I've never used any ... with zero trouble.

---

### Post by toxicblogger on 2009-11-30
I was a victim of a nasty hack from what i thought was a trusted site and good online friends. But they hacked me using a keylogger system. That was when i was on XP hence the migration to Ubuntu

I just want to be sure that no one is tracking me or more importantly my data. What do i have to do ensure that?

---

### Post by ed-koala on 2009-11-30
Ubuntu works differently than Windows.  Nothing is going to be installing programs behind your back in Ubuntu, because as you noticed already, any time you want to install something, you have to put in your password to do that. So, no keylogger program gets secretly put in, or any other executable program.

Programs like keyloggers and root kits designed for Windows simply won't work, even with Wine, due to how they are written.

So, have little fear. As I said, I've been using Ubuntu for 3 years with no virus protection, no spyware software, and I've had not a single problem.

Do start another post tho, and see what responses you get.  :)  Never hurts to be safe!

---

