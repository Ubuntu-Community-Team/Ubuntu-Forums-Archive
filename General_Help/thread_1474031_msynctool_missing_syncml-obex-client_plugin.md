---
title: "msynctool missing syncml-obex-client plugin"
date: 2010-05-05
forum: General Help
---

### Post by hkam on 2010-05-05
I'd like to get sync between evolution and nokia E51 running. Following the instructions given in [https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync). 

Therefore I need the plugin syncml-obex-client, but I cannot get it. I guess the problem is the that the package opensync-plugin-syncml cannot be downloaded.

Is it not part in ubuntu 10.04 anymore?

kam@kam-laptop:~$ sudo aptitude install multisync-tools opensync-plugin-evolution opensync-plugin-syncml libsyncml-utils
[sudo] password for kam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "opensync-plugin-syncml"
Couldn't find any package whose name or description matched "opensync-plugin-syncml"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

kam@kam-laptop:~$ msynctool --listplugins
Available plugins:
palm-sync
evo2-sync
file-sync
gnokii-sync
irmc-sync
synce-opensync-plugin
sunbird-sync
google-calendar
barry-sync

---

### Post by truchas on 2010-05-07
Hi!

I have the same problem. Please, anyone can help us?

Thanks

---

### Post by tattwood833 on 2010-05-08
Yes, me too.

  syncml-obex-client

is missing from --listplugins

and when I run msynctool --sync nok

I get "group is locked"

loving 10.04 otherwise!

t x

---

### Post by tattwood833 on 2010-05-08
It seems the clever people are talking about it here

[https://bugs.launchpad.net/ubuntu/+source/libopensync-plugin-syncml/+bug/524938](https://bugs.launchpad.net/ubuntu/+source/libopensync-plugin-syncml/+bug/524938)

but this is too much for me...

can someone shout when there is a set of instructions for how to get it working again?

thanks!


tom x

---

### Post by Irihapeti on 2010-05-08
I'm one of the people posting on the bug report and I've been asked to clarify things a bit further here. I hope I'm successful. :)



Opensync-plugin-syncml and two of its dependencies were removed from the Lucid repositories because the dependencies are considered to be obsolete.

Fortunately, we can still install the dependencies by hand.

Three files are involved: libsoup2.2, libsyncml0 and opensync-plugin-syncml.

Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) About 1/3 of the way down the page, there is a section called "Search Package Directories".

Set the distribution to "Karmic" and section to "any"

Then search for "libsoup2.2". You'll get three results. The first one is the one we want. Click on the "karmic" link and it will take you to a page where you can download it (see panel at the bottom of the page). Choose your architecture and then your mirror.

Do the same for libsyncml and opensync-plugin-syncml.

You should end up with these three .deb files.

[INDENT]libsoup2.2-8_2.2.105-4ubuntu1_i386.deb
libsyncml0_0.4.6-3build1_i386.deb
opensync-plugin-syncml_0.22-2_i386.deb
[/INDENT]
Double-click on each one in turn, in the order shown. That will launch the manual installer. It will want to install other packages as well, which you will need to allow it to do.

That's it. Now you can set up your system to use syncml.



If the sync group is locked, you probably have a permissions problem with USB devices.

That can be fixed by adding a rule in /etc/udev/rules.d
Instructions for doing that are here, in the [USB]("https://help.ubuntu.com/community/NokiaEvolutionSyncing") section. Sorry, there doesn't seem to be any way around this other than command line.

My rules file is a little different from what that page shows, and I'll post it here to give you an idea. Obviously, you'll need to change the idProduct to match your phone.

```
BUS=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="002f", MODE="0660", GROUP="dialout"
```

In Lucid, you'll get a rude error message when it boots up (if you are booting with "quiet" off) but it still works - on my machine, anyway.

Here's another useful link for setting up sync with Nokia Symbian 60 v3 phones: [http://myrtti.fi/blog/2009/03/25/howto-sync-s60v3-phone-to-google-calendar-and-make-backups-of-contactscalendarnotes/](http://myrtti.fi/blog/2009/03/25/howto-sync-s60v3-phone-to-google-calendar-and-make-backups-of-contactscalendarnotes/) OK, it's for google calendar, but the bit for configuring the syncml plugin is very useful.

You can install multisync0.90 if you want to use a GUI for this.



I've found that the sync process isn't all that robust. That's a nice way of saying that errors easily occur. :) I'm using a Nokia 6120 classic phone and the sunbird-sync plugin for Lightning (Thunderbird extension).

I won't go into detail about that yet, because you people may not get the same errors - different phones and PIM software. I can post that later if it's wanted.

---

### Post by tattwood833 on 2010-05-09
Thank You so much for all your help.

downloaded the three files as you said.

libsoup2.2 installed no problems.

but libsyncml-dev_0.4.6-3build1_i386.deb won't install - 
Error: Dependency is not satisfiable: libsyncml0 (= 0.4.6-3build1)

and, consequently, neither will opensync-plugin-syncml_0.22-2_i386.deb
Error: Dependency is not satisfiable: libsyncml0 (>= 0.4.5)

Have I done something wrong?

Let me know if you get a moment...

Cheers!

Tom x

---

### Post by Irihapeti on 2010-05-09
> **tattwood833 said:**
> Thank You so much for all your help.

downloaded the three files as you said.

libsoup2.2 installed no problems.

but libsyncml-dev_0.4.6-3build1_i386.deb won't install - 
Error: Dependency is not satisfiable: libsyncml0 (= 0.4.6-3build1)

and, consequently, neither will opensync-plugin-syncml_0.22-2_i386.deb
Error: Dependency is not satisfiable: libsyncml0 (>= 0.4.5)

Have I done something wrong?

Let me know if you get a moment...

Cheers!

Tom x

You need libsyncml0_0.4.6-3build1_i386.deb from the same source.

Unless you are going to be compiling stuff, you don't need the libsyncml-dev file at all.

---

### Post by tattwood833 on 2010-05-09
when you say I need it from the same source what do you mean? sorry...

I got all three files from the same mirror...

sorry, I'm rubbish.
!
tom x

---

### Post by Irihapeti on 2010-05-09
Maybe I'm not expressing myself very clearly.

You need to get libsyncml0_0.4.6-3build1_i386.deb from [http://packages.ubuntu.com](http://packages.ubuntu.com), by searching for "libsyncml0" in the Karmic distribution, section "any".

Only one choice should come up.

It doesn't matter which mirror you get it from; it's exactly the same file.

---

### Post by tattwood833 on 2010-05-09
my fault!

silly silly silly!

all three packages installed. great.

now when I run msynctool I get the following error
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error

and also when I run hcitool scan
Device is not available: No such device

so it appears the bluetooth has gone away...

continual thanks, how are things in NZ, I spent a couple of weeks in Wellington in 2006 - loved it...


t x

---

### Post by Irihapeti on 2010-05-09
I'm glad we've got that sorted out. Writing so that everyone understands what I'm trying to say isn't always easy. But I like to know about it so I can improve.

I'm sorry, I don't know a great deal about bluetooth, because I don't use it much. I prefer to use the USB cable for syncing. I found [another link]("http://antoine.ginies.free.fr/syncnokiae70/syncnokia.html") about setting up Nokia phones for bluetooth. As far as I know, you don't need to play with udev rules files to get bluetooth to work, unlike USB. I've also set up obextool, which does a similar job to PC Suite or Ovi Suite, to use over USB. I tried it a couple of times with bluetooth but I recall I had some trouble with pairing.

I'm glad you enjoyed Wellington. I lived in Wellington (actually, Lower Hutt) for about 25 years and liked it, apart from the strong, cold southerlies in the wintertime. I hope you had good weather while you were there.

---

### Post by hkam on 2010-05-09
Thanks Irihapeti! Plugin is now available and Connection works.

---

### Post by kangar on 2010-05-15
It is also possible to add the old package sources in synaptic to install the packages, although I think it is not recommended ;)
adding "deb [http://*de.archive.ubuntu.com/ubuntu*]("http://%3Ci%3Ede.archive.ubuntu.com/ubuntu%3C/i%3E") karmic main universe" works for me. 

installing is now just installing opensync-plugin-syncml. dependencies are added automatically.

but the syncml-obex-client command is not found in the terminal. msynctool --listplugins list it. where should I find it? Does anyone now?

Edit: Found it in libsyncml-utils 0.4.6-3build1.
This link has also helped me: [http://en.opensuse.org/OpenSync/SyncML-OBEX-Client](http://en.opensuse.org/OpenSync/SyncML-OBEX-Client)

---

### Post by summentier on 2010-05-16
Thank you for the detailed instructions on installing the SyncML support manually.

However, I'm wondering if these packages conflict with a future release of libsyncml or the syncml plug-in to the opensync framework. And what are the security implications of installing a package that is maintained for a different version of the distribution?

Does anybody know if there will be any SyncML plugin at all for 10.04, since the bug comments talked about "feature freeze"? Or do I have to wait for half a year until the next distro upgrade?

---

### Post by Irihapeti on 2010-05-16
I don't know the answers to any of these questions for certain. Regarding the security question, you'd need to ask someone with more knowledge than I have.

I get the impression that there won't be a syncml plugin *at all* for 10.04. That is, unless someone creates a PPA.

The opensync team don't recommend using the latest version, 0.39, for production use. The next stable version is 0.40, and no date is given for its release.

Maybe when that happens (if it's while 10.04 is still supported) something can be done about a PPA.

Not much help, I know. In the meantime, what we have is about the best we can do.

---

### Post by summentier on 2010-05-17
@Irihapeti: Thank you for your fast and concise answer!

The situation is not very satisfactory. I think I'll have a shot at the manual installation after all...

---

### Post by oliver69 on 2010-05-28
I also deeply missed syncml-obex-client! :sad:

Searching for an alternative I found [http://syncevolution.org](http://syncevolution.org) - perhaps interesting for others who read this thread. I tried the PPA, but then compiled newest 1.0beta3 from its sources. Although beta it works quite reliable and very fast!

To compile it including bluetooth and gui do:
```

sudo apt-get install libboost-dev libsqlite3-dev libpcre3-dev libsynthesis-dev libbluetooth-dev libebook1.2-dev libical-dev libnotify-dev 
./configure --enable-bluetooth  --enable-gui=gtk
make
sudo make install

```

---

### Post by Nephiel on 2010-09-17
Installing those three Karmic packages seems to do the trick. Thanks!

---

