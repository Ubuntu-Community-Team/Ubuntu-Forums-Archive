---
title: "dd if=/dev/cdrom of=/tmp/cdimg1.iso"
date: 2010-06-09
forum: General Help
---

### Post by limestone on 2010-06-09
Hi guys, I got a mysterious thing going on here. I'm about to copy my Rollercoaster2 cd to an ISO using dd. I open a terminal and typed umount /dev/cdrom and then dd if=/dev/cdrom of=/tmp/roller2.iso. I get following output:
dd: reading `/dev/cdrom': Input/output error
1284832+0 records in
1284832+0 records out
657833984 bytes (658 MB) copied, 446.532 s, 1.5 MB/s

So, what's the Input/Output error? And when I mount the image I got a empty disk with 0 size, still the image is 658Mb???

Anyone familiar with dd?
/Thanks

---

### Post by Bachstelze on 2010-06-09
It means that the kernel has trouble reading from the CD, probably a scratched/dirty disc, or maybe a drive failure. As for the mounted image, how are you mounting it?

---

### Post by lavinog on 2010-06-09
did the cdrom drive show any activity during the operation?

---

### Post by limestone on 2010-06-09
> **Bachstelze said:**
> It means that the kernel has trouble reading from the CD, probably a scratched/dirty disc, or maybe a drive failure. As for the mounted image, how are you mounting it?
I mount it using Ubuntu's built in Archive mounter. The cd is not scratched btw..

---

### Post by limestone on 2010-06-09
the cd/dvd drive LED blinks but the hard drive seems not to write that much.

---

### Post by darkdragn on 2010-06-09
Well, one option might be to scrap that image, install ddrescue, and run it. 

dd_rescue /dev/sr0 **/tmp/cdimg1.iso**

... also... it might have worked, if you would have done

dd if=/dev/sr0 of=/tmp/cdimg1.iso

You make an image of a directory, not a device... i've never seen anyone do that...

Edit: Since you said it isn't scratched, I'm sure that's what's wrong. You did a byte copy of a directory, and pushed all of the files into one... not a byte copy of a device with filesystem structure included. Once you do 

dd if=/dev/sr0 of=/tmp/cdimg1.iso

Mount it as follows
cd /tmp
mkdir temp
mount -o loop cdimg1.iso temp/

---

### Post by limestone on 2010-06-09
> **darkdragn said:**
> Well, one option might be to scrap that image, install ddrescue, and run it. 

dd_rescue /dev/sr0 **/tmp/cdimg1.iso**

... also... it might have worked, if you would have done

dd if=/dev/sr0 of=/tmp/cdimg1.iso

You make an image of a directory, not a device... i've never seen anyone do that...

Edit: Since you said it isn't scratched, I'm sure that's what's wrong. You did a byte copy of a directory, and pushed all of the files into one... not a byte copy of a device with filesystem structure included. Once you do 

dd if=/dev/sr0 of=/tmp/cdimg1.iso

Mount it as follows
cd /tmp
mkdir temp
mount -o loop cdimg1.iso temp/

This solution works! Wonder why Ubuntu's archive mounter wont work. Anyhow, Thanks=)

---

### Post by john newbuntu on 2010-06-09
Yeah, the archive mounter does not work for me either.  It does not even open a window.  On the other hand, it mounts the iso in $HOME/.gvfs/ - really intuitive.
Right click the .iso file and use archive manager instead.  It works a lot better.

---

