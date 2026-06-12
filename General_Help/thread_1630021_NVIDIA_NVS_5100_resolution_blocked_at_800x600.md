---
title: "NVIDIA NVS 5100 resolution blocked at 800x600"
date: 2010-11-24
forum: General Help
---

### Post by PABlanche on 2010-11-24
Hi there,
 
I installed Ubuntu 10.10 64 bits on a HP Elitebook 8540p with a NVIDIA NVS 5100 graphic card.
 
Initially, [SIZE=2][FONT=Arial]the computer did not boot correctly and was stuck with the following error message:[/FONT][/SIZE]
[FONT=Arial][ 6.484165] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid[/FONT]
 
[FONT=Arial][SIZE=2]I found the solution on a forum ([/SIZE][/FONT][[FONT=Arial][SIZE=2][COLOR=#800080]http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/[/COLOR][/SIZE][/FONT]]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")[SIZE=2][FONT=Arial]):[/FONT][/SIZE]
[SIZE=2][FONT=Arial]and correct the problem by [/FONT][/SIZE][FONT=Arial]editing Grub with nomodeset:[/FONT]
[FONT=Arial][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/FONT][/FONT]
[FONT=Arial][FONT=Arial]Then update it by: [FONT=Arial]sudo update-grub.[/FONT][/FONT][/FONT]

[FONT=Arial][FONT=Arial][FONT=Arial]Now Ubuntu boots but the screen resolution is 800x600 instead of 1600x900 and I can not change it.[/FONT][/FONT][/FONT]

[FONT=Arial][FONT=Arial][FONT=Arial]Note that I had the 1600x900 resolution before updating the Grub file but it was not stable: went back to the "Pointer to BIT loadval table invalid" when restarted.[/FONT][/FONT][/FONT]

[FONT=Arial][FONT=Arial][FONT=Arial]Any help is welcome.[/FONT][/FONT][/FONT]
[FONT=Arial][FONT=Arial][FONT=Arial]Thanks[/FONT]
[FONT=Arial]
[/FONT][/FONT][/FONT]

---

### Post by PABlanche on 2010-11-24
I found the solution:  the correct Nvidia driver was not installed. 
Système ->administration->additional driver
 
Resolution is 1600x900 now

---

