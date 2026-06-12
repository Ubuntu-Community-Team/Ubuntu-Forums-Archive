---
title: "External USB drive - switch on and off and automount?"
date: 2010-05-28
forum: General Help
---

### Post by capitales7 on 2010-05-28
I'm trying to setup my media streaming server, and everytying is going quite well, but there's one thing I don't understand.
Can you have ubuntu automatically pick up and mount your external USB drive when you switch it on?

I don't like leaving the hard drive running, and I only need to have it on when I want to stream something, but it seems to lose the mount when I switch it off and on again.
Anyway to make it automatically detect that it's on and mount it back onto my mount point?

Thanks.

---

### Post by capitales7 on 2010-06-01
bump....anyone :(

---

### Post by cj.surrusco on 2010-06-01
What format is the drive in? If it is ext3 or something similar you will be able to mount it by UUID. If not, it will be harder since the drive location may change.

---

### Post by capitales7 on 2010-06-02
> **cj.surrusco said:**
> What format is the drive in? If it is ext3 or something similar you will be able to mount it by UUID. If not, it will be harder since the drive location may change.
df -T
/dev/sdb1  fuseblk   976760000 497644220 479115780  51% /media/External

NTFS. I mounted it with mount -t ntfs-3g /dev/sdb1 /media/External if I recall.
The thing that annoys me is that when I switch it on and off ubuntu seems to automount it (it appears on the desktop when I VNC), but not to that location. This could be because /media/External isn't umounted first perhaps?

---

### Post by john newbuntu on 2010-06-02
See if following the instructions in "configuring automounting" from this document helps you:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by capitales7 on 2010-06-02
> **john newbuntu said:**
> See if following the instructions in "configuring automounting" from this document helps you:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

I actually did read that already and went through with it. But the problem it seems to have is that if you just switch off the drive without doing anything on the OS side, the mount seems to remain active for a while. If I ls or cd the mountpoint I get "input output error" or something.

When I switch the drive back on, it sometimes shows up as sdc, and the automount mounts it to /media/External_ (notice the _).
This would be fine if I only needed the drive for normal access, but my PS3 media server is looking for the /media/External location only, and it basically renders my media server useless if that's not the exact location of the drive.

...does all that even make sense (I'm seriously tired... baby crying etc)

---

### Post by jarviser on 2010-06-02
As far as I am concerned there's only two safe ways to stop a USB drive, and that's either leave it running while you shut down the PC, or select Safely Remove (or Unmount/eject). If you do the latter you will need to unplug and plug back in to detect it. Although most drives are now spring return and physical damage is a thing of the past, there's no guarantee that all data blocks have been written from the last write if you simply power down. 
I may be out of date but I always believed that was why the Safely Remove option was added to both Linux and Windoze.

---

### Post by capitales7 on 2010-06-02
> **jarviser said:**
> As far as I am concerned there's only two safe ways to stop a USB drive, and that's either leave it running while you shut down the PC, or select Safely Remove (or Unmount/eject). If you do the latter you will need to unplug and plug back in to detect it. Although most drives are now spring return and physical damage is a thing of the past, there's no guarantee that all data blocks have been written from the last write if you simply power down. 
I may be out of date but I always believed that was why the Safely Remove option was added to both Linux and Windoze.

No no, I completely agree. I actually lost around 8GB of data off a flash drive once, because I forgot to eject the damn thing. But I noticed that external drives (non-flash) are quite safe to just power down. But you gave me an idea. Gonna try and umount it, switch it off, then power it back up to see if it automounts to the same mount point.

---

### Post by jarviser on 2010-06-02
...I was going to add that media playing is mostly read-only but the OS is surely designed for controlled shut-down to finish all I/O operations cleanly.

---

### Post by capitales7 on 2010-06-02
A colleague of mine suggested to simply spinning down the disk to basically achieve what I want. I tried sg_start, but my disk doesn't spin down.
It's relatively new 1TB Lacie (samsung HDD inside) usb disk.

Man, there's no way to do this.
Maybe I should just write a script, cron it to poll the mount point and mount the disk when needed? :(

---

### Post by el_manaba on 2010-07-07
Was this ever resolved?

I have the same problem.  I have an external USB HDD (NTFS) that is always plugged in.  When I need it, I want to just turn it on and have the OS automount it.  But it won't automount it unless I unplug the usb cable and reinsert it.  It won't even show up in fdisk -l until I reinsert the cable.

If I get it to mount this way and then unmount it and switch it off.  When I turn it back on, I have to unplug it and plug it back in to get it to automount.

Is there a way to get Ubuntu to automount when I turn on a drive that's already plugged in?

---

### Post by JoelOl75 on 2010-07-07
> **el_manaba said:**
> 
Is there a way to get Ubuntu to automount when I turn on a drive that's already plugged in?

As far as I know it already does this by default, even popping up a nautilus session to browse the disks content (I'm using xfs on one drive and ext3 on another and both do this)

---

### Post by capitales7 on 2010-07-07
> **el_manaba said:**
> Was this ever resolved?

I have the same problem.  I have an external USB HDD (NTFS) that is always plugged in.  When I need it, I want to just turn it on and have the OS automount it.  But it won't automount it unless I unplug the usb cable and reinsert it.  It won't even show up in fdisk -l until I reinsert the cable.

If I get it to mount this way and then unmount it and switch it off.  When I turn it back on, I have to unplug it and plug it back in to get it to automount.

Is there a way to get Ubuntu to automount when I turn on a drive that's already plugged in?

I wrote a php script and run it in cron every minute.
If the script detects the id (/dev/disk-byid/) of the disk, it mounts it, if it doesn't, it unmounts it.
Apparently ubuntu doesn't automatically do that for my drive... it just keeps the mount point open, and the next time you switch it on, it will fail to mount, so I have to do everything manually. SCRIPTS FOR THE WIN! :D

---

### Post by jarviser on 2010-07-07
> **capitales7 said:**
> I wrote a php script and run it in cron every minute.


Sounds very interesting - please could you publish the script and explain the method?

---

### Post by capitales7 on 2010-07-07
> **jarviser said:**
> Sounds very interesting - please could you publish the script and explain the method?

Don't have it to hand right now (at work), but it's a very crude script that simply uses a series of exec commands.

Here's some pseudo code:

GREP for disk id in /dev/disk/by-id

IF ID FOUND
determine [location] (e.g /dev/sdb1/sdc1)
LS [mountpoint]
IF EMPTY (i.e. drive not already mounted)
mount [location] to [mountpoint]

IF NO ID FOUND
umount [mountpoint]
exit script

That's basically it.
There's minimal amounts of PHP in the script, and it's mostly exec("linux cmdline command");, which just a few variables and arrays used to check values etc in PHP.

If anyone wants to see th script still, I can post it here.

---

### Post by capitales7 on 2010-07-07
Actually, just setup my tunnel and got the script. I'm using sudo becasuse I don't want to run this as root (my script kicks off other shell scripts that are not included here, and they have to run as my user). I have no knowledge of awk, and I'm sure there's an easier way to do it using awk, but here's my method.

NOTE: The cut field number in the first command will vary depending on your username. Since my cut delimiter is [space], it will be the amount of spaces between your username and the next value. My username is 3 characters, so -f10 works. Just need to count and modify it.

[PHP]
<?php
$command = "/bin/ls -l --time-style=long-iso /dev/disk/by-id | /bin/grep [ID OF DISK] | /usr/bin/cut -d' ' -f10";
exec($command, $drive);

if(!empty($drive))
{
        $loc = substr($drive[0], -4);

        $command = "/bin/ls -l --time-style=long-iso /media/External | /bin/grep total | /usr/bin/cut -d' ' -f2";
        exec($command, $mounted);
        if($mounted[0] == 0)
        {
                $command = "/bin/echo [SUDO PASSWORD] | /usr/bin/sudo -S /bin/mount /dev/$loc /media/External";
                exec($command);
        }
}
else
{
        $command = "/bin/ls /media/External";
        exec($command, $off);

        if(empty($off))
        {
                $command = "/bin/echo [SUDO PASSWORD] | /usr/bin/sudo -S /bin/umount /media/External";
                exec($command);
        }
}

?>
[/PHP]
The biggest flaw in this script is that it basically umounts your drive every minute, even when the drive is off! But that's something I'll just live it... doesn't hurt the system anyway.

---

### Post by el_manaba on 2010-07-08
It sounds like this may be a hardware related problem since some users experience it and others don't.  I believe I'll still report it as a bug.  In the mean time, capitales7's script seems like a suitable work around, at least better than unplugging the USB cable from the back of the case and reinserting it every time I need to use my drive.

Thanks all!:)

---

