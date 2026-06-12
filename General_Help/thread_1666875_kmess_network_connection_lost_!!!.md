---
title: "kmess network connection lost !!!"
date: 2011-01-14
forum: General Help
---

### Post by rostom_zer on 2011-01-14
hi guys

could some one try ho help me fixing my problem please

i installed kde workspace in my ubuntu 10.10 so that i will have a choice betweel gnome/kde into the login screen

all was working fine

but i didn't like that environment (KDE), sins it installed some other applications that i allrady have for example i have firefox installed and he installed me konqueror which is for KDE so, it installed all kde apps. now i have the apps twice. 

I decided to uninstall that environment

i didn't find a way to uninstall it completlly from pc in one click in software center or synaptic

so i opend synaptic then selected some packages installed which are version (4:4.5.1-0ubuntu4) it's like this writen in package manager

so i inunstalled them

now i'm having a problem using kmess...

when i try to connect to my msn account, it tells me (Authenticating...) then (Authenticated) then (waiting for contact list) then the contacts appears just for 1 milli cesond then disconnects !!!!!

a notification apprase telling me " kmess network connection lost "

here is the log which i copied from terminal

> 
10.297> kmess(2537) RoamingService::updateDisplayPicture: Missing profileResourceId, not updating display picture 
15.563> kmess(2537) MimeMessage::splitLine: Couldn't split line ' "" ' 
15.563> kmess(2537) MimeMessage::splitLine: Couldn't split line ' "" ' 
19.752> kmess(2537) RoamingService::updateProfile: Missing profileResourceId, not updating profile 
19.753> kmess(2537) RoamingService::updateProfile: Missing profileResourceId, not updating profile 
20.161> kmess(2537) MsnNotificationConnection::slotError: MSN Notification Connection error type 4 : "The remote host closed the connection" 



please help me i'm connectin to my msn account only by kmess i really liked that app

thanX in advance

---

### Post by nothingspecial on 2011-01-14
Have a look at this

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

for future ref, you do not have to install the whole of Kubuntu to try out kde.

---

### Post by rostom_zer on 2011-01-14
Thanx,

but, my problem is not how to uninstall kubuntu.

my problem is after i uninstalled it, kmess won't work and that was my log into terminal (1st poste)

kmess is not working now

i need to fix it

i uninstalled it then reinstalled it, but not working !!!!

[COLOR=Red]I suppose that i deleted a packege by error that is not part of kde desktop[/COLOR] since i uninstalled kde manually from synaptic by selecting the packeges

thanX

---

### Post by rostom_zer on 2011-01-14
Here are the packages that i deleted from synaptic

check attachment

thanX

---

### Post by rostom_zer on 2011-01-14
Here are the packages that i deleted from synaptic

check attachment

thanX

Oups...

[COLOR=Red]sorry for double poste (bad connection)
please admin, delete this and try to help me solving my problem
thanX[/COLOR]

---

### Post by Lekensteyn on 2011-01-14
The bug with KMess has nothing to do with your removal of the KDE workspace, it's a bug caused by Micro$ofts change in the protocol.
You can get the latest version of KMess from their PPA (see [https://launchpad.net/~kmess-packages/+archive/kmess-stable](https://launchpad.net/~kmess-packages/+archive/kmess-stable)).
You can add this PPA (Personal Package Archive) by running:
```
sudo apt-add-repository ppa:kmess-packages/kmess-stable
```
Then update your sources list and upgrade KMess:
```
sudo apt-get update && sudo apt-get upgrade
```
This solved random logouts during chats.

In my case, this worked for only a day. The next day, I had a new problem. KMess would show me the contacts list shortly, and close within a second with the error you described.
That has to do with another change at Micro$oft, and is (will) be fixed in KMess 2.0.6, which is not officially available yet.
Vistaus has applied a patch which made it work again (at least, for 64 bits). See [http://kmess.org/board/viewtopic.php?f=4&t=4585&start=30#p14229](http://kmess.org/board/viewtopic.php?f=4&t=4585&start=30#p14229).
I didn't like to install a whole .deb file, which could break things or contains other stuff, so I just replaced the core parts: a library file and the kmess binary.
**WARNING:** this will work for 64-bits systems only, the 32-bits binary wouldn't build on his system and as a consequence, there is not 32-bits version available from his side.
The code for downloading the archive, extracting the involved files and replacing the original binary and library:
```
cd /tmp&&wget 'https://sites.google.com/site/ubukuntu/downloads/kmess_stable-1_amd64.deb'&&ar x kmess_stable-1_amd64.deb data.tar.gz&&umask 0022&&sudo tar xpf data.tar.gz -C/ ./usr/bin/kmess ./usr/lib/kde4/libkmesssendplugin.so
```
umask 0022 prevents the binaries be created with 640 if you'd set umask 0027 earlier. 'p' in tar xpf preserves the date, permissions and ownership/groupship. -C/ changes the working dir to root, so the extracted files will be put in the correct directories.

---

### Post by Lekensteyn on 2011-01-14
Oops - double post due to busy ubuntuforums which gave a database error (please delete post).

---

### Post by Lekensteyn on 2011-01-14
Oops - double post due to busy ubuntuforums which gave a database error.

---

### Post by Lekensteyn on 2011-01-14
Oops - double post due to busy ubuntuforums which gave a database error.

---

### Post by rostom_zer on 2011-01-15
I'm in 32bit system

so no way to fix this problem ???

---

### Post by Lekensteyn on 2011-01-15
You could compile the stuff on your own, but I do not recommend it.

---

### Post by rostom_zer on 2011-01-15
so...

i'm using empathy till a new release will be done.

just i wana know if this problem is caused by me or it's from kmess itself

because i was confused. i was online in kmess talking with my friends.

suddenly i desided to uninstall KDE environment.

i uninstalled it then go to bed. tomorrow i tried ti login then the problem appeared !!!

---

### Post by davirrirri on 2011-01-15
Thanks Lekensteyn for explain this KMESS error. I have the same bug but don't knew what was the problem. Thanks again.
rostom_zer is not a KDE problem or you. Apparently your change KDE - GNOME desktop was simultaneous to the protocol changes by Microsoft, like said Lekensteyn. I didn't this change between desktops and I have the same bug.

---

### Post by Lekensteyn on 2011-01-16
From [http://kmess.org/board/viewtopic.php?f=4&t=4585&p=14349#p14349:](http://kmess.org/board/viewtopic.php?f=4&t=4585&p=14349#p14349:)
[QUOTE=Lekensteyn]After messing a few hours, I've finally a working deb for 32 bits :D
Built in a Ubuntu 10.04 (with all updates) VM from commit 02c8a86 with no configure option ("./configure").
[http://www.lekensteyn.nl/files/kmess_2.0.6git-dev02c8a861_i386.deb](http://www.lekensteyn.nl/files/kmess_2.0.6git-dev02c8a861_i386.deb)
I wasn't skilled enough to build the whole .deb file, so I just replaced the kmess binary in data.tar.lzma with the patched binary. Furthermore, I've removed a .so file which was probably used for Konqueror integration. It does not depend on libkonq5 anymore, and konqueror is neither suggested.
[/QUOTE]

---

### Post by rostom_zer on 2011-01-17
>                      Originally Posted by **Lekensteyn**                                      
                 [I]After messing a few hours, I've finally a working deb for 32 bits :grin:
Built in a Ubuntu 10.04 (with all updates) VM from commit 02c8a86 with no configure option ("./configure").
[http://www.lekensteyn.nl/files/kmess...8a861_i386.deb]("http://www.lekensteyn.nl/files/kmess_2.0.6git-dev02c8a861_i386.deb")
I wasn't skilled enough to build the whole .deb file, so I just replaced  the kmess binary in data.tar.lzma with the patched binary. Furthermore,  I've removed a .so file which was probably used for Konqueror  integration. It does not depend on libkonq5 anymore, and konqueror is  neither suggested.[/I]
Hi [B]Lekensteyn.

can i use that deb file safety (no problem will touch other softs ?)

is this deb package is stable ???

One other thing. if the problem is still happening, Empathy[/B]©** 2.32.1 connects successfully could the loging method ****of ****Empathy**©[B] be helpfull to fix the problem ?

i'm connecting with empathy now greatlly

but belive me guys... i love kmess

Help us developers...

ThanX lekensteyn for your package. it worked fine
nice fade effect when login done ;)


[/B]

---

### Post by Lekensteyn on 2011-01-18
> **rostom_zer said:**
> Hi [B]Lekensteyn.

can i use that deb file safety (no problem will touch other softs ?)

is this deb package is stable ???

One other thing. if the problem is still happening, Empathy[/B]©** 2.32.1 connects successfully could the loging method ****of ****Empathy**©[B] be helpfull to fix the problem ?

i'm connecting with empathy now greatlly

but belive me guys... i love kmess

Help us developers...

ThanX lekensteyn for your package. it worked fine
nice fade effect when login done ;)


[/B]
I've built KMess myself on Ubuntu 10.04 LTS, following the instructions on their website. The deb is based on the deb file from Ubuntu, since I wasn't skilled enough to build a deb file from scratch (although I tried it :D)
I've tested it before uploading, so you should be fine.

---

### Post by oxan on 2011-01-20
I've  created updated 2.0.5 packages for Lucid, Maverick and Natty, both i386  and amd64, available from my  [PPA](https://launchpad.net/~oxan/+archive/misc). They're just the 2.0.5 packages with the upstream patch added, I've tested it and it works well :)

---

### Post by L_V on 2011-01-27
Kmess seems to be a mess.

V2.0.4 is used by Maverick & Natty.
There are some V2.0.5, and now some "patched" 2.0.5 due to recent connection troubles.
I understood that V2.0.6 has been made available to correct new recent connection problems.
Does somebody really understand which Kmess version should be used at ubuntu without confusion ?

---

### Post by L_V on 2011-02-07
The current version of KMess is: 2.0.6

[http://kmess.org/](http://kmess.org/)

---

