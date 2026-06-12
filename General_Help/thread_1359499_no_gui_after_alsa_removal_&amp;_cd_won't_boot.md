---
title: "no gui after alsa removal &amp; cd won't boot"
date: 2009-12-19
forum: General Help
---

### Post by ajm1979 on 2009-12-19
I was running 8.04 on a lenovo n200 laptop. All fine but the sound wasn't working, from terminal executed the relevent sudo commands to remove then re-install ALSA.

Lost GUI when I re-booted. Found it was a known issue and have read every fix I can find.

The usual apt-get fixes will not work as no matter what I do I can't get a connection to any server.

I don't care about recovering the install, I had nothing to back-up as I use the laptop just for surfing and watching the odd movie.

I just want to install another version of Ubuntu or in fact any o/s but this is the problem I have.

Nothing will boot from the cd drive now. Yes I have gone to the boot menu and ensured that the cd/dvd drive is first in line in the boot menu.

I can't get Ubuntu Live CD to boot, I tried from GRUB too. I can't get Ultimate Boot CD or anything else to boot either.

All that happens is the laptop will insist on bringing me to the ubuntu login (non gui)
regardless of whether I am booting from the CD or from the Hard Drive.

I would re-format but I can't even manage to get to the DOS prompt.

I'm currently layed up with a fractured ankle and won't be able to go anywhere for 6 weeks and if I can't have access to the internet I might just have to rip my own eyes out with shards of my Live CD

Please, anyone, how can I just force a removal of this install and put something new on there????

Many thanks in advance,

Aj

---

### Post by john newbuntu on 2009-12-20
You mentioned that you get a console.  Could you try logging in and mounting the CD using the command 
mount /cdrom
or 
mount /media/cdrom

Actually could you try and start gdm from the console and see what you get:
sudo /etc/init.d/gdm start

The one other thing you could try and do is to see if you have an option in BIOS to autodetect the IDE devices.

---

