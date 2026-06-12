---
title: "Ubuntu is Half Dead"
date: 2006-06-13
forum: General Help
---

### Post by souteneur3190 on 2006-06-13
First off I would like to say go slow with your eplanations.

Before the Problem:

I had two Hard Drives one was 20Gb.  I attempted to install dapper in a stupid way and my xserver crashed, but that isnt important.  Anyway I ditched the 20 gig.  The ohter was a 200Gb.  I used the 200gb and installed dapper the proper way everything was going fine until my dad asked me if i could have the 20gig I wasnt using.

The Problem:

I took it out and GRUB did not load on the only hardrive left...the screen is just black with a little (-) in the corner.  I think Grub is the Problem.

Where Im at Now: 

I took my 20gig back and installed it on my brothers computer sicne i fried my cd rom drive.  I get some errors of course but after reconfiguring xorg i was able to get to the fourms.  I am able to still browse my 200gig from here

My Question:

Is the Problem GRUB?  If so is there a way i can manually install grub onto that harddrive?

---

### Post by zxee on 2006-06-13
Were these drives master and slave on the same ide channel? You can't remove either without it causing problems with bios-which has little to do with grub since the bios is now confused. If that's not the problem please specify how your drive(s) are connected i.e. IDE, SATA, and the drive order.

---

### Post by souteneur3190 on 2006-06-13
my 200gig is master
my 20 gig is slave

and when grub for 20gig launches it doesnt give me the option to to boot from the 200gb even tho i can clearly see ubuntu is installed when i browse it from the 20gig

---

### Post by souteneur3190 on 2006-06-13
can i just replace everyfolder from the 200gig HD to the 20gig HD so i can have all my settings and try to mount my 200gig from there?

---

### Post by caldevil on 2006-06-13
Why don't you try adding a menu entry for 200gig HD installed ubuntu?

---

### Post by zxee on 2006-06-13
[QUOTE=souteneur3190]my 200gig is master
my 20 gig is slave

and when grub for 20gig launches it doesnt give me the option to to boot from the 200gb even tho i can clearly see ubuntu is installed when i browse it from the 20gig[/QUOTE]

You're reading the master drive from the slave? What is installed on the 20GB drive? Anyway caldevil is correct if you have a ubuntu install on the 20GB slave drive you can edit /boot/grub/menu.lst. 
I don't know if you want to do this but you can also sudo chroot to the partition holding the install on the 200GB drive and go into grub (just typing grub from the chroot environment should get the grub prompt (grub>) then you can type: find /bootgrub/stage1 then setup the partition  found from the previous command.
If you need more info let the forum know.

---

### Post by souteneur3190 on 2006-06-13
there is nothing in my boot folder

---

### Post by ihavenoname on 2006-06-13
well,  if you can get to ur 200gig hard drive to start, I would install grub (if it is not installed) and then do a sudo grub-install /dev/hda (where /dev/hda is your 200gig hard drive) this last step would point grub to look in your 200gig harddrive for the /boot/grub folder if thats is not installed then either reinstall grub or you could try coping it from your old hard drive to your new one.

---

