---
title: "Tripple boot"
date: 2006-06-03
forum: General Help
---

### Post by livingword26 on 2006-06-03
I am currently running a dual boot using Windows XP and Ubuntu 6.06. Is there a way to run a tripple or quadruple boot system? Can they all be controlled by the same grub somehow? If I install a new distro but do not install a new grup, will the existing one recognize it and put it on the option list when I first start my computer?

---

### Post by kingmonkey on 2006-06-03
You can multi-boot many OS using Grub.

Hopefully the new distro will recognise that grub is installed and update it to include itself in it.

---

### Post by Rui Pais on 2006-06-03
hi,
grub is independent of linux. As long as you have it on is own partition you can use it to boot any systems you want (at list any linux, window or *bsd...).

if you not make a separated one you have to mount ubuntu partition to launch it and the another distro, not an ideal solution... in that case is better reinstall grub, or just make a small partition (ext2 is more then enough) and cp -a all files on your /boot to there.

Then just change /etc/fstab to point to the new partition and change menu.lst of grub making new entry pointing the new distro or let the installer of the distro do that for you.

I have a debian, 2 gentoos, 3 ubuntus and a windows in my computer. :)
My grub was installed with one of the gentoos...

---

### Post by rgsproductions on 2006-07-13
Sorry if this is a dumb question. Irun xp and ubuntu 6.06 and the same drive.  If I install another linux on a second drive, lets say another ubuntu, then can you keep it from installing grub and making the first already installed grub see it.  I read that if you install to a second drive , to install its boot loader to that drive and point the main drive boot loader to the third os.  I to would like to have a third to trash and learn from instead of killing my main linux os.

---

### Post by Herman on 2006-07-13
> Sorry if this is a dumb question. Irun xp and ubuntu 6.06 and the same drive. If I install another linux on a second drive, lets say another ubuntu, then can you keep it from installing grub and making the first already installed grub see it.It's not a dumb question at all. If you install with the Ubuntu 'Alternate' Install CD you can [install GRUB to a floppy disk]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") and then reboot from the floppy disk temporarily to complete the installation.
Then you can either continue to boot your experimental Ubuntu system from the floppy disk or add the right commands to your regular Ubuntu Dapper's /boot/grub.menu.lst file. Then it will give you the option for booting your new experimental system each time you boot up.

a suitable operating system entry you might add to your /boot/grub/menu.lst might be one similar to this, (but not exaclty the same),
>               title        Ubuntu, kernel 2.6.15-25-386
             root        (hd1,0)
             kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 
             initrd        /boot/initrd.img-2.6.15-25-386
             savedefault
             boot

 You will need to replace the name for the kernel I gave in this example with the real name for your actual kernel in your new install, and the same with the name of your initrd.img
I hope I guessed the partition numbers correctly for you, but you might need to check those also.

One way to find out the right kernel and initrd.img filenames is to try using GRUB's Command Line to investigate your computer for you. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to see how to do that.
If that seems too difficult for you, just boot it with the floppy disk and take a look at what the kernel and initrd filenames are and note them down on a piece of paper and add them to your /boot/grub/menu.lst when you boot your regular install of Ubuntu.

Another way is to just let the installer install grub to MBR (rather than to floppy disk) again like normal (you can use the 'Desktop' Live/Install CD), and after the install is done, reinstall GRUB from a GRUB shell, using (hd0,1) as the root filesytem if that's your regular Ubuntu installation. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") to see what I mean. Then I think you will still need to add your other system to your grub menu though.

Yet another way is to install GRUB or Lilo (using the 'Alternate' CD), to the first sector of your new experimental install's partition and use [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") to boot it from a floppy disk or CD.

I hope this will be enough to give you some ideas, please don't hesitate to ask any questions if I didn't explain anything well enough. It might be a few hours before I can reply though, I need some sleep, Regards, Herman :D

---

### Post by rgsproductions on 2006-07-13
Thank you, I have seen that web page and now it makes more sence.  I will try the tripple deal this week end.


Thanks again   :D

---

### Post by Rui Pais on 2006-07-14
Hi,
sorry but why install again grub on 2nd hd?

You can simply install an OS there, skip the bootloader install section and add an entry to your actual menu.lst, using (hd1,XX).
No need to add any grub part to that hd, neither on its mbr or any partition... 

In fact you you want to duplicate installed ubuntu to make test and experimental things you can use cp -a command to do it easier.

Just make a partition on 2nd hd using gparted or qparted, then boot from a livecd, mount your actual Ubuntu and the knew partition, and do (partition number here are just for the example, adjust to yours):
```
sudo cp -a /mnt/hda2/* /mnt/hdb1/
```
and then edit /mnt/hdb1/etc/fstab and replace the line with
> /dev/hda2    /  (...)
with
> /dev/hdb1    /  (...)
and you have full functional copy of your actual ubuntu with all your prefences and personal settings preserved:)

Then just edit the menu.lst and duplicate the entry for normal ubuntu replacing
> root (hd0,1)
kernel /boot/vmlinuz-2.6.1x-xx-xxx root=/dev/hda2 
with
> root (hd1,0)
kernel /boot/vmlinuz-2.6.1x-xx-xxx root=/dev/hdb1 

Again, the partition numbers and kernel names must be according to your box scheme (if you decide to do it that way).

It's easy and absolutly safe (it wont touch your actual ubuntu or MBRs)

---

### Post by Herman on 2006-07-14
Rui Pais, :-D  Hey! I like that cp -a method for copying an enitre operating system! I will try that out, that looks like a great idea. :D
Is it necessary to edit /etc/fstab to suit the new partition numbers though?
Thank you for sharing that,  :D
You are the champion, regards, Herman

---

### Post by Rui Pais on 2006-07-14
> **Herman said:**
> Rui Pais, :-D  Hey! I like that cp -a method for copying an enitre operating system! I will try that out, that looks like a great idea. :D
Is it necessary to edit /etc/fstab to suit the new partition numbers though?
Thank you for sharing that,  :D
You are the champion, regards, Herman

Hi,
yes cp -a (-a stands for archive, preserves permitions and ownerships of files) is one of my beloved features on Linux. 
It's so easy and the only detail that requires special careful is not doing it copying a live OS (autocopy the system from where it runs, i mean)

I always do 2 copies of my working OS, one stays cool and quite on a partition on the end of a disconnect small hd (reserved for backups) and the other for the crazy things and tests. 
Why play with fire? ;)

Glad you like it!

---

### Post by Herman on 2006-07-14
Yes, I like that very much! You are the only person besides myself that I know of who makes a backup of the operating system and all installed software and settings to another small partition somewhere.
I back up my data seperately. 
The method I was using until now was to resize the partition first to a very small size, and then copy and paste it to the end of my disk with Gparted.
With your method I will not need to resize the partition first, I can cp -a from a larger partition to a smaller partition or the opposite to restore if needed. It should be easier and faster. I will give it a try soon.
I too like to be free to try out crazy experiments without being afraid of losing  all my progess so far. :D All the best, Regards, Herman

---

### Post by andyp11 on 2006-07-14
I do that as well. I suppose most linux users are compulsive fiddlers and it's a 5 minute clean slate when we screw up badly. I've used it for win98 back ups for years, some disk manager prog I think,although in linux you don't need to swap HD cables etc. of course.

By the way I use rsych rather than cp. such as

sudo rsync -aS /media/hda7/. /media/hda10/.

Anyone know the difference?

---

### Post by rgsproductions on 2006-07-15
I finally got it to work with the cp -a.  I had a problem mounting the partitions.  In the menu list file, I added the new information after my windows selection.  Does this make a difference?  When I had the entry as the last ubuntu selection, grub gave an error 17.  But all is well and I am going to trash my new experimental drive.  And to think, I just bought acronis back up for my other system, It will move and restore linux partitions, but this way is much faster.  

Thank you all for your help. Because of Ubuntu, I am 99.99% away from killing xp.

---

### Post by Rui Pais on 2006-07-15
Hi,
> **Herman said:**
> Yes, I like that very much! You are the only person besides myself that I know of who makes a backup of the operating system and all installed software and settings to another small partition somewhere.
Yes, i always find thats so strange... a friend of mine have to had is pirate copy of W2K delete half of his master thesis after a crash to decided to to start make backups at least of his personal work. People are funny when it came to secure they work (and consequently they time...)

[QUOTE=andyp11]By the way I use rsych rather than cp. such as
sudo rsync -aS /media/hda7/. /media/hda10/.
Anyone know the difference?[/QUOTE]
If i remember well from read it somewhere else, the only diference beteween cp and rsync is that rsync allow to resume the copy process if it has been stoped foe any reason. So eventually is even better. 
I'm so conservative when it cames to try new things when i have something that work so well and without a problem, that i, shameless :oops:, never tried.

[QUOTE=rgsproductions]	I finally got it to work with the cp -a. I had a problem mounting the partitions. In the menu list file, I added the new information after my windows selection. Does this make a difference? When I had the entry as the last ubuntu selection, grub gave an error 17. But all is well and I am going to trash my new experimental drive.[/QUOTE]
The position of grub entrys are absolutely at your taste. No  problem there. Use line "default=<N>" to set the defualt OS.

Check carefully your partition numbering and the new entrys, it so easy one make mistakes here (grub has a bad numeration scheme :() Don't forget that you need to check 2 points, root entry (should point to your /boot partition in grub notation) and kernel entry (point to the linux path to your kernel location).

If that not helps post more info on your partitions scheme and your menu.lst.

---

### Post by Herman on 2006-07-15
> I added the new information after my windows selection. Does this make a difference? When I had the entry as the last ubuntu selection, grub gave an error 17. That's strange, are you sure there wasn't a little typo there at the time?
Normally other Ubuntu's and Kubuntu's in my menu.lst experiences get added under the main Ubuntu system entries in the automagic kernels list.
Whether they actually get updated automagically, I'm not too sure, but I doubt it.  Well, as long as it works. I guess that's okay. Enjoy! :D
Regards, Herman :D

---

### Post by rgsproductions on 2006-07-15
I was originally off on mounting the drives.  When everyting coppied, I changed where I placed the commands on the menu list.  This is an old troubleshooting nightmare when you change more than one thing and your not sure what fixed it.  I have acronis because I learned the hard way with xp and do backups very often when changing or updating.  This forum has helped alot in that I am not worried of crashing linux.  

Thanks again.

---

### Post by Rui Pais on 2006-07-15
Hi **rgsproductions**,
just 2 more things. 

My sugestion on post [#7]("http://ubuntuforums.org/showpost.php?p=1254348&postcount=7") was made with assumption that you don't have a separated /boot partition. 
If you *do have* a separate partition for boot then you shouldn't add (as i said) (hd0,x) -> (hd1,x), but leave it as it is for the entry of the "main" ubuntu.
Don't forget too, that you need to edit /etc/fstab of your copied OS.

The key 'E' on your keyboard, if pressed during boot  will allow you to edit (not permanetly) the menu-lst entrys. It can do tab completion, too (ex: (hd0,1)/{TAB} will show whats in /dev/hda2/). 
Those can be very handy when it came to catch grub errors specially those related to mount points.

hope that helps.

---

### Post by rgsproductions on 2006-07-15
Here is what my menu selections look like.  The first time, I could see the files on the partition but grub stated it was an unknown file system.  The second time , I reformated the partition, remounted the drives and with the live cd and it worked.  So it was something I did in the setup.  Works great.

Working copy:

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

Back up copy:

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

---

