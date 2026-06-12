---
title: "Rsync between Windows XP and headless Ubuntu"
date: 2010-03-23
forum: General Help
---

### Post by John J. Smith on 2010-03-23
I've been trying to get my headless Ubuntu 9.10 server to back up files from my Windows XP box and onto a 1 TB Seagate FreeAgent Go USB drive (which is connected to the Ubuntu server). I've tried two different methods, both of which are behaving strangely and not quite working. I'm using SSH to access my Ubuntu server.
     
     The /etc/fstab line for the USB drive looks like this:
     
     ```

/dev/sdb1 /media/usb-backup-windows ntfs uid=34,gid=34,umask=022,dirsync,sync 0 0
     
```     I'm using NTFS because I'd like to share this drive between Windows and Linux. The drive gets mounted fine and I can read/write files after booting up.
     
     The way I'd like for this to work is to have my Ubuntu box mount the Windows drive using CIFS. So I mounted the C drive using the following command:
     
     ```

smbmount //windowsxp/C$ /mnt/windowsxp/C -o directio,iocharset=utf8,noperm,nounix,ro,credentials=/home/user/.smb/passwords.conf
     
```    The mount works fine. I can browse directories under /mnt/windows/xp/C, read files, copy files to Ubuntu, etc. So now I have my USB drive mounted and the C drive on my Windows box mounted. Should be good to go, right? Unfortunately, after several minutes (this varies, sometimes it can go an hour or so) of copying files using [FONT=Courier New]rsync --archive /mnt/windowsxp/C/ /media/usb-backup-windows/C/[/FONT] (the actual command I use has more options - not sure if that's important), the server locks up. The SSH session dies and I can no longer ping it. The server will eventually start responding after several minutes, only to lock up again a few minutes later, and so on and so on. When it locks up, the following messages end up in /var/log/kern.log:
     
     ```

CIFS VFS: Unexpected lookup error -26
CIFS VFS: No response to cmd 46 mid 59789
CIFS VFS: Send error in read = -11
CIFS VFS: server not responding
     
```     I did some Googling on these messages and came across a suggestion to set /proc/fs/cifs/OplockEnabled to 0. I gave that a shot but it didn't make a difference. I also tried plugging in a mouse and noticed that I could make the server respond immediately after a lock up by moving the mouse. I have to move the mouse though - just leaving it plugged in without movement doesn't help. I have to wait for the hang to occur and then move it. Once I do that, things progress for another few minutes.
     
    This got me thinking that I had a lack of entropy and the mouse movement was kicking things into gear. So I tried moving /dev/random to /dev/random-chaos, and created a symlink /dev/random that just pointed to /dev/urandom. This didn't work - same exact behavior. So why in the world does moving the mouse bring the server back and cause it to start responding, if only for a few more minutes until the next hang?
     
     I then gave up on this approach and tried connecting to an rsync daemon running on my Windows box (using Cygwin), instead of using the CIFS mount point. After getting the config file right and figuring out how to run it as a service on Windows, I started getting files copied once again. However, after what seems to be about the same length of time (several minutes to an hour or so), the rsync connection dies and I get the following message in the Windows rsync log file:
     
     ```

2010/03/22 13:01:01 [4024] rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Connection reset by peer (104)
2010/03/22 13:01:01 [4024] rsync error: error in rsync protocol data stream (code 12) at io.c(1539) [sender=3.0.7]
     
```    The Windows box is running rsync 3.0.7 and Ubuntu is running 3.0.6, but they are both protocol 30. The rsync error log on Ubuntu doesn't help much - it also says "Connection reset by peer". I've tried this at least a dozen times and it always fails with these messages. It's weird because it's always 4 bytes, never anything different.
    
    I also noticed that /var/log/kern.log had the following messages, although they do not line up with the times that rsync died:
     
     ```

usb 1-5: reset high speed USB device using ehci_hcd and address 2
     
```     I did some Googling on this message and tried some stuff that worked for other people. I added dirsync and sync to /etc/fstab. I tried setting /sys/block/sdb/device/max_sectors to 64. Neither one of those made a difference. I saw another post that suggested unloading the ehci_hcd module and dropping back to USB 1.0. However, 9.10 doesn't seem to have that module loaded, so I'm not exactly sure how to turn off USB 2.0 and just try 1.0. I'm not real enthused with that workaround anyway because I have at least 500 GB to copy.
    
    I've kind of run out of ideas here. It's frustrating because the entire reason I bought the hardware and set up Ubuntu was to run backups. I'm not sure if my problem is a networking issue (CIFS VFS server not responding, connection reset by peer), a problem with running headless (wiggling the mouse temporarily prevents the hang), a USB device problem (reset high speed USB device messages), or something else entirely.
    
    Any ideas would be much appreciated.

---

### Post by HermanAB on 2010-03-23
I think your problem is a known bug in the Seagate disk drive controller.  Some Googling may find information and a workaround for that.

---

### Post by John J. Smith on 2010-03-26
I've experimented a bit more with this and I'm still trying to get it to work. I came across [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746?comments=all) and discovered that tons of people are having problems with the ehci_hcd driver.

There are quite a few workarounds listed in that bug report, but none of them worked for me. I tried the following:


[LIST]
[*]Set /sys/module/usbcore/parameters/autosuspend to -1.
[*]Tried various settings for max_sectors (64, 128, 1024).
[*]Tried hooking up the Seagate drive to a powered USB 2.0 HUB.
[*]Tried mounting the drive with various combinations of dirsync, sync, etc.
[/LIST]
None of these workarounds helped. I was still getting the "reset high speed USB device" errors. I then got desperate and tried disabling ehci_hcd to drop back to the USB 1 driver. That can be done with the following, as root:

```

cd /sys/bus/pci/drivers/ehci_hcd
echo -n 0000:00:1d.7 > unbind
```You have to do an ls to figure out what bus you have. After remounting, I kicked off the rsync and went to bed. I checked on it 10 hours later and it was still chugging along! No more resets. The problem of course is that the backup was only a fraction of the way finished. Using USB 1 speeds isn't really a viable option. It's just way too slow.

So I went out and bought another USB 2.0 external hard drive. This time a Western Digital My Passport. With this device, the behavior is a little different. I no longer get "reset high speed USB device" errors. However, after about 5-20 minutes of copying data, the entire system will just hang for a couple minutes. When it's hanging my SSH sessions die, I can't ping it, etc. It's totally unresponsive. It will eventually come back to life but by then rsync has been disconnected and the backup is killed.

If I tail the rsync log and watch closely, I can tell when the hang begins. If I then move the mouse a millimeter (the system is supposed to be headless but I still have a USB mouse plugged in), it will wake up and continue processing. If I wait too long (about 30 seconds), all the connections die.

So what's the deal with moving the mouse? I can get the rsync to progress indefinitely as long as I move the mouse. If I stop moving the mouse, things will die. Is there some way to emulate a mouse movement? I'm very confused. I'm honestly trying to think of a way to set up some robot thingy that just mechanically moves the mouse back and forth.

---

### Post by John J. Smith on 2010-03-27
In case anyone's following this, I also tried upgrading to the latest 10.04 Lucid Alpha release. I'm getting the same behavior with the weird system freeze after copying files for several minutes. Again, moving the mouse appears to be the only way to get it unstuck.

---

### Post by cjhabs on 2010-03-27
> **John J. Smith said:**
> In case anyone's following this, I also tried upgrading to the latest 10.04 Lucid Alpha release. I'm getting the same behavior with the weird system freeze after copying files for several minutes. Again, moving the mouse appears to be the only way to get it unstuck.

Is there some power management kicking in and turning off the network card?

---

### Post by John J. Smith on 2010-03-28
> **cjhabs said:**
> Is there some power management kicking in and turning off the network card?

Essentially, that's what it was. I came across a discussion over at [http://forums.overclockers.com.au/showthread.php?t=763940&page=5](http://forums.overclockers.com.au/showthread.php?t=763940&page=5) that suggested disabling C-States in the BIOS and instead enabling GV3. I had never heard of these before, but they're apparently different ways of managing CPU power states. The C-States option appears to be completely broken; disabling it resolves the problems I was experiencing. The rsync now completes successfully and I don't have any more weird hangs or system freezes. Yay!

---

### Post by torsson on 2010-09-20
Hi, I seem to have similar problem.

i have 2 Dell R300 Servers, intel processor, 2 intel network cards and i use GlusterFS (Also tried NFS). and when i move files trough the network on the GlusterFS shares the server completly dies. And it seems to be something with the network cards. But next week im gona go where the server is and se if i can change C-State to GV3 in the Bios and hopefully this will solve my problem to (If my Xeon processor has this settings?).

Im using Ubuntu Jaunty 9.04 with Xen 4.0 and Jeremys latest stable kernel 2.6.32.21. and i have also tried with ubuntu's Xen 2.6.24-19-Xen kernel and same issue.

---

