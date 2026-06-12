---
title: "Command to &quot;reset&quot; Grub?"
date: 2011-07-30
forum: General Help
---

### Post by alohakrakadoa on 2011-07-30
Aloha Ubuntu-Community,

for hours I'm looking for a GRUB-command which fixes a problem with my new Ubuntu 11.04 installation (dual Boot on a 64bit system). 8-10 seconds after booting my Desktop gets "frozen", so I found the boot option "noapic=off", which seemed to be the command I was looking for. After testing it on the manual way I changed GRUB_CMDLINE_LINUX_DEFAULT&#8203;="quiet splash" (in the grub.cfg file) to "noapic=off"... but now, after selecting my Ubuntu version via GRUB I only get thousands of lines of text, but no Ubuntu desktop xD

Now the question: Is there any possibility (/command) to change GRUB to its previous settings, so that I can look for other ways how to solve the problem I described above?!

If you need any hardware/report information, feel free to ask!

thx in advance!

---

### Post by drs305 on 2011-07-30
During boot, if you don't see the Grub menu, hold down the SHIFT key. 

That should display the menu. Hightlight the option you want, then press 'e' to edit the entry.

Use the cursors to move to the 'linux' line and use the DEL key to remove whatever part of the entry is causing the problem.

Press CTRL-x to boot.

Once booted, edit the /etc/default/grub file and update-grub to make the changes permanent.

---

### Post by alohakrakadoa on 2011-07-30
okay I've expressed myself wrong: I CAN open Grub and I CAN edit the boot options- but when I change "noapic=off" back to "quiet splash", Ubuntu won't start as it has done before I changed the grub.cfg o_O  
Moreover I get the purple background of Ubuntu, but then nothing happens... and I can swear there was more code in the boot-options-editor before I deleted the quiet splash option - that is why I would like to undo the changes I made before in my Ubuntu... strange thing ;)

---

### Post by PIDGINZ on 2011-07-30
Maybe boot from a live cd? That'll let you change the file, but I'm not sure if it'll do anything as you need to run update-grub after editing that, correct?

---

### Post by drs305 on 2011-07-30
Did you have the 'nomodeset' option in your 'linux' line? Some users need that to get graphics until they add their video card driver.

You can get the original Grub 2 files back by chrooting into your installation from a LiveCD, then purging/reinstalling (see my signature line) but that won't solve things if you had a 'special' kernel option set which enabled the system to boot properly.

---

### Post by mikejonesey on 2011-07-30
examples on net say kernal line should be like;

kernel /vmlinuz-2.6.23.1 ro root=/dev/sda9 rhgb quiet noapci
or
kernel /vmlinuz-2.6.23.1 ro root=/dev/sda9 rhgb quiet

not
kernel /vmlinuz-2.6.23.1 ro root=/dev/sda9 rhgb quiet noapci=off

maybe this will help?

---

### Post by alohakrakadoa on 2011-07-30
thx guys; I will try out those tips tomorrow... always had some troubles with my LiveCD, so I'll need to get a new one soon ;)

---

