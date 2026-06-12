---
title: "My USB is read only"
date: 2011-05-18
forum: General Help
---

### Post by pottsiex5 on 2011-05-18
I know this question is out there, but none of those are useful for me, im not the best with terminal at the moment, but im learning.
Basically my USB has become read only and i cant copy any files onto it...
Any advice?
Thanks

---

### Post by papibe on 2011-05-18
Is it a hard drive or a stick? Which brand and model are you using?

Could post the result of this after you plug it:
```
$ lsusb
```
Regards.

---

### Post by blackplague1347 on 2011-05-18
> **pottsiex5 said:**
> I know this question is out there, but none of those are useful for me, im not the best with terminal at the moment, but im learning.
Basically my USB has become read only and i cant copy any files onto it...
Any advice?
Thanks

I'm assuming that you're talking about a USB flash drive or external hard drive. Is that correct? 

If so, I had a similar problem once. I had just started using Linux and I had previously used the USB drive as a Live USB stick for some distro or another. After that, it became read-only. Naturally, I wasn't aware that there are different file systems that handle files differently (I was *very *new to the non-Windows world >_> ). I couldn't figure it out, and my thumb drive sat there for months and I just bought another one. Once I learned how,  I reformatted the drive to get rid of everything on it and start from scratch.

I'm still no Linux expert, so someone else may have a better solution than those I'm going to present. Just a forewarning :P

One solution may be to change the ownership of the USB drive using the "chown" command.
Something like: 
```
sudo chown -hR yourusername /path/to/usb/stick 
```I'm not sure if that's exactly what the command would be, so you might want to run "man chown" first and check it out. I once had a partition on my hard drive with data on it that I wasn't allowed to access without being root, so I used "chown" to give my regular user ownership of the file system on the partition. Worked just fine.

Another would be to reformat it (which would cause data loss, so only do this if nothing else works). 
```
sudo mkfs.ext3 /dev/sdb1
```To find out where your USB stick is mounted, open a terminal and run "df -h". In my experience, it's usually mounted under /dev/sdb or /dev/sdb1. Yours may be different. Substitute the location of your flash drive in the above command as necessary. It needs to be unmounted before it the command will work, so if you get an error about it, try "umount /dev/sdb1", again substituting for the location of your flash drive.

---

### Post by wildmanne39 on 2011-05-18
> **pottsiex5 said:**
> I know this question is out there, but none of those are useful for me, im not the best with terminal at the moment, but im learning.
Basically my USB has become read only and i cant copy any files onto it...
Any advice?
Thanks
Hi, I think this would do it.
sudo chown -R yourusername /path/to/usb/stick of course the path is whatever the path to you usb is.

---

