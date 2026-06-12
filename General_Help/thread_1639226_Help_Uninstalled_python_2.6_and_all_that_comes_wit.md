---
title: "Help: Uninstalled python 2.6 and all that comes with it.."
date: 2010-12-06
forum: General Help
---

### Post by MCube78 on 2010-12-06
Hi Everyone,

HAving worked through the shame of making this post..:

 I managed to "mark for complete uninstallation" Python 2.6 from my Lucid Lynx install. Needless to say some other 200 packages are gone with it and my computer is completely crippled..

Pretty much everything is gone.. How can I get my CPU back to life? (CPR didn't work..)

 help..

MCube

---

### Post by oldfred on 2010-12-06
I uninstalled the desktop once. I was experimenting with Kubuntu.

Can you get to a command line with Internet? It used be be you could not as the Internet setup used python also. 

If not you need a liveCD and chroot into your system to reinstall everything. I like Kansasnoob's one line version to chroot as you can just copy one line.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# not sure if above reinstalls python or not, it should, if not just do a install of python
apt-get -f install
dpkg --configure -a

If you can get to command line you can run all the above fixes, but need sudo before each line.

---

### Post by MCube78 on 2010-12-06
oldfred, 

thank you. I understand what you say, I do have one question (I'm still a bit of anewbie -- clearly...!!):

don't I want to mount sda1? That is my system partition. My cpu HD is organized as follows:

dev/sda1 (ext3) filesystem (this has the os files)
dev/sda2 (extended)
dev/sda5 (swap)
dev/sda6 (ext3) filesystem (this is my /home/)

cheers 

mcube

---

### Post by oldfred on 2010-12-06
Yes change the sda5 (which is just a reference but a lot of installs use sda5) to sda1.

---

### Post by MCube78 on 2010-12-06
ok thank you.
Fingers crossed. A little prayer to the mighty lucid lynx, and off we go..

I'll let you know how it goes :)

---

### Post by MCube78 on 2010-12-06
...so a little of an anticlimactic start..
I put in the ubuntu live CD, it asks what to do, when I select "Try Ubuntu without installing" it seems like it's starting to load, then the screen flickers (as if it had restarted) and it goes back to the Ubuntu loading logo (with the little dots under..) and just stays like that.

If I press any of the F# keys I get the error messages:
GLib-Warning: getpwuid_r(): failed due to unknown user id (0)
stdin : error 0
chroot: cannot execute mktemp: Input/Output error
....

all the errors seem to have to do with the fact it can't read/write. But it's just the Ubuntu CD running, why does it need writing?

mcube..

---

### Post by oldfred on 2010-12-06
What version are you running? 

Some more discussion here and links to bug reports with some workarounds.
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

---

### Post by MCube78 on 2010-12-06
Thank you for the link, I had indeed seen that post -- it seems like many people experienced this but it's a bit of an elusive problem.
I'm running Lucid Lynx 10.04 (I believe..)
I'm trying to see if the USB install is any more effective.

Any other suggestions?

...

more excitement to come.. :(

---

### Post by oldfred on 2010-12-06
I have an Nvidia card and all the recent versions I have had to add a nomodeset parameter to get it to boot until I had the full install and could install the Nvidia drivers.
F6 with CD, but I use USB with grub2 boot and just added the parameter to my linux boot line like I did on the first boot.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by cgroza on 2010-12-06
```
sudo apt-get install ubuntu-desktop
``` should put everything back the way it was.

---

### Post by MCube78 on 2010-12-06
Success!!! (only a few hours later..)

For anyone else googling this same problem, here's a summary of the problem and solution (for me..):

--PROBLEM: I uninstalled Python (2.6.5) from synaptic manager (which ended up deleting some other 200 bits and pieces which made the computer unusable, unconnectable, un-everything possible. ](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

--COMPUTER: Dell XPS M1210, with a Lucid Lynx 10.04 installation

--LIVECD: LiveCD failed from CD (the error was the familiar GLib-Warning**: getpwuid_r(): failed due to unknown user id (0), and from USB (it booted to BusyBox -- with no connectivity).

--SOLUTION (for my computer..):

i. Press ESC during GRUB loading to go to the menu
ii. Select the "oldest" kernel in recovery mode (I didn't have to make any editing to the commands).
iii. In the following menu I selected the "drop to command line with connectivity" (or something like that.. sorry can't remember!).
iv. Once I had the command line with internet I simply followed the instructions posted (above) by oldfred. Two minor things with following those instructions: (1) on my specific computer it's dev/sda1, not sda5, so check for which is the appropriate one on yours; (2) the `sudo cp /etc/resolv.conf /mnt/etc/resolv.conf' command gave me an error (because they are the same file..). 

Other than that, it worked like a charm! I paste below the quote from oldfred's post.

cheers

mcube

> 

FROM OLDFRED'S POST:

sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# not sure if above reinstalls python or not, it should, if not just do a install of python
apt-get -f install
dpkg --configure -a


---

