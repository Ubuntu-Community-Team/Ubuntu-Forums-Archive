---
title: "CD Burning problem"
date: 2010-03-09
forum: General Help
---

### Post by rthorpe on 2010-03-09
Hello,

I'm trying to burn a CD.  I have an ISO file, so I use Wodim/CDRecord. So:

# sudo wodim -dev='dev/cdrw' -multi -v -tao ~/cd.iso

Wodim gives the following error:
"wodim: No such file or directory. 
Cannot open SCSI driver!"

Since I only have one CD burner the device name dev/cdrw should work.

It doesn't work either if I use the device name given by "wodim --devices"

#sudo wodim -dev='dev/scd0' -multi -v -tao ~/cd.iso

This gives the same error about the SCSI driver as above.

I've heard that sometimes the CD-R will be automounted, but I've checked for that and it isn't happening.
#umount /dev/cdrom
gives
umount: /media/cdrom0 is not mounted (according to mtab)

I'm using Ubuntu 8.04 on a Dell Inspiron 1525.

---

### Post by rthorpe on 2010-03-09
I have been able to burn CDs with Brasero.

Is there a way to find out the series of commands Brasero used to create a CD?

---

### Post by cjhabs on 2010-03-09
> **rthorpe said:**
> Hello,

I'm trying to burn a CD.  I have an ISO file, so I use Wodim/CDRecord. So:

# sudo wodim -dev='dev/cdrw' -multi -v -tao ~/cd.iso

Wodim gives the following error:
"wodim: No such file or directory. 
Cannot open SCSI driver!"

Since I only have one CD burner the device name dev/cdrw should work.

It doesn't work either if I use the device name given by "wodim --devices"

#sudo wodim -dev='dev/scd0' -multi -v -tao ~/cd.iso

This gives the same error about the SCSI driver as above.

I've heard that sometimes the CD-R will be automounted, but I've checked for that and it isn't happening.
#umount /dev/cdrom
gives
umount: /media/cdrom0 is not mounted (according to mtab)

I'm using Ubuntu 8.04 on a Dell Inspiron 1525.

I suspect the device should be /dev not dev

---

### Post by rthorpe on 2010-03-09
That's the problem.  Thanks a lot.

---

