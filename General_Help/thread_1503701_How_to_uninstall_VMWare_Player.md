---
title: "How to uninstall VMWare Player"
date: 2010-06-07
forum: General Help
---

### Post by lads on 2010-06-07
Hello everyone,

Days ago I installed VMWare Player to run a particular virtual machine. Even after a few upgrades this program still works pretty bad with Gnome and I wish to uninstall it; VBox does the same job but much better. 

Problem is: how do I do it? There doesn't seem to be any package registered for vmware. Here's what I've run:

```
$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware-player
```

```
$ dpkg --get-selections | grep vm
libdevmapper1.02.1				install
libxvmc1					install
libxxf86vm1					install
xserver-xorg-input-vmmouse			install
xserver-xorg-video-vmware			install
```

```
$ dpkg --get-selections | grep player
media-player-info				install
mplayer-nogui					deinstall
```

I'm clueless. Can anybody help? Thanks,

Luís

---

### Post by dcstar on 2010-06-07
> **lads said:**
> Hello everyone,

Days ago I installed VMWare Player to run a particular virtual machine. Even after a few upgrades this program still works pretty bad with Gnome and I wish to uninstall it; VBox does the same job but much better. 
..........
I'm clueless. Can anybody help? Thanks,

Luís

[LIST=1]
[*]Go to the Virtualization forum
[*]Read about the version of VMware Player that actually works with 10.04
[*]Install it or find the instructions on removing the version you installed.
[/LIST]

---

### Post by lads on 2010-06-07
Hello David, thank you for your reply.

I don't think this thread belongs in the Virtualization forum, since it is not specifically on that issue, but on an uninstall procedure in Ubuntu.

Th VMWare Player version I'm using is 3.1.0 build-261024. A google search for that version plus the worlds "ubuntu" and "uninstall" returns no relevant results.

---

### Post by ba_saish on 2010-06-08
vmware-installer -u NAME

---

### Post by dcstar on 2010-06-08
> **lads said:**
> Hello David, thank you for your reply.

I don't think this thread belongs in the Virtualization forum, since it is not specifically on that issue, but on an uninstall procedure in Ubuntu.

Th VMWare Player version I'm using is 3.1.0 build-261024. A google search for that version plus the worlds "ubuntu" and "uninstall" returns no relevant results.

And the instructions on the VMware site tell you exactly how to do it.

All the installation and removal instructions on all Ubuntu VM platforms are also in the Virtualization forum, because the Virtualization forum is where Virtualization questions go.

---

### Post by tolgainci on 2010-07-28
Here's the correct answer for people who may not be experienced enough to find their way into the Virtualization forum and end up here through forum search. (like me). Type the following in a terminal and follow the instructions:

> sudo vmware-installer -u vmware-player

Please feel free to move this thread to where it belongs, it might actually help someone ;). Lads can you mark this thread [SOLVED] if it helps?

---

### Post by spiderbaby on 2011-09-16
"sudo vmware-installer -u vmware-player" did not work for me. In my case, I had accidentally tried installing VMware Workstation on top of an old VMplayer installation (installed by either by me or an older user). This is a big no-no as you are meant to uninstall VMplayer first.

The Workstation installation failed and left me with a big mess of half-installed programs. The fix for it was to follow the VMware knowledge base document "Manually uninstalling VMware Workstation from Linux hosts" found here:
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=38]("http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=38")

Not all the steps worked since my installation was in a limbo state but following all the steps allowed me to install Workstation.

---

### Post by Jerin P Robert on 2012-08-24
"sudo vmware-installer -u vmware-player" is worked for me in Ubuntu 10.04, remove the vmware player v4.0.4 and after that i can install the VMware Workstation 8. 

Thanks for the post...

---

