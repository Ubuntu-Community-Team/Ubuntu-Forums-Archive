---
title: "k9copy Isn't working....."
date: 2011-06-05
forum: General Help
---

### Post by ae804 on 2011-06-05
So, the program did work I just don't know what happened to make it quit working.  Here's a couple lines from terminal when I try to run it...

```

k9copy(3753)/kio (KDirModel) KDirModelPrivate::_k_slotDeleteItems: No node found for item that was just removed: KUrl("file:///home/ae804/Documents/Attach0.html") 
k9copy(3753)/kdesu (kdelibs) KDESu::PtyProcess::exec: [ ../../kdesu/process.cpp : 293 ]  Running "/usr/bin/sudo"
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "[sudo] password for ae804: "
k9copy(3753)/kdesu (kdelibs) KDESu::PtyProcess::WaitSlave: [ ../../kdesu/process.cpp : 379 ]  Child pid 3763
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line ""
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "Sorry, try again."
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "[sudo] password for ae804: "

```

Anyone with advice would be appreciated.

Thanks

---

### Post by ae804 on 2011-06-06
Anyone?.. help please :(

---

### Post by linuxinstalledfromhdd on 2011-06-06
Has this ever worked before on your system? What are you running, 10.10?

---

### Post by ae804 on 2011-06-06
> **linuxinstalledfromhdd said:**
> Has this ever worked before on your system? What are you running, 10.10?

Sorry, I should have put that in, but this is pretty much my frist time to post.

I am running 11.04 and yes it did work like last week.  Then I must have done something... not sure what, but it stopped working.

---

### Post by linuxinstalledfromhdd on 2011-06-06
Have you installed anything or changed anything on your system since last week?

---

### Post by ae804 on 2011-06-06
Yea, but i don't know what I did......  I will tell you my history from last time it worked (for sure)....
These are all that I installed:
[QUOTE=Monday]libwxbase2.6-0 (2.6.3.2.2-5ubuntu2)
libwxbase2.8-0 (2.8.11.0-0ubuntu8, automatic)
tuxpaint-plugins-default (0.9.21-1ubuntu, automatic)
tuxpaint-data(0.9.21-1ubuntu2, automatic)
tuxpaint(0.9.21-1ubuntu2)
tuxpaint-stamps-default(2009.06.28-1, automatic)
unrar (4.0.3-1)
wx2.6-headers (2.6.3.2.2-5ubuntu2)
python-wxgtk2.6 (2.6.3.2.2-5ubuntu2)
libwxbase2.6-dev (2.6.3.2.2-5ubuntu2)
rar(4.0.b3-1)
libwxgtk2.6-dev (2.6.3.2.2-ubuntu2)
wx-common (2.8.11.0-0ubuntu8)
python-wxversion (2.8.11.0-0ubuntu8)[/QUOTE]
[QUOTE=05 June]
acidrip(0.14-0.2ubuntu6)
[/QUOTE]
[QUOTE=04 June]
pokerth (0.8.3-1)
libgsasl7 (1.4.4-2ubuntu1, automatic)
libboost-iostreams1.42.0 (1.42.0-4ubuntu2, automatic)
libntlm0 (1.2-1, automatic)
pokerth-data (0.8.3-1, automatic)
gsfonts-x11 (0.21, automatic)
[/QUOTE]

---

### Post by coffeecat on 2011-06-06
> **ae804 said:**
> So, the program did work I just don't know what happened to make it quit working.  Here's a couple lines from terminal when I try to run it...

```

k9copy(3753)/kio (KDirModel) KDirModelPrivate::_k_slotDeleteItems: No node found for item that was just removed: KUrl("file:///home/ae804/Documents/Attach0.html") 
k9copy(3753)/kdesu (kdelibs) KDESu::PtyProcess::exec: [ ../../kdesu/process.cpp : 293 ]  Running "/usr/bin/sudo"
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "[sudo] password for ae804: "
k9copy(3753)/kdesu (kdelibs) KDESu::PtyProcess::WaitSlave: [ ../../kdesu/process.cpp : 379 ]  Child pid 3763
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line ""
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "Sorry, try again."
k9copy(3753)/kdesu (kdelibs) KDESu::SuProcess::ConverseSU: [ ../../kdesu/su.cpp : 259 ]  Read line "[sudo] password for ae804: "

```Anyone with advice would be appreciated.

Thanks

Did you run k9copy with sudo or kdesudo? You don't need to run k9copy as root. I wonder if this is the problem.

---

### Post by ae804 on 2011-06-06
how do I fix that?

---

### Post by coffeecat on 2011-06-07
I don't know. I noticed the kdesu/sudo comments in the output you posted and concluded you ran k9copy as root.

First thing - you didn't answer my question: whether you ran k9copy as root. If you did, open a terminal and run k9copy with:

```
k9copy
```No sudo. Post any errors you get.

Let me expand on this running as root business. Some applications which are not designed to be run as root can give you problems if you do so. I've not had direct experience of this, but this is an issue that comes up occasionally on the forum. What (sometimes?) happens - or so I read - is that a configuration file in your home folder for the app in question gets owned by root. When you next try to start it without root privileges, it fails.

I really don't know whether this is the problem in your case, but let's investigate. The only configuration file that I can find for k9copy is ~/.kde/share/config/k9copyrc. Open your home folder, pres ctrl-H to see the hidden folders/files, open the .kde folder, then share, then config and right-click on the k9copyrc file. Select Properties > Permissions tab. What does it say about Owner?

---

### Post by ae804 on 2011-06-07
Permissions:
> Owner:           ae804-AE804
Access:          Read and Write
Group:           ae804
Access:          None
Others
Access:          None
Execute:         [ ] Allow executing file as a porgram
SELinux Context: unknown
Last changed:    unknown

And when I opened terminal and typed k9copy, I got this:
> ae804@ae804-P5K-Deluxe:~$ k9copy
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kbuildsycoca4 running...
Disc in /dev/sr1 is a Video DVD
Disc in /dev/sr1 is a Video DVD
Disc in /dev/sr1 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr1 is a Video DVD
Disc in /dev/sr0 is a Video DVD
klauncher(2369)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2369)/kio (KLauncher): SlavePool: No communication with slave. 

---

### Post by coffeecat on 2011-06-07
Your k9copyrc file is owned by yourself, so running as sudo doesn't seem to have done any harm. When I run k9copy from the terminal in Ubuntu Natty (Unity desktop) I get no output. k9copy simply opens as normal and shows the contents of the DVD when I click on "Open" in the k9copy toolbar.

My guess is that those messages are telling you something about the kde underpinnings that k9copy is running on, but I have little experience with KDE4 so I don't know what they might mean. Googling the "Connected to deprecated..." line gives a lot of hits and seems to be a general KDE problem.

I'm sorry I can't help any further. I know you've tagged the thread 'Ubuntu', but are you running Kubuntu 11.04, or have you installed k9copy in Ubuntu 11.04?

---

### Post by ae804 on 2011-06-07
> **coffeecat said:**
> Your k9copyrc file is owned by yourself, so running as sudo doesn't seem to have done any harm. When I run k9copy from the terminal in Ubuntu Natty (Unity desktop) I get no output. k9copy simply opens as normal and shows the contents of the DVD when I click on "Open" in the k9copy toolbar.

My guess is that those messages are telling you something about the kde underpinnings that k9copy is running on, but I have little experience with KDE4 so I don't know what they might mean. Googling the "Connected to deprecated..." line gives a lot of hits and seems to be a general KDE problem.

I'm sorry I can't help any further. I know you've tagged the thread 'Ubuntu', but are you running Kubuntu 11.04, or have you installed k9copy in Ubuntu 11.04?


I am pretty low on the totem poll when it comes to Ubuntu knowledge.  I know that I have downloaded from ubuntu.com the image, I burned it to a DVD, and then I installed it on the computer.  I don't know if I have something weird here, but I got k9copy to work and I backed up about 25 movies, then it all stopped working.... Well, I think that I will have to format the drive and then reinstall ubuntu.  

Is there any way I can run linux inside of windows (like a reverse wine)?

And yea, i installed k9copy in ubuntu.  I know that is where I got it.

---

### Post by coffeecat on 2011-06-07
Install Ubuntu within Windows? Yes, you can, sort of, using something called Wubi. More here:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

As far as whether you are running Ubuntu or Kubuntu, there's an easy way to tell. Kubuntu is very blue! :wink: Kubuntu uses the KDE desktop and Ubuntu uses the gnome desktop, but in 11.04 the desktop will default to the new Unity interface if your graphics hardware will support it. Unity is simply a shell sitting on top of gnome.

Each of KDE and gnome have their own set of libraries and components, but gnome applications can run in KDE and vice versa if the appropriate libraries are installed. My comment about the "underpinnings" of KDE was implying that I think something has gone wrong with one of the KDE dependencies rather than k9copy itself.

To try to fix this, without knowing exactly what has gone wrong, there are the following approaches, each more drastic than the previous. Only the last will guarantee success.

1 - Purge your personal KDE configurations so that they are regenerated when you next log in.

2 - Do 1 and reinstall k9copy.

3 - Do 1 and 2 and reinstall every dependency of k9copy as well.

4 - Reinstall the whole operating system.

I don't usually like to suggest a complete reinstall because most things are fixable, but in the long run it may be quicker for you. Let us know what you decide and whether you need any help. If you want help with the details of 1,2 and 3 I can give you directions.

---

