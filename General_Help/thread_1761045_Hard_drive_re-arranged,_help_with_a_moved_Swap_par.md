---
title: "Hard drive re-arranged, help with a moved Swap partition, grub menu"
date: 2011-05-17
forum: General Help
---

### Post by dave.kts on 2011-05-17
I had to do some serious moving of data / partitions to make space for backups and remove some distro's that werent working, and replace a failing Spinpoint F3 drive. (3rd failed drive now in 6 months :().  Ubuntu resides on my WD black drive that I use for DAW storage

My swap partition was sdc5 in an extended partition. It has been moved to the beginning of this drive, followed by Ubuntu partition, followed by new ntfs storage partition. I moved the ubuntu partition (same partition label) and resized with gparted and it was succesful, booted right up no appearant problems, only thing is ubuntu is not automatically using the new swap partition (now on sdc1). It will use it if i turn it on in gparted, but each time i boot, ubuntu isnt finding it. (4 gigs of RAM, so i dont really need the swap that badly. actually i have yet to even see it used yet no matter what im doing ;))

ive searched around and found a bunch of confusing or non relavant info on this.

Also I want to update grub to remove unused boot menu items, and so it will find my new XP install on sda (disk 0).. my previous XP installation was all screwed up and cross-weaved between 2 drives/2 installs of XP.. both of the XP entries in grub menu used to boot me into the same XP partition even tho i had 2 installs on 2 different HD's and showed up in grub for both sda and sdc.... anyways i keep finding info that is outdated or not relevant to me.
My distro is super ubuntu 10.10

---

### Post by oldfred on 2011-05-17
You probably need to edit fstab with the correct UUID for your new swap partition. An update grub will find other bootable systems if they are ok.

To see your UUID and partitions:
sudo blkid
sudo fdisk -l
cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

Always run this after editing fstab to make sure it is ok. If ok, it just remounts everything without any messages. If a message do not reboot without resolving the error.

sudo mount -a

#to get the menu updated:
sudo update-grub

If you want to know what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

New version is a zip file that you have to extract to get the .sh file to run.

---

### Post by dave.kts on 2011-05-17
Thanks, all cleared up!
it wouldn't let me use the cp command to make the backup but i just used "save as" in gedit for the backup, edited the UUID in the original, and everything remounted no problems.

---

### Post by oldfred on 2011-05-17
Glad it worked. 

I forgot sudo again. I do that all the time on my commands, but have learned when ever it does not work to just up arrow and add sudo.

---

