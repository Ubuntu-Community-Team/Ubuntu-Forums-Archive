---
title: "Mounting network drive"
date: 2006-03-23
forum: General Help
---

### Post by [h2o] on 2006-03-23
I am running Dapper Drake, but I believe that this is more a general Gnome thing, so I post this question here, and hope noone will get mad ;)

Now to the problem. I am a laptop user with a limited harddrive, and therefore I have a USB/ethernet harddrive connected to the network. It is connected directly to my router and shows up as a SAMBA share.
I connected to it by choosing the "Connect to server..." option and it works fine. First problem is: In some programs, Banshee as an example, I can't browse my way to it, and thus I can't import all my music. Irritating, so I changed my fstab to mount it on /mnt/edmini.
But, drives are mounted before network is started (managed by NetworkManager) and it fails to mount it at boot. So, everytime I boot up I have to start a console and enter "sudo mount /mnt/edmini" and enter my password. It's a bit annoying.

Is there a way to solve this in some kind of automagical way? I know I could create a script which handles the mounting, but I prefer it when things just work without me having to do something :)

---

### Post by magisterludi on 2006-03-23
you can put a init script in /etc/init.d and link it from rc2 with a number higher than your network startup scripts.

---

### Post by [h2o] on 2006-03-24
Ah...that would be a solution I guess. But... mounting requires root...does initscripts automatically run like root? Should my script say "sudo mount /mnt/edmini" or "mount /mnt/edmini"?

---

### Post by magisterludi on 2006-03-24
does not require sudo

---

### Post by morguns on 2006-03-25
[QUOTE=magisterludi]you can put a init script in /etc/init.d and link it from rc2 with a number higher than your network startup scripts.[/QUOTE]
could someone please explain this in a little more detail? i'm having problems mounting an nfs share at boot. to be specific, 

sudo mount -t nfs 192.168.1.9:/path/to/share /mnt/point
works fine when entered at the command line, but 

192.168.1.9:/path/to/share  /mnt/point     nfs     rw,hard,intr 0 0
in fstab fails.

---

### Post by copperhead on 2006-03-25
Have you tried running "/etc/init.d/mountnfs.sh"?  This should mount all your remote samba and nfs mounts.

---

### Post by Barrakketh on 2006-03-25
[QUOTE=copperhead]Have you tried running "/etc/init.d/mountnfs.sh"?  This should mount all your remote samba and nfs mounts.[/QUOTE]
You can find a guide to mounting samba shares at boot [here](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html[/url).

---

### Post by Ranime on 2006-03-26
Read this: [http://www.ubuntuguide.org/#automountnetworkfoldersall](http://www.ubuntuguide.org/#automountnetworkfoldersall)

It works! dont forget to apt-get install smbfs!

---

### Post by morguns on 2006-03-26
[QUOTE=copperhead]Have you tried running "/etc/init.d/mountnfs.sh"?  This should mount all your remote samba and nfs mounts.[/QUOTE]thanks copperhead, how should i run it? in sessions, startup programs or something?

[QUOTE=Barrakketh]You can find a guide to mounting samba shares at boot [here](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html[/url).[/QUOTE]thanks Barrakketh, i've read the page a couple of times and it's still digesting. pardon my ignorance, but are samba shares and nfs shares the same? i ask because i'm working with a simpletech nas device and it supports nfs according to what i've read, but perhaps it can do samba also? if it does both, is there a reason i should use one over the other (eg security, ease of use (lol!), compatibility)?

[QUOTE=Ranime]Read this: [http://www.ubuntuguide.org/#automountnetworkfoldersall](http://www.ubuntuguide.org/#automountnetworkfoldersall)

It works! dont forget to apt-get install smbfs![/QUOTE]thanks Ranime, but i don't know if the info will apply in my case. as of now user/pass is not required to access the share (i read somewhere that the pass is sent across the network in the clear so i'm not enabling it yet). that may change, i'm just trying to get the basics figured out right now. also, my confusion re: nfs vs. samba applies here also.

thx everyone, the feedback is much appreciated!

---

### Post by copperhead on 2006-03-26
First of all, make sure that you can run the command and it works (I had a problem with it [hosing my system]("http://ubuntuforums.org/showthread.php?t=106000") after I ran it, and I had to do a slight modification.

So, boot your system clean, then try running the following:
```
$ sudo /etc/init.d/mountnfs.sh
```
If that mounts your drive correctly, then do the following:
```
$ sudo update-rc.d mountnfs.sh start 99 2 .
```
Then reboot and see if your shares mount automatically.

---

### Post by morguns on 2006-03-27
interesting info copperhead. thx especially for advising the first command as it definitely hosed the system :) the unfortunate thing is it didn't even mount the share. i don't see much point in commenting out the bootclean stuff if it can't mount the share anyway. 

does it really need to be this difficult? (sorry for whining.) i'll keep working on this, but i clearly need to do more research so i can at least converse intelligently on the subject :)

---

### Post by el3ktro on 2006-06-04
I have a similar problem and I'm trying for MONTHS now to somehow solve this. I can't believe tht Linux fails so much in doing proper networking on the desktop :-(

I also have a desktop computer, which is not always on, and I have a laptop which sometimes has a wired, sometimes has a wireless and sometimes has no connection at all (with networkmanager). All I want is to _transparently_ and _automagically_ mount the directory on the desktop! But it's almost impossible!

GnomeVFS is nice yes, but not supported by many programs. NFS is absolutely crap, when you loose the connection, everything freezes and goes crazy. Ironically, Samba works much better.

The perfect solution would be if networkmanager could handle this. If networkmanager has any kind of network connection, then it should transparently mount a share when I access it and immideately unmount it after I stopped using it. If no network connection is available, then it should just not mount the remote directory.

I think I'll write to the networkmanager devs if something like this could be done ...

Tom

---

### Post by TestUser on 2006-07-31
Hi

Sorry for noob question but if I like to do the fix mentioned earlier 
$ sudo /etc/init.d/mountnfs.sh 
$ sudo update-rc.d mountnfs.sh start 99 2 .

how to do this when mountnfs now is placed in /etc/network/if-up.d ?


Tu

---

