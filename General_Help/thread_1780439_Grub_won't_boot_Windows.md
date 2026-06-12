---
title: "Grub won't boot Windows"
date: 2011-06-12
forum: General Help
---

### Post by mpl34 on 2011-06-12
So after completely giving up on linux for a year... after problems with installing grub, i reluctantly decided to give it another shot.

So I installed a new copy of kubuntu, everything worked correctly except one problem arised with my windows partition. When i try to boot windows through grub, it simply directs me back to the grub boot menu. I can boot kunbuntu fine.

I have tried recovering startup issues by using a windows 7 disc and also run bootrec.exe. I had no problems running the command /FixMbr however /FixBoot has issues....

My partitions are as follows
/dev/sda1      fat16 boot     47 MB
/dev/sda2      extended      149 GB
    /dev/sda5  ntfs Windows  109 GB
    /dev/sda6  Linux-Swap    1.7 GB
    /dev/sda7  ext3 Linux     40 GB


I think the problem is that grub has overwritten windows boot files so everytime i try boot windows it reverts me to grub in a sort of loop.

If anyone could please provide help it would be much appreciated.

---

### Post by garvinrick4 on 2011-06-12
How did windows get into a logical partition sda5?

---

### Post by linuxinstalledfromhdd on 2011-06-12
LOL :popcorn:

They are pulling your leg man.

---

### Post by garvinrick4 on 2011-06-12
If you download this script to your desktop and then run the code below it will
put a results text file on your desktop post it here and you will get help.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
  sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by mpl34 on 2011-06-12
I have attached the results

---

### Post by garvinrick4 on 2011-06-12
Looks like Ubuntu grub was installed in sda1 instead of sda
Windows sda5 has no boot files in it.
sda1 is Dell utility not a boot partition.
Do not usually see Windows install in a logical partition sda5 likes primary sda1, sda2,sda3 or sda4
Put in the Ubuntu Live cd and choose try Ubuntu and with internet working do this.
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR
Now reboot into Windows.
Put install CD back in and Choose try ubuntu and do this in a terminal.
```
sudo mount /dev/sda7 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Now choose ubuntu and go into ubuntu and open a terminal and:
```
sudo update-grub
```Let us know.

---

### Post by mpl34 on 2011-06-12
I could not reboot into windows after...

> Code:
sudo apt-get install liloCode:
sudo lilo -M /dev/sda mbrMay show error messages about the rest of lilo missing, ignore, we just want MBR
Now reboot into Windows.


I followed the rest of the instructions now when i turn on my pc i get the message 
> error file missing
Grub_rescue
in a command prompt.

---

### Post by garvinrick4 on 2011-06-12
In a live Cd just copy and paste these so you get grub2 back in sda for sure.
                                 ```

sudo mount /dev/sda7 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
sudo chroot /mnt
grub-install /dev/sda
update-grub
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
sudo umount /mnt
sudo reboot

```

---

### Post by mpl34 on 2011-06-12
I have done exactly what you said, but i still have the same problem. I currently have to boot off live

---

### Post by garvinrick4 on 2011-06-12
What is your bootscript look like now, before it had no Linux boot loader just windows in the mbr. Do another one. Grub2 has to be in the mbr of sda. Will stick around for it.

## Did it say when you installed grub that it installed fine.

---

### Post by mpl34 on 2011-06-12
Is this the boot script you were after? I have run the test off a live boot.

---

### Post by garvinrick4 on 2011-06-12
Now you show grub2 in the mbr of sda but there is nothing showing in sda7 (Ubuntu at all)
I believe sda5 was mounted on live cd at time of running your script. It is a mess, sda1 has boot files that are not suppose to be there. sda5 windows has no boot files at all. Now sda7
Ubuntu has a UUID but showing nothing to read in partition right now. And now there is 
a sdb drive showing had something was attempted there at one time. It is getting worse
as you go. Were you mounting drives in the live Cd or the Usb and attempting or getting your files off of? Do you have your Windows disks? You must it was installed in sda5 at one time or another and does not come like that. 
To tell you the truth I would just install Windows on whole disk and then install Ubuntu and
choose to install side by side and just be done with it. I mean your drive is a real mess and just
needs to be fixed up the right way. That would put Windows in sda1 and Ubuntu in sda5 and swap in sda6 like it is meant to be. 
I am sorry but things have happened and are happening that just are not normal.
When you installed grub it should have said all went well or there was a problem. When
you did update-grub should have run so you could see. Something is going on that I do not
know about. This will bump up to the front of Forum maybe someone else will think there
is a salution to this script.

---

### Post by mpl34 on 2011-06-12
Thanks for the help...

Is it then possible to reinstall windows over my old copy to keep all my programs and data whilst moving the install to sda1

---

### Post by garvinrick4 on 2011-06-12
No, you must back anything up that you have. In live cd I believe you had sda5 your windows 
mounted at the time you ran boot script so should be able to get your personals if you mount
again and retrieve them. But both installs will have to be fresh. Should not take all that long.
I really think you will be much happier with a drive that is ship shape instead of helterskelter.
Good luck to you and have a nice day.

---

### Post by Neoxhadowespio on 2011-06-12
I'm having my own boot problems, but one suggestion.
You sound like your one of those people who know what they are doing. Don't give up on Linux, try Gnome. KDE isn't very stable. Once you are set to go, most people like you would have no trouble at all.

---

