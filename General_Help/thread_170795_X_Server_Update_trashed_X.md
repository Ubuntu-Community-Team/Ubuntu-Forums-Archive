---
title: "X Server Update trashed X"
date: 2006-05-05
forum: General Help
---

### Post by rcarring on 2006-05-05
This is the second time I have applied the X-org updates and yet again it is trashed X on my vmware device. I am running Ubuntu 5.10, and I noticed after installing the 69 updates, and this time rebooting machine it found problems with the default-display-configuration and one of the folders it insists now does not exist, the one being /etc/X11/X -- even though I can see the folder in mc and also when doing ls, running startx at the command line throws an error saying that this particular folder is missing.

This is fairly catastrophic, as I imagine many people are using the vmware appliance, and if any of them run the update manager they will kill X completely.

If anyone can telll me how the hell to reconfigure X from the command line it would help me greatly, as XF86Config doesn't work.

If I cant fix it, then I will have to create a new appliance instance and deselect anything to do with X on the updates.

---

### Post by rcarring on 2006-05-05
Ok, I went outside and had a smoke, and did some hard thinking:

When the update manager runs, it downloads the updates from the appropriate repository, caches the files locally for installation, prepares packages and then installs them.

Default behavior appears to be that the old files are removed. Now, Xserver appears to be massively upgraded, so the old X stuff is trashed and the new stuff installed, except I believe the trashing fractures the symbolic link to X for a start and somehow this throws the system into a major confusion.

I am reporting this bug here, as I hope that by sharing it a) others will be made aware of it and b) maybe I may even be able to fix it =D

I really don't want to start over again for a third time.

UPDATE:

This seems to be the problem - the update has removed package xserver-xfree86 from my virtual machine. X cannot start because it is no longer installed.

I am running as root, and typed in dpkg-reconfigure xserver-xfree86

I get a note that xserver-xorg-core 6.8.2-77 1 is a virtual package and there is no candidate available for installation.

---

### Post by Slim Odds on 2006-05-05
[QUOTE=rcarring]UPDATE:

This seems to be the problem - the update has removed package xserver-xfree86 from my virtual machine. X cannot start because it is no longer installed.

I am running as root, and typed in dpkg-reconfigure xserver-xfree86

I get a note that xserver-xorg-core 6.8.2-77 1 is a virtual package and there is no candidate available for installation.[/QUOTE]

ubuntu 5.10 does not use xfree86, it uses xorg.

Maybe try reconfiguring xorg instead of xfree86

---

### Post by rcarring on 2006-05-05
It tried substituting xorg for xfree86, that said xserver-xorg was not installed.

I ran deselect but I really am not sure what to do.

I can restore the original machine, but it is kinda annoying that the update trashed X

---

### Post by Slim Odds on 2006-05-05
[QUOTE=rcarring]It tried substituting xorg for xfree86, that said xserver-xorg was not installed.

I ran deselect but I really am not sure what to do.

I can restore the original machine, but it is kinda annoying that the update trashed X[/QUOTE]

It might be somehow related to the vmware installation. I just updates 2 machines yesterday with the same xorg updates and they both worked fine.

---

### Post by rcarring on 2006-05-05
I checked the vmware forums. There doesn't seem to be any posts relatiing to problems met updating xorg. I did find that booting a vm with Dapper Drake beta led to the following:

a) extremely slow boot up
b) when gdm loads after about ten minutes the mouse freezes up

I guess I am going to have to start again, and make sure I don't update anything relating to xorg.

UPDATE:

The sledgehammer approach --

sudo su -
Logged in as root

apt-get install xorg-common
apt-get install xserver-xorg

startx

logged into desktop as root (gdm)

logout

back to command line

exit

now logged in as user

startx

desktop loads

It is working again.

I think the updates dont work with vmware.

---

### Post by simohell on 2006-05-05
The recent update messed my X on my desktop, but not on my laptop.

I think for me it is to do with the graphics driver:
my laptop has Intel 915GM and uses driver i810 - no problems
my desktop has Matrox G450 and uses mga - which wont work.

I changed my desktop to use vesa and now X works. Unfortunately I use 1600x1200  TFT, and with vesa  I wont reach that high resolution.

---

### Post by rcarring on 2006-05-05
One final step, I forgot to mention...

Logout from desktop and back to command line.

sudo su -

Logged in as root

shutdown -r now

Machine shutsdown and reboots

Loads stuff

Loads gdm and desktop

I can now logout and get to the login gui state.

[I have crossposted a reference to this thread in the User Suggestions (moderated) forum on the VMTN forums -- hope this is okay?]

---

### Post by jrb114 on 2006-05-05
I've got a similar problem that may be related. (Not sure if it's due to the X update (suspect so) or the latest kernel update.)

See

[http://ubuntuforums.org/showthread.php?t=170869](http://ubuntuforums.org/showthread.php?t=170869)

Ta,

J

---

