---
title: "can't reach ubuntu"
date: 2012-04-23
forum: General Help
---

### Post by LEOXD on 2012-04-23
I had got Windows7+Trisquel installed previously. Than I saw, that Trisquel can't connect to the Internet for some reason, and overwrote the Trisquel-partition with ubuntu. But now I can't reach ubuntu, because I have still the Trisquel-GNU-GRUB, that only lists win7+trisquel. And Trisquel is messed up, because the files are overwritten as I said before. 
What can I do to delete the rest of Trisquel? Or at least get access to ubuntu? 
I don't have a Windows-installation-disc, because windows was pre-installed. So the "make all to windows and split up again"-thing doesn't work. Probably. 
I get the GRUB after booting before the windows-boot-screen.

Last option I can imagine is [DBAN]("http://dban.org/"), but...
I hope somebody of you have a better plan.

---

### Post by mick222 on 2012-04-23
Looks like ubuntu is either not properly installed or hasn't been detected by grub.How did you install Ubuntu and can you run it from live cd.

---

### Post by LEOXD on 2012-04-23
I can run it with Live-CD, I can even see the installed ubuntu-files with the Live-CD. Also installed ubuntu with the Live-CD. So it seems like it's the GRUB's fault. And now?

---

### Post by mick222 on 2012-04-23
you could try Rescatux, look here for instructions [http://www.webupd8.org/2011/02/live-cd-to-fix-restore-grub-and-grub2.html](http://www.webupd8.org/2011/02/live-cd-to-fix-restore-grub-and-grub2.html) .Or reinstall ubuntu from the live cd .Dban seems extreme as it would kill the windows install.

---

### Post by sanderj on 2012-04-23
> **LEOXD said:**
> I can run it with Live-CD, I can even see the installed ubuntu-files with the Live-CD. Also installed ubuntu with the Live-CD. So it seems like it's the GRUB's fault. And now?


Boot the live-cd and install again.

---

### Post by ajgreeny on 2012-04-23
You could also try simply reinstalling grub to the system's MBR again with the live CD.  See my grub2 links in signature for details, but make sure you have the correct version of live CD for the grub and ubuntu you are reinstalling, and finally ensure grub goes onto the MBR of a disk, not a partition, ie /dev/sda, **not** /dev/sda1 or /dev/sda2, etc etc.

Even if it does not work, you will have lost nothing.

---

### Post by LEOXD on 2012-04-24
the reinstall did it. OK. Thank you.

---

### Post by ajgreeny on 2012-04-24
> **LEOXD said:**
> the reinstall did it. OK. Thank you.
Reinstall of the whole OS, or just grub?

---

### Post by LEOXD on 2012-04-24
whole OS.

---

