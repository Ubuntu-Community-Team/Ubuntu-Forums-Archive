---
title: "Trying to boot from Win7 to Ubuntu from Grub2"
date: 2011-07-30
forum: General Help
---

### Post by cjack2964 on 2011-07-30
[SIZE=3][SIZE=2]Hi everyone, this is my first post on this forum so please be gentle with me. I have been using ubuntu 11.04 on my laptop for a grand total of seven days now, so i am an incredible newbie.

I have created an almost seamless dual-boot between Windows7 and ubuntu, and the only link missing in the chain is the ability to reboot directly from Windows7 desktop to ubuntu.

My intention is to run a remote pc using vnc servers in both OSes, so that I can press the start button in the morning and walk out the door able to access both all day, but i need to find some way to return to ubuntu from windows.

First some background, I am running Grub2 straightforward, and windows has no way to access my config files natively, and i did not have to forsight to format my ubuntu drive to ext3 inode size 128, so ext2ifs is out.

I have my boot default set to Windows so all i need to do is restart normally from ubuntu and boot correctly, but I am really stuck on this guys......

and just to save time
1. Yes i have explored extensively on FAQs and other post (for about 6 hours now)
2. I do not know where this thread really should go, so if you want to move it please do
3. I am a fast learner, but terminal is still a little new to me, so please be patient  :D
[/SIZE][/SIZE]

---

### Post by garvinrick4 on 2011-07-30
##I experimented with Vmware player (free software) with Windows 7 64 bit as host and ubuntu 11.04 classic 32 bit as guest. (64 bit does not install) Can open both Ubuntu and
Windows at same time using the VMware. Can actually install how many linux installs you want as long as you have enought Ram to run them all together. Or you can run just one linux and Windows with multiple installs if you choose. (less Ram needed) Do not know if
your if you can run your remote access for both but worth checking into.
## Do no that you can only access the partition you have booted in dual, triple, quad or however many installs you have. Each partition is like its own HDD so will never be able to
access one that is not booted.

---

### Post by cjack2964 on 2011-07-30
Thank you for the quick response, I am aware that I could run VMware, but I am really looking for a more integrated solution, if I'm already going to use a vnc client to login, then using a virtual machine seems like a clunky solution.

Also, I would be able to access the ubuntu hard drive, and all others from windows if I was able to mount ext3 file systems, but thanks to my poor foresight, I just can't lol.....I should probably add though that I have one partition, about 9gb, that is in correct format to use ext2ifs for windows.

Thanks again :)

---

### Post by garvinrick4 on 2011-07-30
Run Ubuntu and mount all partitions in /mnt
sudo mkdir /mnt/windows
sudo mkdir /mnt/lucid
sudo mkdir /mnt/temp
sudo mkdir /mnt/natty
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt/windows
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt/lucid
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt/temp
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt/natty
[COLOR=Red]x[/COLOR] being drive and [COLOR=Red]y[/COLOR] being partition number
##Go to files system and open /mnt all will be mounted in there directorys.

sudo umount /mnt/windows
sudo umount /mnt/lucid
above to unmount of course.

##Is this what you want to mount all at once in one install and be able to access.

---

### Post by cjack2964 on 2011-07-30
No, what I want is some stable method to reboot into ubuntu from windows 7 with Grub2 as my boot loader.

I only bring up the partition issue because it means that I am unable to make changes to the grub configuration file from Win7, which is a hinderance

---

