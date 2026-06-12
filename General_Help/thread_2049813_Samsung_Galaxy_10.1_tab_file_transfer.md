---
title: "Samsung Galaxy 10.1 tab file transfer"
date: 2012-08-29
forum: General Help
---

### Post by candtalan on 2012-08-29
Want to transfer files from the tablet  via usb to the Ubuntu PC. Problem.

Using ubuntu 12.04 currently fully updated.

Galaxy tab 10.1 model No GT-P7510
Android version 3.1
kernel versiion 2.6.36.3 se.infra@SEI-29 #1
build number HMJ37.XXJG8 P7510XXKG8

Using a Samsung branded connector cable from the tablet to a USB socket on my Ubuntu PC. This is not the charging cable.

Very quickly after the usb is plugged in, the tablet bleeps and indicates
'USB connected MTP-connected'

Also the ubuntu display appears and shows the tablet folders mounted, with folders shown (screenshot)

However, the contents of the folders does not appear, they show as (empty) (screenshot)

However, a file already downloaded in the tablet I think via email is indicated ok, for example (Exhibitor Questionnaire Retirement Fair 2012.docx) (screenshot)

So it looks as if the tablet file system is mounted  but  the folder contents - at  least - are not being displayed (??) I wonder if it is a permissions problem of some sort?

The Nautilus display (of the tablet contents) will allow a new folder to be created and this folder does get onto the tablet. At this stage the new folder is seen on both in nautilus and on the tablet (App 'my files') however on subsequent connections, it is not then shown on nautilus, yet is still seen on the tablet.

Using terminal command on my ubuntu pc:
mount:
```

candt@novatech1:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/candt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=candt)

```

Interestingly, my ubuntu (nautilus) display shows at the top
'these files are on a digital music player  [open rhythmbox music player]'

But this is an incorrect association. 
And what about permissions too?

So it looks like the tablet is getting mounted but is not allowing files in folders to be seen, and they are not 'music' anyway.

(FWIW it mounts fully in win7)

Help, comments, anyone please? tia

---

### Post by coffeecat on 2012-08-29
@candtalan, I've moved your post out of this thread:

[http://ubuntuforums.org/showthread.php?t=1785650](http://ubuntuforums.org/showthread.php?t=1785650)

Which was getting a bit long in the tooth, because your question really deserves a fresh thread.

You might find this useful:

[http://hdfpga.blogspot.co.uk/2012/03/connecting-samsung-samsung-galaxy-tab.html](http://hdfpga.blogspot.co.uk/2012/03/connecting-samsung-samsung-galaxy-tab.html)

I have to admit I haven't tried that yet, as I went for the simpler option of using a microSD card to transfer files - at least for the time being. For the record, I'm using a GT-P5110 Galaxy 10.1 Tab2 with Android 4.0.4 and I'm seeing the same in Ubuntu.

---

### Post by candtalan on 2012-08-29
coffeecat thanks. fwiw I already did install mtp tools and a library but no change. Is is significant that win 7 has no prob with it all - opening the usb  device and with functioning file transfer in either direction?  As in my post, files at the tablet top level are seen ok, (the docx in the screenshot) but files in subfolders are not seen. It is a bit outside my experience ....

---

### Post by coffeecat on 2012-08-29
Tbh, it's a bit outside my understanding as well. For explanations, there's a bit at the beginning of this link:

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

The howto in that is really the same as in the earlier link I posted, except that it's strangely garbled with all caps in the commands and stray " characters. You're better off trying the method in the first link. If I get around to trying that howto, I'll post my findings.

---

### Post by candtalan on 2012-08-29
> **coffeecat said:**
> Tbh, it's a bit outside my understanding as well. For explanations, there's a bit at the beginning of this link:

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

The howto in that is really the same as in the earlier link I posted, except that it's strangely garbled with all caps in the commands and stray " characters. You're better off trying the method in the first link. If I get around to trying that howto, I'll post my findings.


Thanks for this.
[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

Yes, however, guessing through most of the garbled stuff, and basically doing what I think was needed. I found that copy paste into a terminal (or text editor) cleaned up the upper case!!

I ended up with a small problem only relating to my use of alias, it did not work and I did not understand enough about alias to guess correct.
However, for the record, ultimately
the command
mtpfs -o allow_other /media/SAMSUNG_Android
DID work, yay!
(SUCCESS)

Comment: my galaxy tab identified itself by name as SAMSUNG_Android so that is what I ended up using.

mtp-detect | grep idVendor
gave:
Device 0 (VID=04e8 and PID=6860) is a Samsung GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note.

So my
SUBSYSTEM=="usb", ATTR{idVendor}=="VENDORID", ATTR{idProduct}=="PRODUCTID", MODE="0666"

became
SUBSYSTEM==&#8221;usb&#8221;, ATTR{idVendor}==&#8221;04e8&#8221;, ATTR{idProduct}==&#8221;6860&#8221;, MODE=&#8221;0666&#8243;

also I modified eventually to:
sudo service udev restart
sudo mkdir /media/SAMSUNG_Android
sudo chmod a+rwx /media/SAMSUNG_Android
sudo adduser candt fuse

(I am username candt)

The 
gksu gedit /etc/fuse.conf
activity was ok

I now have a bash full of wrong failed aliases, I will try to clean the crap somehow, and maybe at a later date, get the alias working correctly......

Thanks for your help


edit
unmount:
fusermount -u /media/SAMSUNG_Android

edit(2)
tried it monnecting again and cannot get it to work , so neds more work, but was good to get it once, anyway

---

