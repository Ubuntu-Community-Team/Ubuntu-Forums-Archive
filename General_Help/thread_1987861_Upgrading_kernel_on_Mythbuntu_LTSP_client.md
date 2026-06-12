---
title: "Upgrading kernel on Mythbuntu LTSP client"
date: 2012-05-26
forum: General Help
---

### Post by rage_311 on 2012-05-26
Hi,

I have a 64-bit Ubuntu 10.04.3 server which I'm using as a server to boot remote LTSP (via mythbuntu-diskless-server) clients from.  I followed the walkthrough for setting this up ```
https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless
``` and the client boots into Mythbuntu 10.04 just fine.

One client that I have is going to be using the onboard HDMI for video and audio -- it's an Intel Sandy Bridge Celeron G530 processor.  In stock Mythbuntu 10.04, I am unable to get the HDMI to show up as an audio device, either in the system ```
aplay -L
``` or in MythTV's setup.  After doing some digging, it looks like the Sandy Bridge HDMI audio isn't really supported until kernel version 2.6.39+.  So, I figured that the easiest thing to do would be to upgrade the kernel to the newest supported version for 10.04.  I chrooted into the /opt/ltsp/amd64 directory (which is the root filesystem for the LTSP clients), and did ```
apt-get install linux-headers-generic-lts-backport-oneiric linux-image-generic-lts-backport-oneiric
``` (as root user).  It seemed to update the kernel to 3.0.0-19 just fine and set the symlinks from vmlinuz and initrd.img to point to the new files.  I then exited my chroot environment and ran ```
sudo ltsp-update-kernels
``` which ran just fine and appeared to update everything appropriately.  But when I reboot my remote client, it stops partway through the booting process at these messages:
```
TFTP prefix: /ltsp/amd64/
Trying to load: pxelinux.cfg/default
Could not find kernel image: vmlinuz
```
I checked and vmlinuz is right where it is supposed to be and pointing to the new, valid kernel files.  I can change the pxelinux.cfg/default to read the old initrd.img and vmlinuz files (now located at initrd.img.old and vmlinuz.old in the same directory), and the client will boot just fine on the older kernel.

So... any ideas as to why it refuses to boot with the new kernel?  Or why it "can't find" it?

Am I going about this the right way?  Or is there an easier way to get Sandy Bridge HDMI audio support on the 2.6.32 kernel?

Is it possible and/or reasonable to create an LTSP image of Mythbuntu 12.04?  If so, how?

Please let me know if any more information is needed.  Thanks!

---

### Post by rai4shu2 on 2012-05-26
I doubt the metafiles have changed much for 12.04. It should probably work the same as 10.04. 12.04 has the 3.2 kernel, so it should work with your hardware no problem.

---

### Post by rage_311 on 2012-05-27
Thanks for the reply.

I have now verified that a regular Mythbuntu 12.04 install works perfectly with my hardware.

Now, I guess my question is... How do I get an LTSP image built for Mythbuntu 12.04 on a 10.04.3 server?  Where does it get the information for the packages to "build" the client (via ltsp-build-client, with --mythbuntu switch)?  I can see it grabbing packages from the Lucid repos, but where are the repos specified?  Is this something that's configurable?

Would it be easiest to install Ubuntu 12.04 in a virtual machine, build the LTSP client files, then transfer them to the actual server?

Any direction in this matter would be greatly appreciated!

---

### Post by rage_311 on 2012-05-27
Ah-ha! I think I'm getting closer...

I did a little digging around in the ltsp-build-client man pages and noticed an option called "--dist".  With this option, I can specify which Ubuntu/Debian version to build the client for.  So, in addition to the --mythbuntu and --mythbuntu-user-credentials options, I'm using ```
--dist precise
```My entire command looks like this:
```
sudo ltsp-build-client --purge-chroot --arch amd64 --dist precise --mythbuntu --mythbuntu-user-credentials="mythuser:password"
```
Everything seems fine with that command -- it starts building a Mythbuntu 12.04 client, as far as I can tell.  I can see it pulling from Precise repos and adding MythTV specific packages, so it looks like it's building it correctly.  After several minutes of configuring the downloaded packages, it errors out with these messages:
```
Adding user `mythuser' ...
Adding new group `mythuser' (1000) ...
Adding new user `mythuser' (1000) with group `mythuser' ...
Creating home directory `/home/mythuser' ...
Copying files from `/etc/skel' ...
usermod: group 'admin' does not exist
error: LTSP client installation ended abnormally
```
and it won't finish building the client image.  What do I need to look at here?  Why is it trying to use the admin user group and why doesn't the group exist?

---

### Post by rai4shu2 on 2012-05-28
Right. In recent years, the "admin" group was removed from the system. The admin group is now called "sudo" in 12.04.

I suppose you could create the group. See group(5).

---

### Post by imachavel on 2012-05-28
sorry I'm not a sys admin expert, this is a permissions issue? When you configured all the necessary conf files between your server and client, didn't you need to configure a permissions file? So if it's not a sysadmin file anymore what directory is the .conf file for Sudo in? This all sounds too risky, like you are editing a file too important to the entire file system permissions, sudo?

server admin is gone from ubuntu now configure sudo

what you are saying is webmin doesn't exist in ubuntu admin configuration any more? No shitting huh?

---

### Post by imachavel on 2012-05-28
also, am I assuming that you are trying to boot to a network drive on a computer with no disk? Never tried configuring that, wouldn't know how to configure the i.p. informationf from the bios. Was a little confused as to how many nodes you are working with, and which machine you are trying to configure, etc. etc.

I could be wrong, that link in no way shape or form talks about connecting to a network drive, it's only that the url includes the word "diskless", although it's not in the header or body of the html page, simply put the web page says nothing about configuring that in any way shape or form. Sorry to debo this thread with garbage. It was a great thread until I got involved

---

### Post by rage_311 on 2012-05-28
> **rai4shu2 said:**
> Right. In recent years, the "admin" group was removed from the system. The admin group is now called "sudo" in 12.04.

I suppose you could create the group. See group(5).

Interesting... I wasn't aware that they did away with the admin group.  So, it would appear that it's still scripted to get some user/group configuration settings from pre-12.04 distro information, regardless of the "--dist precise" switch.  Any ideas on how I could instruct it to create/use the sudo group instead of admin for the client's environment?  I can't get it to build the client image in the first place, so I can't chroot into it and set this up post-install.  I don't see any other options for ltsp-build-client which would allow changes of that sort.  I'm using the latest ltsp-server package available for Lucid (5.2.1-0ubuntu9), by the way.


@imachavel
From my understanding, the only user/group/security changes that will have to be made will be in the client's "environment", which is stored on the server, but has its own root, security files, etc.  It's basically an entire, separate *buntu (or Debian) file system.  It sounds like it was only the naming of the "admin" group that was changed, and nothing to do with the actual functionality.  I could be wrong since this is the first I've heard of it.

I AM attempting to boot a diskless remote frontend client.  This link has more info on how that process generally works ```
https://help.ubuntu.com/community/DisklessUbuntuHowto
```I will have 3 remote, diskless, network clients using this configuration and one server that is my dhcp, tftp, and nbd server.

---

### Post by rage_311 on 2012-05-29
Any thoughts?

---

