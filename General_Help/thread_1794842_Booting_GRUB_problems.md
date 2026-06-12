---
title: "Booting GRUB problems"
date: 2011-07-01
forum: General Help
---

### Post by jan-90 on 2011-07-01
Hi,
i just installed ubuntu on a separate hard disk from my windows 7. however GRUB replaced my windows 7 bootloader despite being on a separate HDD. I do not what this since if i delete the linux partitions it will mess up my windows partition too.  Plus my usb keyboard does not work in the GRUB screen (it does in bios) and makes booting to windows impossibile.
Can i use EasyBCD to create a windows bootloader on the windows HDD? if yes how should i proceed?
thanks

---

### Post by ahears on 2011-07-01
[COLOR=Black]The keyboard:

[/COLOR] [COLOR=Black]Make sure your bios settings for the USB keyboard are set to 'enable' anything else will shut down the USB port after bios exits, leaving Linux to install driver on boot-up.
[/COLOR][COLOR=Red][COLOR=Black][/COLOR][/COLOR][COLOR=Red]
[/COLOR]

---

### Post by oldfred on 2011-07-01
You first want to install grub2's boot loader to your Ubuntu drive (probably sdb). And you want to reset where grub reinstalls on updates. Set BIOS to boot from sda, then fix windows to boot from sda. You may also need fixMBR or run the auto repair 3 times. The switch BIOS back to sdb and grub will boot and its menu will give you a choice of Ubuntu or windows.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by jan-90 on 2011-07-01
> **ahears said:**
> [COLOR=Black]The keyboard:

[/COLOR] [COLOR=Black]Make sure your bios settings for the USB keyboard are set to 'enable' anything else will shut down the USB port after bios exits, leaving Linux to install driver on boot-up.

[/COLOR][COLOR=Red][COLOR=Black]Now that you have fixed the keyboard you may _not_ need the following:[/COLOR]

To get the windows boot-loader back, run the windows  setup cd and choose to recover: Then when you get to the recovery  console enter:[/COLOR]

[COLOR=Red]
[/COLOR]

thats a problem i could not solve. i have looked in vain for the setting but its nowhere to be found. it might be due to the old bios version i am running? (the mobo is an abit ip35pro)

---

### Post by jan-90 on 2011-07-01
> **oldfred said:**
> You first want to install grub2's boot loader to your Ubuntu drive (probably sdb). And you want to reset where grub reinstalls on updates. Set BIOS to boot from sda, then fix windows to boot from sda. You may also need fixMBR or run the auto repair 3 times....

I installed easybcd and added a win 7 and linux to booting it did not replace grub however. i now have 2 post screens asking for the options.
but if i take out the linux hard disk the windows cannot boot.
does your method solve this please
thanks

---

### Post by oldfred on 2011-07-01
If you do not replace grub in the MBR of sdb you may not be able to boot Ubuntu without having to use a liveCD to reinstall grub to sdb. then having  a windows boot loader in sda will take you to windows. If you have EasyBCD in windows it works as another dual boot, but I do not know how it boots Ubuntu.

Not sure about easyBCD. You should only get one menu from easy, but would get a second from grub?

---

### Post by jan-90 on 2011-07-01
i manage to partially fix it. I restored via easuBCD i now have the windows bootloader first that leads to the GRUB so the default is win 7 (i use that mainly)

However booting the windows disk is still not functional, GRUB booting for windows is on sdb

so i still have to boot the windows bootloader on the windows drive (sdb) the linux bootloader is ok u just need to change the waiting time before selection.

any idea how i can creat a bootloader on the windows partition, easyBCD only overwrites the current bootloader on the other drive (sda)

---

### Post by ahears on 2011-07-01
> **jan-90 said:**
> i manage to partially fix it. I restored via easuBCD i now have the windows bootloader first that leads to the GRUB so the default is win 7 (i use that mainly)

However booting the windows disk is still not functional, GRUB booting for windows is on sdb

so i still have to boot the windows bootloader on the windows drive (sdb) the linux bootloader is ok u just need to change the waiting time before selection.

any idea how i can creat a bootloader on the windows partition, easyBCD only overwrites the current bootloader on the other drive (sda)

Sounds like a mess. Get rid of the easybcd its third party and is making things more difficult. You may need to restore your windows loader using the install cd to recover on the appropriate partition, *then* the ubuntu live cd to recover and install the grub on the first partition of the first drive, in that order. Oldfred or I can help but stop what you are doing because its making it harder for us to help. Are you satisfied with the keyboard issue? If not then setting you up with a dual boot is useless because you will not be able to choose what to boot. That being said, you are going to have to switch keyboards first. Then follow the steps oldfred gave you to get started. If you can't get into Ubuntu let us know.

---

### Post by oldfred on 2011-07-01
I think we have posted what you need, but I am losing track of what is where. If you need more help post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.
Links in post #9 now do not work.

---

### Post by jan-90 on 2011-07-02
If will run the windows recovery (with the ubuntu drive unplugged) and after  delete the ubuntu partitions and have a fresh reinstall. Windows booting should work off the windows hdd


Then i install ubuntu with the windows hdd removed i can then get to boot from ubuntu or windows by switching my hard disk boot priority.
do you think this makes sense?
thanks

---

### Post by oldfred on 2011-07-02
You can switch boot priority and boot either drive, but you do not have to. Be sure to keep windows as sda or first drive. It does not like drive changes. Ubuntu/grub2 uses drive but also then does a search by UUID, so it will find the correct partition to boot even if drive has changed.

If after you have installed to separate drives you plug both in and run this you can boot  Ubuntu or winodws when you boot the Ubuntu drive.
```

sudo update-grub
```

---

### Post by jan-90 on 2011-07-02
thanks both for your help. the boot loader is now on the windows partition and i can use ireboot to go into ubuntu. hopefully i will try to solve the usb keyboard problem when the abit sites comes back online (if it does at all its been more than a week).
later on i will try to put a MBR on the linux drive to make it bootable without ireboot

thanks alot guys

---

### Post by jan-90 on 2011-07-03
follow up: i reinstalled ubuntu with the windows drive removed and now can boot from both drives.

---

