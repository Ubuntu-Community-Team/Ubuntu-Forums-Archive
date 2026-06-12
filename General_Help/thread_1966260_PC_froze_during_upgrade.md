---
title: "PC froze during upgrade"
date: 2012-04-26
forum: General Help
---

### Post by TimEnid on 2012-04-26
I had to shut it down, now it won't start up properly and I was in the midst of upgrading. Not sure what to do now. PC will not boot into Ubuntu. And I have no network connection in safe mode. Any help would be appreciated.

Also, I rebooted the PC and when i select 3.2.0-24 generic and all I get is a flashing cursor. I reinstalled grub thru the CD and still have the issue.

---

### Post by techsupport on 2012-04-26
> **TimEnid said:**
> I had to shut it down, now it won't start up properly and I was in the midst of upgrading. Not sure what to do now. PC will not boot into Ubuntu. And I have no network connection in safe mode. Any help would be appreciated.

Also, I rebooted the PC and when i select 3.2.0-24 generic and all I get is a flashing cursor. I reinstalled grub thru the CD and still have the issue.

I would probably use the alternative installation disc for 12.04 and see if it couldn't be repaired with that.

---

### Post by PD808 on 2012-04-26
Unfortunately I think your only option would be to re-install Ubuntu. I would make a LiveCD of Xubuntu or something and mount your hard drive while in the LiveCD (you can test the system without installing) and backup any important files to another storage medium (such as a USB drive). Once you have it backed up, you can wipe & reinstall. I'm sure there's other computers you could use to make the LiveCD or LiveUSB. Maybe if not, you could borrow someones?

---

### Post by TimEnid on 2012-04-27
> **techsupport said:**
> I would probably use the alternative installation disc for 12.04 and see if it couldn't be repaired with that.

is there an option to repair? i would prefer this method.

> **PD808 said:**
> Unfortunately I think your only option would be to re-install Ubuntu. I would make a LiveCD of Xubuntu or something and mount your hard drive while in the LiveCD (you can test the system without installing) and backup any important files to another storage medium (such as a USB drive). Once you have it backed up, you can wipe & reinstall. I'm sure there's other computers you could use to make the LiveCD or LiveUSB. Maybe if not, you could borrow someones?


i was trying to avoid that. but i guess it wont be such a bad idea to start from scratch. I back up my apps my regularly, so restoring them wont be an issues. 

thanks for the suggestions.

---

### Post by matt_symes on 2012-04-27
Hi

Maybe you could boot into a liveCD/USB, chroot into the broken install and fix the upgrade that way.

Kind regards

---

### Post by codingman on 2012-04-27
If I were you I would re-install from scratch;it's safer, and you might have lost some big chunky root files during the upgrade, and repairing is not such a good idea for computer help.

---

### Post by TimEnid on 2012-04-27
> **matt_symes said:**
> Hi

Maybe you could boot into a liveCD/USB, chroot into the broken install and fix the upgrade that way.

Kind regards

> **codingman said:**
> If I were you I would re-install from scratch;it's safer, and you might have lost some big chunky root files during the upgrade, and repairing is not such a good idea for computer help.


I think i will go this route. I already copied my Home folder to an external HD. Might as well start from scratch.

---

### Post by matt_symes on 2012-04-27
Hi

> I think i will go this route. I already copied my Home folder to an external HD. Might as well start from scratch.

That is the best way as there is no guarantee of success with trying to fix a broken upgrade.

You obviously can attempt it but it is always best to install a fresh version than upgrade anyway.

The quickest way is to backup home and start again. 

Might i suggest you make some partition(s) for you documents, downloads, videos, pictures etc and mount them at boot time. Map them to your home folder using symlinks.

If you need to reinstall then you just reinstall to your root/home partition, edit fstab to mount the partition(s) at boot time again and recreate the symlinks.

Just a thought and it's your call.

Kind regards

---

### Post by techsupport on 2012-04-27
> **matt_symes said:**
> The quickest way is to backup home and start again. 


Also using a post install guide helps too:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by TimEnid on 2012-04-27
> **matt_symes said:**
> Hi



That is the best way as there is no guarantee of success with trying to fix a broken upgrade.

You obviously can attempt it but it is always best to install a fresh version than upgrade anyway.

The quickest way is to backup home and start again. 

Might i suggest you make some partition(s) for you documents, downloads, videos, pictures etc and mount them at boot time. Map them to your home folder using symlinks.

If you need to reinstall then you just reinstall to your root/home partition, edit fstab to mount the partition(s) at boot time again and recreate the symlinks.

Just a thought and it's your call.

Kind regards

> **techsupport said:**
> Also using a post install guide helps too:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Thanks for the advice.

---

