---
title: "halt no longer powers down computer..."
date: 2006-06-02
forum: General Help
---

### Post by conro on 2006-06-02
Every since i upgraded to dapper, when i halt my compuer i have to manually turn off the power which was not the case in breezy.. I found this out the hardway yesterday when i tried to halt my laptop and threw it in my backpack while it was shutting down... When i took it out it was super hot, the battery was just about dead and it was still at the shutdown screen. The last line says, 'will now halt.'

does anyone know how i can get it to automatically powerdown at this point?

thanks!

---

### Post by Thomaseov on 2006-06-03
I have the same problem...has anyone figured this out?

---

### Post by lotv on 2006-06-03
same problem with desktop!

---

### Post by Lil_Eagle on 2006-06-03
Add me to the list.

In addition, my system freezes if I open a virtual terminal with <Alt><Ctrl><F2> for example and then go back to X with <Alt><Ctrl><F7>.

It is quite frustrating.  It sometimes happens as well when I try to end my session so I can log in as another user.

---

### Post by givré on 2006-06-03
Did you try a freash install, it resolve the problem of a lot of people

---

### Post by viciouslime on 2006-06-03
I have the same problem on a fresh install...

---

### Post by givré on 2006-06-03
If this happens even in a fresh install, without tweaking anything, fill a bug there [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)
and put here the adress of you bug so other people who have the same issue could add a comment

EDIT : It's like there is already a bug fill, [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

---

### Post by george_apan on 2006-06-04
Same thing here after a dist-upgrade. Any idea if and when this is going to be fixed?

---

### Post by Cartson on 2006-06-04
I have the same problem,too!
Help!

---

### Post by Peter76 on 2006-06-04
I had the same problem, think it has to do with with older hardware and the newer Dapper kernel.
To solve it, edit your /boot/grub/menu.lst and pass "acpi=force" and "lapic" to the standard kernel as arguments. Save the file, run: sudo update-grub, and reboot. It should shutdown and restart fine now.

Here's my entry in my /boot/grub/menu.lst ( it's near the end of the file )  :

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash acpi=force lapic
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

Good luck, and hope this helps.

PS: It is possible you only need to pass one of the options; there's a bell ringing somewhere that I needed one of them for something else, but not sure anymore. Try and post your results, so others can benefit as well.

---

### Post by gabrielp on 2006-06-04
[QUOTE=Peter76]I had the same problem, think it has to do with with older hardware and the newer Dapper kernel.
To solve it, edit your /boot/grub/menu.lst and pass "acpi=force" and "lapic" to the standard kernel as arguments. Save the file, run: sudo update-grub, and reboot. It should shutdown and restart fine now.

Here's my entry in my /boot/grub/menu.lst ( it's near the end of the file )  :

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash acpi=force lapic
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

Good luck, and hope this helps.

PS: It is possible you only need to pass one of the options; there's a bell ringing somewhere that I needed one of them for something else, but not sure anymore. Try and post your results, so others can benefit as well.[/QUOTE]

Sorry ,but does not help

---

### Post by jolinux on 2006-06-04
Yes, works fine. Thx. But... This works if you dont run this command:

[QUOTE=Peter76]Save the file, run: sudo update-grub[/QUOTE]

Save the file and reboot directly.

---

### Post by halfvolle melk on 2006-06-05
I can't get it to work here. I tried with and without update-grub. /var/log/dmesg says "ACPI: Looking for DSDT ... not found!", could that have anything to do with it?

---

### Post by Peter76 on 2006-06-05
Got this feeling my solution only works with older hardware.... And some Bios settings Can all the persons who tried this post their hardware specs? Maybe something to file a bug about....

---

### Post by halfvolle melk on 2006-06-05
I tried it on a L440GX+.

---

### Post by Revan on 2006-06-08
[QUOTE=Peter76]I had the same problem, think it has to do with with older hardware and the newer Dapper kernel.
To solve it, edit your /boot/grub/menu.lst and pass "acpi=force" and "lapic" to the standard kernel as arguments. Save the file, run: sudo update-grub, and reboot. It should shutdown and restart fine now.

Here's my entry in my /boot/grub/menu.lst ( it's near the end of the file )  :

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash acpi=force lapic
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

Good luck, and hope this helps.

PS: It is possible you only need to pass one of the options; there's a bell ringing somewhere that I needed one of them for something else, but not sure anymore. Try and post your results, so others can benefit as well.[/QUOTE]

Worked for me, thank you very much!

(ASUS P5GD2 Premium motherboard)

PS What is "acpi=force lapic" exactly doing, btw?

---

### Post by sidd-tx on 2006-07-15
adding "acpi=force lapic" to my kernel line in grub fixed my 3 laptops.

Toshiba Satellite 4090 X DVD

Toshiba Portege 7200 Series

Toshiba Portege 7020CT

Thanks.
Sidd....

---

### Post by squee on 2006-07-18
You might need to replace some of the lines in the command with the ones that are in the menu.lst already. That command seems to be personal to him. Mine is different: 


title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro quiet splash acpi=force lapic
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot


I've added his extra code but changed the  2.6.15-26-686. Hope this helps! ;)

---

### Post by Culito on 2006-07-18
My comp shut itself down until I messed with some startup settings with sysv-rc-conf.  Now it doesn't shut off.  And I forgot the settings.  Oh, well, I'll figure it out sometime.

---

### Post by JamesB on 2006-07-20
I've got a Asus A8Jc and have the same problem, I tried the above with no joy, any have an answer for newer hardware?

James

---

### Post by JamesB on 2006-07-21
Up-date...
The Asus will shut down properly when running on batteries but not when plugged into the mains...
Ho Humm

James

---

### Post by betty on 2006-08-20
The lapic fix worked for me.  I've got an older slot a k7 mobo.

---

### Post by zek725 on 2006-10-31
> **Peter76 said:**
> I had the same problem, think it has to do with with older hardware and the newer Dapper kernel.
To solve it, edit your /boot/grub/menu.lst and pass "acpi=force" and "lapic" to the standard kernel as arguments. Save the file, run: sudo update-grub, and reboot. It should shutdown and restart fine now.

Here's my entry in my /boot/grub/menu.lst ( it's near the end of the file )  :

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash acpi=force lapic
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

Good luck, and hope this helps.

PS: It is possible you only need to pass one of the options; there's a bell ringing somewhere that I needed one of them for something else, but not sure anymore. Try and post your results, so others can benefit as well.

Worked fine! I had same problem with Edgy--halt no longer shutdowns. Reboot works fine but the shutdown is the problem. That happened when I installed Edgy from scratch. It did not happen when I update from Dapper to Edgy.

> **Peter76 said:**
> acpi=force lapic

What does those mean?

---

### Post by paul6 on 2006-11-07
I'm still having this problem. Adding "acpi=force" worked in Dapper, but turns my CPU fan off in Edgy. Adding "acpi=off" does not seem to fix anything.

From reading the bug reports on launchpad this appears to be some sort of kernal problem or acpi conflict. Any help is appreciated, as this bug is *damn* annoying.

---

### Post by Ennead on 2006-11-14
I have this problem too.  The "acpi=force lapic" didn't help.  I've tried several other suggestions from other threads in the Forum, but so far nothing has worked.  One of my pet peeves about MSWindows was that, sooner or later, the power-down feature always seemed to fail.  So this is a bit of a disappointment, but all in all, I'd still much rather have Ubuntu Linux than the other stuff.

Thanks to all who've helped with this problem.  I'm not giving up, but I am moving forward.;)

---

### Post by JamesB on 2006-11-15
I've managed to fix this in Dapper. I was running a usb dvb-t tv thingy which prevented the laptop from powering down. If I remove the dvb-t it powers down sweet. So the problem could be kernel thing or a firmware thing, or both. Either way, it was the dvb-t that caused the porblem. Hope this helps someone...

---

