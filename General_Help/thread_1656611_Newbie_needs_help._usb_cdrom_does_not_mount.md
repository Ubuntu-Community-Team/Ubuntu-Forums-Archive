---
title: "Newbie needs help. usb cdrom does not mount"
date: 2010-12-31
forum: General Help
---

### Post by xr4ti on 2010-12-31
My cdrom is not mounting on ubuntu 8.04. I find this message in syslog (below).  How can I resolve this?
 
<code>
 
 
Dec 30 16:13:26 ubuntusap kernel: [ 351.765683] usb-storage: device scan complete
Dec 30 16:13:26 ubuntusap kernel: [ 351.766423] scsi 5:0:0:0: CD-ROM Memorex DVD+-RAM 530L v1 5M64 PQ: 0 ANSI: 0
Dec 30 16:13:26 ubuntusap kernel: [ 351.766785] scsi 5:0:0:0: Attached scsi generic sg1 type 5
Dec 30 16:13:26 ubuntusap kernel: [ 351.856208] Driver 'sr' needs updating - please use bus_type methods
Dec 30 16:13:26 ubuntusap kernel: [ 351.861991] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 30 16:13:26 ubuntusap kernel: [ 351.861994] Uniform CD-ROM driver Revision: 3.20
Dec 30 16:13:26 ubuntusap kernel: [ 351.862029] sr 5:0:0:0: Attached scsi CD-ROM sr0
 
</code>

---

### Post by xr4ti on 2010-12-31
Surely someone can help me. 
 
> **xr4ti said:**
> My cdrom is not mounting on ubuntu 8.04. I find this message in syslog (below). How can I resolve this?
 
<code>
 
 
Dec 30 16:13:26 ubuntusap kernel: [ 351.765683] usb-storage: device scan complete
Dec 30 16:13:26 ubuntusap kernel: [ 351.766423] scsi 5:0:0:0: CD-ROM Memorex DVD+-RAM 530L v1 5M64 PQ: 0 ANSI: 0
Dec 30 16:13:26 ubuntusap kernel: [ 351.766785] scsi 5:0:0:0: Attached scsi generic sg1 type 5
Dec 30 16:13:26 ubuntusap kernel: [ 351.856208] Driver 'sr' needs updating - please use bus_type methods
Dec 30 16:13:26 ubuntusap kernel: [ 351.861991] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 30 16:13:26 ubuntusap kernel: [ 351.861994] Uniform CD-ROM driver Revision: 3.20
Dec 30 16:13:26 ubuntusap kernel: [ 351.862029] sr 5:0:0:0: Attached scsi CD-ROM sr0
 
</code>

---

### Post by dandnsmith on 2011-01-01
I'm not sure what is going on - unfortunately one of the messages suggests updating a driver, and I think 8.04 has dropped off the support list. Could you install a later version (10.04LTS would be a good move)?

---

### Post by xr4ti on 2011-01-02
> **dandnsmith said:**
> I'm not sure what is going on - unfortunately one of the messages suggests updating a driver, and I think 8.04 has dropped off the support list. Could you install a later version (10.04LTS would be a good move)?
 
Thanks.  8.04 is also a LTS version.

---

### Post by QLee on 2011-01-02
[QUOTE=xr4ti]Surely someone can help me.[/QUOTE]

The output you have shown shows that the system has identified the CD-ROM and assigned it to sr0.

Can you explain in more detail what you expect from "mount". If you put a data CD into it, does the light come on and the drive spin-up as if it is trying to read?

---

### Post by xr4ti on 2011-01-03
> **QLee said:**
> The output you have shown shows that the system has identified the CD-ROM and assigned it to sr0.
 
Can you explain in more detail what you expect from "mount". If you put a data CD into it, does the light come on and the drive spin-up as if it is trying to read?
 

Thanks for responding.  
 
I assumed that it was assigned to sr0 so I also assumed that I should find /dev/sr0 but I don't.  If I place a data cd (such as my ubuntu install cd) into the drive I also expect the ls command (ls -la /dev/sr0) to display the files on the cd but it doesn't.  How can I display the files on my cdrom?

---

### Post by dandnsmith on 2011-01-04
> **xr4ti said:**
> Thanks for responding.  
 
I assumed that it was assigned to sr0 so I also assumed that I should find /dev/sr0 but I don't.  If I place a data cd (such as my ubuntu install cd) into the drive I also expect the ls command (ls -la /dev/sr0) to display the files on the cd but it doesn't.  How can I display the files on my cdrom?

two methods spring to mind:
1. use Places|Computer to bring up Nautilus. If mounted, the CD/DVD drive will show that it can see a filesystem, which you can then display by clicking on it in the LH column
2. in a terminal window, issue the *mount* command to show where the disk is mouted. It will list /dev/sr0 as mount on /media/xxxxx. You can then list the files under that /media/xxxx.

Note that the ls on /dev/sr0 cannot but show details of the node type (with cdrom somewhere in it), any more than ls -al /dev/sda1 will list files in the first partition of a HDD (try it). You have to address the point in the file structure where the device is mounted to see the files.

---

### Post by xr4ti on 2011-01-04
> **dandnsmith said:**
> two methods spring to mind:
1. use Places|Computer to bring up Nautilus. If mounted, the CD/DVD drive will show that it can see a filesystem, which you can then display by clicking on it in the LH column
2. in a terminal window, issue the *mount* command to show where the disk is mouted. It will list /dev/sr0 as mount on /media/xxxxx. You can then list the files under that /media/xxxx.
 
Note that the ls on /dev/sr0 cannot but show details of the node type (with cdrom somewhere in it), any more than ls -al /dev/sda1 will list files in the first partition of a HDD (try it). You have to address the point in the file structure where the device is mounted to see the files.
 
Thanks for responding.  I'm a newbie with just a little Unix experience.  That said I don't know how to Places|Computer but I'm assuming that you mean use a desktop menu item and I don't have any such thing.  I installed the Ubuntu 8.04 server then installed minimal UI (I think its gnome) stuff.  
 
Anyway I got your point #2 but sr0 doesn't even appear in /dev.  Also the mount command has no mention of sr0 or /media/cdrom (or /media/xxx,  xxx being anything else).

---

### Post by QLee on 2011-01-04
Yes, I would have expected there to be an sr0 in /dev, I would have also expected there to be a link there for cdrom.

Does it spin-up when you put a data CD in? Does it show up if you boot with a data CD in it?

I do remember a while back seeing questions about CDROMs not being recognised, it might have been with 8.04. I don't remember much because I didn't have the problem so didn't read them carefully. Maybe that caution about the driver, from your syslog, might need to be investigated. Maybe the kernel module really does need updating in 8.04, your device is probably pretty new. It might be of some benefit to search the forum for threads about CDROMs not mounting or not working and see if any apply to your issue.

Sorry, I'm not helping, except to suggest you search, if I think of anything else I'll post back.

---

### Post by xr4ti on 2011-01-04
> **QLee said:**
> Yes, I would have expected there to be an sr0 in /dev, I would have also expected there to be a link there for cdrom.
 
Does it spin-up when you put a data CD in? Does it show up if you boot with a data CD in it?
 
I do remember a while back seeing questions about CDROMs not being recognised, it might have been with 8.04. I don't remember much because I didn't have the problem so didn't read them carefully. Maybe that caution about the driver, from your syslog, might need to be investigated. Maybe the kernel module really does need updating in 8.04, your device is probably pretty new. It might be of some benefit to search the forum for threads about CDROMs not mounting or not working and see if any apply to your issue.
 
Sorry, I'm not helping, except to suggest you search, if I think of anything else I'll post back.
 
Ok, thanks.

---

### Post by dandnsmith on 2011-01-04
I think there's another oddity.
Those lines in syslog I would find more appropriate in dmesg, which is where they always appear in all the versions of linux I have used (not just ubuntu).

Any thoughts on that?
Is the kernel a special build?

---

### Post by xr4ti on 2011-01-04
> **dandnsmith said:**
> I think there's another oddity.
Those lines in syslog I would find more appropriate in dmesg, which is where they always appear in all the versions of linux I have used (not just ubuntu).
 
Any thoughts on that?
Is the kernel a special build?
 
No, not a special build.  Yes, you are correct about the syslog messages.  They are exactly identical to the dmesg output.  I don't have enough ubuntu experience, however,  to comment on that.

---

