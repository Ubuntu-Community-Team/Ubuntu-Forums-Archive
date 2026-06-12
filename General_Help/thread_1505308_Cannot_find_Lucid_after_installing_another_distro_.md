---
title: "Cannot find Lucid after installing another distro - Mandriva"
date: 2010-06-09
forum: General Help
---

### Post by rajn on 2010-06-09
Hi,
I am a relatively new user, using Lucid for the last one month and I had partitioned the disk manually into /boot, /home, /usr, etc...i.e., in 9 partitions. I was enjoying using Lucid however, there were problems with uncertain hangups, screen freezes but on the whole I was able to work. 

I decided (because I had extra space) to install Mandriva. During installation it asked me the choice and I marked the choice which said "use available space". And then Mandriva got uploaded and it works fine.
I would though love to get back to Lucid as I have grown quite fond of it and also familiar.

However, now when I boot I do not get the old boot options which were the Linux 2.6.32 kernels.
I do not see them at all. The boot menu just shows
linux(/boot/vmlinuz)
failsafe option for the above
desktop586 2.6.31.5-1 mnb
desktop586 2.6.31.5-13 mnb

This is the output from - "mount"

/dev/sda11 on / type ext4 (rw)
none on /proc type proc (rw)
/dev/sda13 on /home type ext4 (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
gvfs-fuse-daemon on /home/xygujju/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xygujju)

I really do not know what it means

And this is the output from fdisk -l.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         244     1951744   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             244         851     4882432   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3             851        1459     4882432   83  Linux
/dev/sda4            1459        9729    66429562+   5  Extended
/dev/sda5            1459        1520      487424   83  Linux
/dev/sda6            1520        2128     4881408   83  Linux
/dev/sda7            2128        2371     1951744   83  Linux
/dev/sda8            2371        2614     1951744   83  Linux
/dev/sda9            2614        3222     4881408   83  Linux
/dev/sda10           3222        3465     1951744   82  Linux swap / Solaris
/dev/sda11           3466        5032    12586896   83  Linux
/dev/sda12           5033        5541     4088511   82  Linux swap / Solaris
/dev/sda13           5542        9729    33640078+  83  Linux

I do know that I had started during Lucid installation on a clean disc with /boot followed by /root, /home, /tmp, /usr, /usr/local, and finally /var. The Boot device shows /dev/sda/ (ATA WDC WD800BEVE-00) and also dev/fd0 (H1440) and then it shows all the rest of /dev/sda*. I do not understand what the first two mean.
When I try to add additional entries I have the option to choose a root partition but it asks for image?

I tried using partition manager on Mandriva but cannot follow it much. It shows all the partitions i.e., partition 1 is at the beginning which I had named as /boot for Lucid. I see it at the left extreme side of the bar. I recognize it by the size ~2Gb I had allocated to it. But I do not see any associations.Then the rest follows and then I see a swap after which /root for Mandriva and then a swap space and then /home.

I do not understand how to enable booting into distro of my choice. Do I have to reinstall? I read some tutorial on Grub and it said I should do "find grub stage 1" and it should give me all the stage 1 for each distro. 
However, I only see one. Do not see the other.And then something about MBR. What is that and where do I find it?

Any help is appreciated.
Please help.

---

### Post by amite on 2010-06-09
i am fairly new to linux too..........
if after installing another distro if u  r not find any of the distro already installed on ur system then it may be due to grub is not detecting it,so give it a try it should work as it worked in my case...
$sudo grub-update

---

### Post by john newbuntu on 2010-06-09
From your description, it appears that /dev/sda11, sda12 and sda13 are Mandriva partitions and the rest are Ubuntu's.  Mandriva uses legacy grub and Lucid uses grub2 as the default bootloaders. In your situation, it looks like you installed Mandriva's bootloader to the MBR, which is why you are getting its boot menu.  In doing so, you have replaced the portion of grub2 that was in the MBR.

You could do any of the following to dual boot these OSs:
1. Fix grub2 first using an Ubuntu liveCD by reinstalling grub to the MBR.    See section #13 in the following post by drs305 to fix this:  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Then run "sudo update-grub".  Reboot and check. If you still are not able to see mandriva, try adding this stanza to /etc/grub.d/40_custom file in Lucid
```
menuentry "Mandriva" {
   insmod ext2
   set root='(hd0,11)'
   linux (hd0,11)/boot/vmlinuz
   initrd (hd0,11)/boot/initrd.img
}

```followed by "sudo update-grub".  Reboot and check.

2. Chainload to grub2 from grub which involves installing grub2 to /dev/sda1 and then changing menu.lst on mandriva's side to chainload to Ubuntu.

---

### Post by rajn on 2010-06-10
Thank you john newbuntu. I appreciate you pointing out the possible solutions. That was really helpful, however, I am still not there.
Here is an update. Hopefully, I will solicit more suggestions.

I updated the grub after doing grub-install from a live CD.
The problem was after rebooting, I was launched directly into grub shell i.e.,

sh grub>



sh grub>** ls**

It shows me exactly what fdisk -l shows and is same as what I posted earlier. There is an asterix in sda1 and it shows it is a boot sector.

sh grub> **set root=(hd0,1)**

sh grub>** linux **
no files found.

I did this for all sectors i.e., hd0, * where *goes from 1 to 10 and 

found no linux kernels.

Then 
sh grub> **set root=(hd0,11)**
sh grub> **linux /vmlinuz root=/dev/sda11 ro**....command taken from "Ubuntu help on grub"

gave some output which looked like an address in Hex. Looks like it found the vmlinux.

sh grub> **initrd /initrd.img**
no file found

sh grub>boot

Now it booted without launching me into the grub shell but hung up midway with some error (do not exactly remember) but the computer hung with Cap and Scroll 
lock lights flashing. No cntrl-alt-del worked. Had to shut down. On rebooting I am back to

sh grub>

I realize the following: Sector sda11 is where Mandriva's root exists. Wonder why it did not boot into Mandriva which worked all along.


when doing grub-install with a live CD i used

$** sudo mount /dev/sda1/ /mnt**

$ **grub-install --root-directory=/mnt** **/dev/sda**

no errors

$**sudo umount /mnt**

and then I realized that when I had installed Ubuntu Lucid, the /root and the /boot were partitioned as sda2 and sda1 respectively.But when I do 

$ **sudo mount /dev/sda1/ /mnt/boot**
gives me an error..not found


The command "**grub-install --root-directory=/mnt  /dev/sda/ **" -> Doesn't this assume that --root-directory is same as the boot? I do not understand this command. Can someone help?


Maybe that is why the kernels are not being found.
Any suggestion folks? 

I will try for another couple of rounds. What the heck, I am learning and is fun. Though I am tempted to reinstall everything again. But now if I have to install 
two distros - Lucid followed by Mandriva, can someone suggest me a best way to do this or point to a tutorial or a site?

---

### Post by dnguyen1963 on 2010-06-10
Try updating Grub first as suggested in this thread.  If you are going to do fresh re-install of the two systems, I suggest that you install Mandriva first follow by Lucid.  Ubuntu is better at recognizing other existing OS and upgrade Grub accordingly.

---

### Post by rajn on 2010-06-10
:p Thank you all,
This problem got solved. 
As I mentioned earlier - I had not properly understood the grub commands suggested in the link for grub-install. I was doing it wrong.

when doing grub-install with a live CD i had used

$** sudo mount /dev/sda1/ /mnt**
$ **grub-install --root-directory=/mnt** **/dev/sda**
 $**sudo umount /mnt**
All this above is INCORRECT because

I had manually partitioned during Lucid install such that 
sda1 - boot
sda2 - root

Therefore after rebooting with live CD here are the commands I used now:

[B]$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /mnt/boot
[/B]After this ran ok without errors[B]
$sudo umount /mnt/boot
$sudo umount /mnt
$reboot[/B]

On rebooting I could see all i.e., all Lucid kernels and the Mandriva kernels in the grub menu. 
I booted into Lucid and as expected opened with a blank purple screen and to get the menu had to use
"killall gnome-panel" (B.T.W I had started a thread on this and haven't yet found a solution as to why this happens but I should not digress). Next 

**$ sudo update-grub**

Then, I decided to boot into Mandriva. Rebooted and in the grub menu selected the Linux choice.
Unfortunately, this and other choices corresponding to Mandriva did not work and hung the computer with this message:

"
[I]VFS: Cannot open root device "UUID = ###......" or unknown -block (0,0)
Please append a correct "root=" boot option; here are the available partitions
kernel panic - not syncing : VFS: Unable to mount root fs on unknown -block(0,0)
Pid: 1; comm: swapper Not tainted 2.6.31.5-desktop 586 -lmnb #1

Call Trace: 
....
<###> kernel-thread-helper +0x7 /0x/0[/I]
                                                               "
This was accompanied by Cap and Scroll LED lights blinking until I had to force a manual shutdown.

Then for a possible resolution, I followed the suggestion of john newbuntu and changed the grub.d/40_custom, exactly as he had suggested.
updated grub and then rebooted.
On rebooting saw an additional kernel which was named just plain "Mandriva"
Selected it and booted into a working Mandriva.
Feeling quite thrilled!! 

Thank you all.

Some questions (If I can get answers to some it would be icing on the cake):

1. All that italicized message: is that something serious I should worry about?
2. What should I do to those Mandriva kernels which boot up with the system hang? Can I remove them from grub menu and how? Or should I just leave them and somehow hope that other users do not boot from them by mistake
3.In my earlier attempts which I posted here, I had done grub-install in the same /mnt not realizing that my boot and root partitions were different. Did that screw up something causing the above message?
4. If so how do I correct it?

---

### Post by john newbuntu on 2010-06-11
Glad you got it to work.  
1. To be honest I do not know why you got that message.  My  guesses are that the UUID in the kernel is wrong or that the initramfs is missing a few required modules.  Somebody else can shed more light on this.  You might want to post a copy of your grub.cfg and the output of "sudo blkid -c /dev/null" to help us out.  If you require a cleanup, you could take off the execution bit on the 30_os-prober until things are sorted out and run 'sudo update-grub'

2. For now, leave them the way they are.  But once you figure the solution to problem 1, it would all work automatically or you could go into Mandriva and remove the older kernels.

3. It should not have done anything bad hopefully since you are able to boot and work in Ubuntu.  The command looks for a /boot directory for grub installation and would not have found it. I am surprised it did not complain or perhaps it created a /boot directory(you might want to check it).

---

### Post by oldfred on 2010-06-11
The osprober in grub2 finds mandriva but the kernel and init lines
linux (hd0,11)/boot/vmlinuz

Have that (hdX,Y) for drive & partition as part of the kernel & init. Grub2 copies those as it is part of those lines, but it is old grub not grub2 so the partitions are off by 1. You have to copy the mandriva entry to 40_custom and edit the partition number. Actually it is better just to remove it as it is not required. The set root = is all that is required. You then turn off osprober so you do not have duplicate entries. You can turn it on again if you install something and want it to find an entry for you.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

---

### Post by john newbuntu on 2010-06-11
Thanks for chipping in oldfred.  Yeah, I wish grub2 was smart enough to deduce the drives and partitions from legacy grub automatically.  This way, just an update-grub would have done the job.  But perhaps they are not backward compatible.

---

### Post by garvinrick4 on 2010-06-11
Once you get your grub2 into sda, which is not that hard. Once you boot into the ubuntu OS you give it a.

```
sudo update-grub
``````
sudo grub-mkconfig

```It is easier for me to label my partitions such as "lucid" or "maverick" or "fedora" whatever is easiest to remember for each.

So lets say I have lucid label in sda5. Take a Live CD or Live USB.

```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda5 /media/lucid
```                          ```
sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda")
```Now you have grub2 in sda. Shutdown and remove Live CD. Boot into sda5 and run.
```
sudo update-grub
```  (updates grub menu)
```
sudo grub-mkconfig
```  (new config file with every install in its order using grub2)

If you install a Linux OS in you machine and its got grub legacy lets say and you install it
in sda you need to just go to live CD right away and reinstall grub2 right off the bat. Just need your sda # and label of ubuntu install.

```
sudo blkid 
```(small L second letter)

[GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")

---

### Post by rajn on 2010-06-11
> **oldfred said:**
> The osprober in grub2 finds mandriva but the kernel and init lines
linux (hd0,11)/boot/vmlinuz

but it is old grub not grub2 so the partitions are off by 1. You have to copy the mandriva entry to 40_custom and edit the partition number. Actually it is better just to remove it as it is not required. The set root = is all that is required. You then turn off osprober so you do not have duplicate entries. You can turn it on again if you install something and want it to find an entry for you.


In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Thanks once again,

That did it for me. I worked out the solution as you suggested. 

First noticed that in /boot/grub.cfg in the section relating to 30_osprober the sector was off by 1 i.e., it showed (hd0,10) instead of (hd0,11).
I am still not clear why is that happening..
Therefore, copy pasted the entire 30_os-prober section and pasted it onto 40_custom file and corrected the partition number.
Then in etc/default/grub added 
GRUB_DISABLE_OS_PROBER=true     
followed by 
update-grub
 
rebooted into grub menu and I could see all the kernels and the init lines. This time I purposely opted to boot from a kernel which had resulted in a system hang earlier. But now with the above changes it worked like a charm. Haaaapy! 
I have now set root= because I do not need those extra Mandriva kernels and retained only one. 

So a big thank you again for a good dose of grub fundamentals from everyone on this post.

---

