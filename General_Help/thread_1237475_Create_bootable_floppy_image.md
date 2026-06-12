---
title: "Create bootable floppy image"
date: 2009-08-11
forum: General Help
---

### Post by slrohn on 2009-08-11
I need to create a bootable floppy image for use with VirtualBox. I do not have a floppy drive, and a boot CD is not an option.

I'm not sure where to begin with this. I've searched the forums and scoured Google for answers, but nothing has helped thus far.

I think I need to:
1) create a mountable, bootable, floppy image
   [help!]
2) write files to said floppy image
   [easy!]
3) mount the floppy image using a virtual machine in VirtualBox
   [I think I can manage this]

Any pointers?

Thanks!

---- Info ----

Running:
- Ubuntu 9.04 (jaunty)
- Kernel Linux 2.6.28-14-generic

On:
- Dell Inspiron 710m laptop

---

### Post by asai on 2009-08-11
Hi
Right after I sent you my reply on the PM, I think I solved it.

I downloaded this image: [DOS 6.22]("http://s93616405.onlinehome.us/bootdisk/622c.zip")

Inside the ZIP file there is a file called 622C.IMG
Mount this image in Virtualbox, and your up and running on DOS.
If it is some other OS you are looking for, take a look here: [http://www.bootdisk.com/]("http://www.bootdisk.com/")

---

