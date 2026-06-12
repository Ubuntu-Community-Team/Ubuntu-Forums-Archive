---
title: "QEMU disk error booting Win2K"
date: 2005-02-20
forum: General Help
---

### Post by sleepyhead on 2005-02-20
After installing qemu-0.6.1 (along with kqemu-0.6.2) from source, I created a disk image in / with the command:
qemu-img create win2k.img 2050M

Then I dumped my Win2K cd to hard disk using the command:
dd if=/dev/cdrom of=/win2k.iso

Then I ran qemu with the following command:
qemu -hda /home/username/win2k.img -cdrom /win2k.iso -boot d -std-vga 

I was able to install Win2K, and I rebooted it serveral time, and it starts back up fine. But, if I shut it down, when I run the qemu command again, I get:

Disk Error
Press any key to restart

I Googled and found at least one other person who has this problem:
[http://www.emuscene.com/view.php?a=12&p=1](http://www.emuscene.com/view.php?a=12&p=1) 

Has anyone been able to work around this?

---

### Post by sleepyhead on 2005-02-21
I just got a response on the QEMU forums. Somebody else had the same problem, but the CVS version seems to work fine. I'll give it a shot tonight.

---

### Post by sidd-tx on 2005-08-05
I just had a similar problem. 
Installed qemu from Ubuntu Repositories. 
Installed W2K. 
Emulator had to reboot after installing. 
Received disk error. 

I resolved this problem without having to reinstall W2K into the emulator by:
Following Lunde's guide, almost exactly, but not to the "T"..

[http://ubuntuforums.org/showthread.php?t=39513](http://ubuntuforums.org/showthread.php?t=39513)

I downloaded and installed 0.7.1 instead of 0.7.0...

I could not get the checkinstall route to work.
I just did the traditional 
./configure
make
make install

For some reason, I had to remount /dev/shm according to an error message
And started emulator with:
qemu -boot c -hda /path/to/hd.img -user-net -pci -m 256

W2K booted without any further errors..

I am not going to even pretend to know how or why this worked.. It took about 4 
hours of piddling around.. 

Hope it helps...

sidd

---

