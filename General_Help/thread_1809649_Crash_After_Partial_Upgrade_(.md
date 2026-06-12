---
title: "Crash After Partial Upgrade :("
date: 2011-07-21
forum: General Help
---

### Post by fadi hamadneh on 2011-07-21
[SIZE=3][B]I was using my ubuntu 10.04 LTS computer normally ... suddenly .. the update manager asked me to that it should make something called : Partial Upgrade .. i accepted ... and then a long process began .. the title was : Distribution Upgrade 

then my computer ran out of battery power .. and it was turned off during the process !!
I turned it on again .. the grub menu was normal ... the splash screen came normally ... but the login screen has been changed ... not my customized themes ... with my user name ... but without mouse control or keyboard control :(  i cant login ...  
i want my files ...  :( i want my settings ,, bookmarks , customizations  :( i want my ubuntu backk normally :( 
is there something in ubuntu like system restore ??? i want everything back  :( i will lose many things .. many important files and firefox bookmarks ... Plsss help me guys ... :([/B][/SIZE]

---

### Post by fadi hamadneh on 2011-07-22
> **fadi hamadneh said:**
> [SIZE=3][B]I was using my ubuntu 10.04 LTS computer normally ... suddenly .. the update manager asked me to that it should make something called : Partial Upgrade .. i accepted ... and then a long process began .. the title was : Distribution Upgrade 

then my computer ran out of battery power .. and it was turned off during the process !!
I turned it on again .. the grub menu was normal ... the splash screen came normally ... but the login screen has been changed ... not my customized themes ... with my user name ... but without mouse control or keyboard control :(  i cant login ...  
i want my files ...  :( i want my settings ,, bookmarks , customizations  :( i want my ubuntu backk normally :( 
is there something in ubuntu like system restore ??? i want everything back  :( i will lose many things .. many important files and firefox bookmarks ... Plsss help me guys ... :([/B][/SIZE]

guys please help

---

### Post by Quackers on 2011-07-22
A tip, never run updates (and certainly not upgrades) on battery power.
It is asking for a catastrophe - as you can see.

Another tip, always have backups! Then you won't lose things.

It's possible there has been damage done to your system.
You could have a look at the thread below. The users problems were solved, but he wasn't running an upgrade at the time.
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)

---

### Post by sikander3786 on 2011-07-22
Another attempt would be trying to upgrade/fix your PC via the Recovery mode's Root Shell (if it allows you to boot that successfully).

From Grub menu, choose Recovery Mode (the option below the normally used one probably) and then choose Drop to Root Shell. Run these commands one by one:

```
dhclient eth0
```

Where 'eth0' is your network interface. This command would connect your PC to the internet.

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If the commands finish without any errors, hopefully your install would be repaired and you might be able to boot it successfully.

If the commands don't work, the only choice is to boot an Ubuntu Live CD/USB and then mount your partition and copy over your data and do a fresh install.

If you are unable to even get to the Root Shell, you can try to Chroot your install from a Live CD and then run the same commands as listed above.

To Chroot, boot an Ubuntu Live CD/USB and get to a Terminal, then run these commands one by one:

```
sudo mkdir /mnt/temp 
sudo mount /dev/sd[COLOR="Red"]**XY**[/COLOR] /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

Replace '[COLOR="Red"]**XY**[/COLOR]' with your intended partition to which Ubuntu is actually installed. It should actually look something like 'sda1', 'sda2' etc. You can find it by running this command:

```
sudo fdisk -l
```

Once Chrooted, run the same commands as mentioned above.

Good Luck!

---

### Post by Elfy on 2011-07-22
Duplicate closed - also please note this from the Code of Conduct.

> Use color and font properties for highlighting _portions_ of your text, and _not for all_ of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

---

