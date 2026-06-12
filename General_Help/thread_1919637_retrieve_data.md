---
title: "retrieve data"
date: 2012-02-03
forum: General Help
---

### Post by nn2 on 2012-02-03
My old computer a Toshiba satellite Pro had windows and crashed. I am trying to retrieve data using this article 
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
and a CD ubuntu 9.04 Desktop edition.

I boot ubuntu from cd and when I open the Computer file browser, 40GB Media appear and clicking it the message 
"Cannot mount volume" without details option

then the message "Opening 40gb media"

then the message "Unable to mount location" Details:
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Then "cannot mount volume" Details:
ntfs_attr_pread_i: ntfs_pread failed: input/output error
Failed to read vcn 0x5: Input/output error Failed to mount '/dev/sda1':Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/directory, (eg. /dev/mapper/nvidia_eahaabcc1). Please see 'dmraid' documentation for more details.



Can anyone help from here? I have tried to fix it before unsuccessfully so I might have done smth wrong, first time i booted with cd it run immediately now first i get many errors screens before ubuntu starts.

---

### Post by drmrgd on 2012-02-03
I might be misinterpreting the error.  However, it looks to me like that drive is in bad shape and failing, which might be why you can't mount it. I would recommend following the instructions given in the error, and try rebooting to Windows command line and running chkdsk /f to have Windows verify the integrity of the drive.  Assuming it's just corrupt and not physically failing, you may be able to revive it (or at least get it mountable to rescue your data).

---

### Post by Bucky Ball on 2012-02-03
Yea, could be dead or dying. Any chance of trying this with a more recent and stable version of Ubuntu (10.04 LTS for instance) as 9.04 is no longer supported? There has been some improvements since then but not sure if they're gonna help here. Worth a shot.

---

### Post by jerrrys on 2012-02-03
Maybe TestDisk would work on this.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by nn2 on 2012-02-03
I saved Testdisk on USB stick, run it from there and nothing happens. A window "Open files" opens with 2 empty boxes: Available application and Recent applications.

Can you explain how to run chdsk /f on Windows?
Windows are not booting at all. I am using the ubuntu cd without installation to access the files i had.

---

### Post by drmrgd on 2012-02-03
I would first try to boot to safe mode with command prompt (although this may not work if the drive is experiencing severe problems).  When you start your computer, right after the BIOS screen goes away tap the F8 key until you get a Windows boot manager screen (this may take a couple tries to get the timing right).  Then select Safe Mode with Command Prompt.  

If that doesn't work, the only way I'm aware of to do it is to boot from a Windows CD and get into the Recovery Console.  Here is a website with some instructions on that:

[http://www.computerhope.com/issues/ch000627.htm]("http://www.computerhope.com/issues/ch000627.htm")

You might also contact Toshiba or look up some info on that particular machine.  Some computer manufacturers put a recovery partition on the drive in order to facilitate addressing problems like this.  If you have such a partition, this may be another way to go.

---

