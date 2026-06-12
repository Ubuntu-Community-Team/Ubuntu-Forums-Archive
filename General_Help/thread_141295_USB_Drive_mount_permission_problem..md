---
title: "USB Drive mount permission problem."
date: 2006-03-08
forum: General Help
---

### Post by guice on 2006-03-08
I posted this on the Kubuntu forums, but seeing this place gets FAR more traffic, I'd though I'd post this here, too.

My USB Drive is getting auto mounted with a umask of 0077, this is a bad thing. Is there anyway I can change this? I need the umask to be 0022.

---

### Post by Sutekh on 2006-03-08
Go to this link 

[http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

It will show you how to edit the /etc/fstab which is where the umask option should go.  Basically modify the line for mounting NTFS partitions for your needs

This is how it should look if /dev/sda1 is the USB drive (**sudo fdisk -l** can check that) and if /media/windows is where you want the USB mounted to (make sure you **sudo mkdir /media/windows** first) and if the USB is NTFS
```
/dev/sda1    /media/windows    ntfs    nls=utf8,umask=0222    0    0
```

If its partitioned using FAT then the line should look similar to this
```
/dev/sda1    /media/windows    vfat    iocharset=utf8,umask=0222    0    0
```

---

### Post by guice on 2006-03-08
No way to do it w/out editing the fstab? Does that mean I'll have to do this to every USB drive I might connect? Not that I plan to connect many, I'd just hoped there would have been a setting inside KDE to fix that.

Now, editing the fstab will cause it to mount on boot. How will KDE handle that when it loads up since KDE (I believe) will attempt to automount the drive, too. Or will it?

---

### Post by Sutekh on 2006-03-08
[QUOTE=guice]No way to do it w/out editing the fstab? Does that mean I'll have to do this to every USB drive I might connect? Not that I plan to connect many, I'd just hoped there would have been a setting inside KDE to fix that.[/QUOTE]Sorry i don't know any other way than to edit the fstab.

[QUOTE=guice]
Now, editing the fstab will cause it to mount on boot. How will KDE handle that when it loads up since KDE (I believe) will attempt to automount the drive, too. Or will it?[/QUOTE]
I'm not sure what you mean by this.  

KDE will attempt to mount the USB based on the information in the fstab (as far as I know)

---

### Post by scokar on 2006-03-08
[QUOTE=guice]No way to do it w/out editing the fstab? Does that mean I'll have to do this to every USB drive I might connect? Not that I plan to connect many, I'd just hoped there would have been a setting inside KDE to fix that.

Now, editing the fstab will cause it to mount on boot. How will KDE handle that when it loads up since KDE (I believe) will attempt to automount the drive, too. Or will it?[/QUOTE]


if your USB partition is /dev/sda1 and your mount point is /media/windows, from the command line you should be able to:

mount -t ntfs -o nls=utf8,umask=0022  /dev/sda1 /media/windows

---

### Post by guice on 2006-03-08
Err, I meant more through KDE's automount interface. :D

KDE automounts USB drives and it's mount is dependant upon at what USB chain you plug in the drive into. Which means, if I were to change it's USB slot, I'd have to change the fstab/mount command (after the Linux gets a clue and realizes there is no drive at /dev/sda1).

I'd like to be able to tell KDE "automount all USB drivers with X settings."

---

### Post by retsaw on 2006-03-09
If a device is not listed in your fstab, then pmount will be used to mount it either by KDE itself with 3.5 or by ivman with 3.4.  I'm not sure how to configure it so that the default umask is 002, but the option is probably lurking somewhere between hal, pmount and KDE (I think it is most likely hal) or maybe ivman if you are using KDE 3.4, I couldn't work out what you need to add/change though.

You could use pmount manually to get the permissions you wanted e.g "pmount -u 002 /dev/sda1".

Another option is you can give your USB drives unique device names using udev and set up individual fstab entries for each of them.  The downside is you need to set up each device individually, so any new USB drives you connect won't be set with the umask you want, but leaving a fstab entry in for sda1 might catch them.

---

### Post by Vati-Khan on 2006-06-07
[QUOTE=guice]
My USB Drive is getting auto mounted with a umask of 0077, this is a bad thing. Is there anyway I can change this? I need the umask to be 0022.[/QUOTE]

I had the same problem - that's my solution

[COLOR="Red"]WARNING: I'm not sure if this procedure is best-practice or if it might break something in the future[/COLOR]

edit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

search for and replace 

```

<match key="volume.fstype" string="vfat">
      <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
      <merge key="volume.policy.mount_option.quiet" type="bool">true</merge>
</match>

```

with

```

<match key="volume.fstype" string="vfat">
      <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
      <merge key="volume.policy.mount_option.quiet" type="bool">true</merge>
      <merge key="volume.policy.mount_option.umask" type="string">0000</merge> <!-- or whatever you desire -->
 </match>

```

please give feedback if it worked

---

### Post by JPorter on 2006-06-14
OK, trying to follow here... I've experimented with the 10-storage-policy.fdi file a bit.

There are separate entries for each type of mountable filesystem as far as I can tell... but adding **<merge key="volume.policy.mount_option.umask" type="string">0000</merge>** to the NTFS section does not make an external USB2.0 NTFS volume writable.


Can anyone tell me what key values to merge to make USB hot-add NTFS drives writable using this method?  I can mount and write via fstab using ntfs-fuse.



Thanks for any help you can provide a newbie... :D

---

### Post by b8s on 2006-06-21
Like JPorter, i also tried to enable writing to a NTFS usb drive with the 10-storage-policy.fdi file method. This did not give positive results. (probably has something to do with the line being added to the section for "vfat" volumes.)  

After looking through the file and trying that line in other locations, i still cant get the drive to automount with writing enabled.

Does anybody know of any other way to auto-mount any NTFS USB drive with writing enabled?

thnx

---

### Post by gReEnT3a on 2006-06-22
Probably you attached the USB drive to your pc while you are booting?

If that's so, I noticed that Ubuntu will generate new entry for that drive of yours in fstab..

what I did was unplugged the USB drive, open fstab and remove that drive entry from it 

save and plug it back again and it should be fine

---

### Post by Sir_Yaro on 2006-06-23
[QUOTE=Vati-Khan]I had the same problem - that's my solution

[COLOR="Red"]WARNING: I'm not sure if this procedure is best-practice or if it might break something in the future[/COLOR]

edit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

search for and replace 

```

<match key="volume.fstype" string="vfat">
      <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
      <merge key="volume.policy.mount_option.quiet" type="bool">true</merge>
</match>

```

with

```

<match key="volume.fstype" string="vfat">
      <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
      <merge key="volume.policy.mount_option.quiet" type="bool">true</merge>
      <merge key="volume.policy.mount_option.umask" type="string">0000</merge> <!-- or whatever you desire -->
 </match>

```

please give feedback if it worked[/QUOTE]
works perfectly on drake, thanks

---

### Post by kherim on 2006-07-20
> **Vati-Khan said:**
> I had the same problem - that's my solution

[COLOR="Red"]WARNING: I'm not sure if this procedure is best-practice or if it might break something in the future[/COLOR]

edit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

search for and replace 

```

<match key="volume.fstype" string="vfat">
      <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
      <merge key="volume.policy.mount_option.quiet" type="bool">true</merge>
</match>

```

with

```

<match key="volume.fstype" string="vfat">
      <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
      <merge key="volume.policy.mount_option.quiet" type="bool">true</merge>
      <merge key="volume.policy.mount_option.umask" type="string">0000</merge> <!-- or whatever you desire -->
 </match>

```

please give feedback if it worked

works !!!! (drake), thanks

---

### Post by nirudha on 2007-02-25
For NTFS drives refer to [http://www.ubuntuforums.org/showthread.php?t=337970&highlight=ntfs-config]("http://www.ubuntuforums.org/showthread.php?t=337970&highlight=ntfs-config")

the link given in the start of the thread was down but on page 5 you get another link which worked for me,

[http://files.maturaball06.com/ntfs-config_0.5.5-0ubuntu1_i386.deb]("http://files.maturaball06.com/ntfs-config_0.5.5-0ubuntu1_i386.deb")

---

