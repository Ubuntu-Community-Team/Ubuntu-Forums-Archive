---
title: "Will reinstalling ubuntu delete my files? If so how can I get my files?"
date: 2009-08-28
forum: General Help
---

### Post by infocom on 2009-08-28
I installed Webmin and Virtualmin to create vhosts for new sites I am developing. They didn't work I got forbidden message I just could not fix. So I uninstalled them and things started to go wrong. My ubuntu now does not start up at all,  hanging on some startup processes, some kernal log daemon or something. 

I thought I'd just reinstall after using live cd to copy files to USB. But it won't allow me to read my files. It states input/output error. So I can't copy them to any other media.  

So can I repair/reinstall ubuntu without overwriting any files?

If not does anyone know I how can read my files using live cd or something else to back them up to USB or email them to me or something. Thanks.

---

### Post by rajeev1204 on 2009-08-28
> **infocom said:**
> I installed Webmin and Virtualmin to create vhosts for new sites I am developing. They didn't work I got forbidden message I just could not fix. So I uninstalled them and things started to go wrong. My ubuntu now does not start up at all,  hanging on some startup processes, some kernal log daemon or something. 

I thought I'd just reinstall after using live cd to copy files to USB. But it won't allow me to read my files. It states input/output error. So I can't copy them to any other media.  

So can I repair/reinstall ubuntu without overwriting any files?

If not does anyone know I how can read my files using live cd or something else to back them up to USB or email them to me or something. Thanks.

Reinstalling ubuntu will delete your files.If you are having trouble reading your files on hard drive with live cd,maybe its a HDD problem.

Please try using another live cd and see if you can acess your files.

---

### Post by infocom on 2009-08-28
I thought maybe it was a permissions issue what with livecd running as different user. I could not access folders from live cd so use terminal as root to change permissions then I could see them. But a copy in terminal as root stated an input/output error when trying to copy to destop or USB.

I think I'll try installing ubuntu again on a new partition and see if I can get files from old partition that way. Always seems easier reinstalling than trying to fix problems :)

---

### Post by infocom on 2009-08-29
Well it turned out permissions were wrong for /var/ and /home/myuser/. As per this thread I have explained the problem: [http://ubuntuforums.org/showthread.php?p=7865287](http://ubuntuforums.org/showthread.php?p=7865287). So HDD and LiveCD do not have an issue, it was permissions wrong which must have messed up accessing the files from LiveCD or Windows.

---

