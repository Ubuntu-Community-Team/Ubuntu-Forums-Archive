---
title: "Precise xswat nvidia driver 304.43 big problem"
date: 2012-08-28
forum: General Help
---

### Post by Cavsfan on 2012-08-28
Well, I installed the xswat PPA in Quantal and the latest driver 304.43 which just came out yesterday and is now in the xswat repository.
So, I figured I could install it in Precise as well. WRONG.

I installed the PPA and Key and then the nvidia-current module which was the 304.43 driver.
Rebooted and had a black screen. Luckily I multi-boot so I was able to look at some things.
I had nvidia-current-upgrades installed version 295.49 before this.
Rebooted and got into recovery mode. Had to select Network first, then root shell.
I entered **sudo apt-get purge nvidia-current** and when it was removed, I entered **sudo reboot**.
I booted back into Precise and 295.49 was still there! :D

Definitely did not want to have to do another clean install and am happy I got Precise back.

Not sure if I did anything wrong. Maybe I was supposed to purge nvidia-current-updates or purge nvidia* before installing nvidia-current. 
But, that may have resulted in requiring a clean install.

Anyway I am throwing this out there in case any one else has the same issue.
In Precise, I am staying away from the xswat ppa.

---

### Post by dino99 on 2012-08-28
you need to make your choice of nvidia-current-updates or nvidia-current, not both indeed. ):P

---

### Post by Cavsfan on 2012-08-28
> **dino99 said:**
> you need to make your choice of nvidia-current-updates or nvidia-current, not both indeed. ):P

So, what exactly should I have done differently?

---

### Post by Dr.Paneas on 2012-08-29
Just in case, feel free to give a try [using my script]("http://ubuntuxtreme.com/howto/how-to-install-nvidia-304-43-with-one-click/") and let me know if it works for you :)

---

### Post by Cavsfan on 2012-08-31
D'oh! I removed nvidia-current-updates via Synaptic and installed nvidia current. Wondered why conky didn't display GPU version 304.43 or the temperature.

Removed and re-installed nvidia-settings and problem solved.
You were correct dino99. Just figured by installing one it would remove the other.
You live and learn...

):P  :guitar:

---

### Post by bogan on 2012-08-31
Hi!,** Cavsfan**,

On my computer nvidia 304.43, downloaded from nvidia.com runs sweetly on Precise, both 12.04 & 12.0-4.1 but not when downloaded from XSwat as nvidia-current.

But then I have never found the Xswat drivers work on my set-up since the 295.40 catastrophe, so I dont trust it.

Running  nvidia-installer -f, or sh NVIDIA.xx.xx.xxx.run -f does un-install any existing nvidia driver - or tries to - whereas with nvidia-current you have to deactivate or remove --purge the previous version  - whatever its name - before installing another, whether from  a PPA, with Additional Drivers, or Synaptic.

Chao!,** bogan**.

---

### Post by Cavsfan on 2012-09-04
> **bogan said:**
> Hi!,** Cavsfan**,

On my computer nvidia 304.43, downloaded from nvidia.com runs sweetly on Precise, both 12.04 & 12.0-4.1 but not when downloaded from XSwat as nvidia-current.

But then I have never found the Xswat drivers work on my set-up since the 295.40 catastrophe, so I dont trust it.

Running  nvidia-installer -f, or sh NVIDIA.xx.xx.xxx.run -f does un-install any existing nvidia driver - or tries to - whereas with nvidia-current you have to deactivate or remove --purge the previous version  - whatever its name - before installing another, whether from  a PPA, with Additional Drivers, or Synaptic.

Chao!,** bogan**.

Thanks bogan!
I'm just going to stick with the nvidia-current that is in the repositories. I borked a couple of partitions and have 
spent the last couple of days re-installing Precise and Quantal. I tried using the xswat ppa in Precise and ended up 
installing it again. Precise sure is slow until you get that nvidia-current driver loaded!
So I guess I too am not going to mess with the xswat ppa any more.

---

### Post by Joherrer on 2012-09-22
> **Dr.Paneas said:**
> Just in case, feel free to give a try [using my script]("http://ubuntuxtreme.com/howto/how-to-install-nvidia-304-43-with-one-click/") and let me know if it works for you :)

How can I do that without GUI, just tty interface???

---

### Post by Cavsfan on 2012-09-22
> **Joherrer said:**
> How can I do that without GUI, just tty interface???

This thread is solved. You should open up a new thread as you will probably get more attention that way.

---

