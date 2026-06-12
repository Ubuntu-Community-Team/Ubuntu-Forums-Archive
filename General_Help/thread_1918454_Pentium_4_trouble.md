---
title: "Pentium 4 trouble"
date: 2012-02-01
forum: General Help
---

### Post by dRounse on 2012-02-01
I am having trouble installing Mythbuntu on a computer with a Pentium 4 processor, i have it on Unetbootin and it boots Unetbootin and brings up the menu and I pressed try without installing that brought up just a list of actions the computer was trying to execute (thats what it looked like, im not sure the technical term) then it just stayed on that page, Im using 32-bit mythbuntu, I also tryied with 32-bit netinstall Ubuntu and that did not work either.... I'm stuck, so any help would be great, thanks

---

### Post by mastablasta on 2012-02-01
any error messages in the end of those "list of actions"? did you check the ISO if it downloaded well?

---

### Post by jonnyboysmithy on 2012-02-01
Try remake the liveusb. Mine didn't extract properly this morning ;).

---

### Post by dRounse on 2012-02-01
> **mastablasta said:**
> any error messages in the end of those "list of actions"? did you check the ISO if it downloaded well?

No there werent any messages, it hung on that page for over 15 minutes so i retried and it did the same thing, thats when i tried the ubuntu netinstall, also its from a school.... so i dont know if it has anything blocking it but i did get puppy linux on it about a month ago

---

### Post by mastablasta on 2012-02-02
ok. using the liveUSB try to use one of the boot options at the bottom (i think F6). 
 
nomodeset
acpi=off
xforcevesa
...
 
more on these here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sudodus on 2012-02-02
What happens if you select the ***default*** alternative in the unetbootin menu?

I know that some of other alternatives can be garbled, probably because unetbootin cannot quite manage all the alternatives made for a boot CD, but the default alternative usually starts a live session.

---

### Post by dRounse on 2012-02-02
[IMG]file:///home/david/Downloads/IMG_20120202_200846.jpg[/IMG]

I'm not sure if that worked but here is a picture of the screen

Sorry didnt work, its too long to type

---

### Post by dRounse on 2012-02-02
```
[4.043879] BUG: unable to handle kernel NULL pointer deference at 00000001
[1.043998] IP: [<f5077d20>] 0xf5077dif
[4.044022] *pde = 0000000
[4.044022] Oops: 0002 [#1] SMP
[4.044022] Modules linked in:
[4.044022] 
[4.044022] Pid: 1, comm: swapper Not tainted 3.0.0-12-generiic #20-Ubuntu Gateway       E-4100         /D865GLC
```

Theres the first half the rest have the [4.044022] so they must all be related but that portion seems to have the most info

---

### Post by sudodus on 2012-02-03
> **dRounse said:**
> ```
[4.043879] BUG: unable to handle kernel NULL pointer deference at 00000001
[1.043998] IP: [<f5077d20>] 0xf5077dif
[4.044022] *pde = 0000000
[4.044022] Oops: 0002 [#1] SMP
[4.044022] Modules linked in:
[4.044022] 
[4.044022] Pid: 1, comm: swapper Not tainted 3.0.0-12-generiic #20-Ubuntu Gateway       E-4100         /D865GLC
```

Theres the first half the rest have the [4.044022] so they must all be related but that portion seems to have the most info
I must admit I don't understand the output, but obviously you do not succeed. So I ask a few questions, and ***maybe your answers will help me or someone else understand*** what to do.

- Did you check your download with md5sum? Did you remake your install USB drive?

- Did you try
[FONT="Courier New"]nomodeset
 acpi=off
 xforcevesa
 ...[/FONT]
according to *mastablasta*'s suggestion? What happened?

- Have you installed Mythbuntu to another computer or downloaded another version of Mythbuntu? So that you know what should happen. For example: is there a live session, or does the install [try to] start directly?

If not, please try! Maybe if you have a computer with a CD/DVD drive, or you can borrow such a computer, try to make a boot CD and see how that works (without completing the installation)!

---

### Post by dRounse on 2012-02-03
> **sudodus said:**
> 
- Did you check your download with md5sum? Did you remake your install USB drive?


Yes, and I have used multiple distros, and flavors

> 
- Did you try
[FONT=Courier New]nomodeset
 acpi=off
 xforcevesa
 ...[/FONT]
according to *mastablasta*'s suggestion? What happened?


No, I don't really understand what i need to do there..

> 
- Have you installed Mythbuntu to another computer or downloaded another version of Mythbuntu? So that you know what should happen. For example: is there a live session, or does the install [try to] start directly?


Yes, well ive booted the usb on my regular desktop with no problems, it gives me the option to install or try live

> 
If not, please try! Maybe if you have a computer with a CD/DVD drive, or you can borrow such a computer, try to make a boot CD and see how that works (without completing the installation)!

I originally tried to use a CD but that didnt work so I went with USB



And last night I tried to boot 12.04, I was in the #Ubuntu chatroom and they said boot 12.04, but that didnt work but I got a message that said something like "No UI configuration" it was a little longer but i forget what it said.

---

### Post by dagroves on 2012-02-03
I have the same problem but I was installing regular Ubuntu. My computer was not booting the Linux 3.x kernel correctly. I cannot live book 11.04 or 11.10 of any of the *buntu family of distros (or any distro that uses the 3.x kernel). What I had to do was install Ubuntu 10.10 (in your case, Mythbuntu 10.10) then upgrade to 11.04 and upgrade again to 11.10, then when you boot, choose an old 2.x kernel in Grub. Then when you get to the desktop, open a terminal and execute this command 'sudo gedit (or whatever text editor you use) /etc/default/grub' without quotes or anything in the (). Then edit the line that says 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash', after quite and splash add this 'acpi=off' no quotes. Save the file and exit the text editor, then in the terminal type this: 'sudo update-grub' and then 'sudo reboot now' and then choose the 3.x kernel to boot into. It works for me. If you have any questions feel free to ask and I hope it all works out. It seems like a lot of trouble, and it is, but it was the only way I could get anything newer than 10.10 and the 3.x Kernel to run on my old Pentium 4 PC. Good luck!

---

### Post by dRounse on 2012-02-03
> **dagroves said:**
> I have the same problem but I was installing regular Ubuntu. My computer was not booting the Linux 3.x kernel correctly. I cannot live book 11.04 or 11.10 of any of the *buntu family of distros (or any distro that uses the 3.x kernel). What I had to do was install Ubuntu 10.10 (in your case, Mythbuntu 10.10) then upgrade to 11.04 and upgrade again to 11.10, then when you boot, choose an old 2.x kernel in Grub. Then when you get to the desktop, open a terminal and execute this command 'sudo gedit (or whatever text editor you use) /etc/default/grub' without quotes or anything in the (). Then edit the line that says 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash', after quite and splash add this 'acpi=off' no quotes. Save the file and exit the text editor, then in the terminal type this: 'sudo update-grub' and then 'sudo reboot now' and then choose the 3.x kernel to boot into. It works for me. If you have any questions feel free to ask and I hope it all works out. It seems like a lot of trouble, and it is, but it was the only way I could get anything newer than 10.10 and the 3.x Kernel to run on my old Pentium 4 PC. Good luck!
Wow thank you i'm going to try that right now.

---

### Post by dagroves on 2012-02-03
> **dRounse said:**
> Wow thank you i'm going to try that right now.
I hope it works! Please, let me know how it goes!

---

### Post by dRounse on 2012-02-03
> **dagroves said:**
> I hope it works! Please, let me know how it goes!

It worked, thank you

---

### Post by dagroves on 2012-02-03
> **dRounse said:**
> It worked, thank you
AWESOME!! So glad to hear it! You can now delete all the old kernels using a tool such as Ubuntu Tweak and enjoy your new system! Please do not forget to mark your thread as solved on your way out! 
David

---

### Post by sudodus on 2012-02-03
> **dagroves said:**
> I have the same problem but I was installing regular Ubuntu. My computer was not booting the Linux 3.x kernel correctly. I cannot live book 11.04 or 11.10 of any of the *buntu family of distros (or any distro that uses the 3.x kernel). What I had to do was install Ubuntu 10.10 (in your case, Mythbuntu 10.10) then upgrade to 11.04 and upgrade again to 11.10, then when you boot, [COLOR=Black]choose an old 2.x kernel in Grub[/COLOR]. Then when you get to the desktop, open a terminal and execute this command 'sudo gedit (or whatever text editor you use) /etc/default/grub' without quotes or anything in the (). Then edit the line that says 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash', after quite and splash add this 'acpi=off' no quotes. Save the file and exit the text editor, then in the terminal type this: 'sudo update-grub' and then 'sudo reboot now' and then choose the 3.x kernel to boot into. It works for me. If you have any questions feel free to ask and I hope it all works out. It seems like a lot of trouble, and it is, but it was the only way I could get anything newer than 10.10 and the 3.x Kernel to run on my old Pentium 4 PC. Good luck!

I think this tip is very valuable, because many of us still run P4 computers.

Thanks for sharing :KS

---

