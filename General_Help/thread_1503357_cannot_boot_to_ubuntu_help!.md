---
title: "cannot boot to ubuntu help!"
date: 2010-06-06
forum: General Help
---

### Post by fazio93 on 2010-06-06
I have Vista 32bit dual booting with Ubuntu 10.04
I want Vista to be my default OS so I installed Start-Up Manager in Ubuntu and set Vista as the default OS and changed the timeout to 0 seconds. 

By doing this, I thought that it would always boot to Vista as if nothing else was installed (which is what I wanted it to act like) and then whenever I wanted to boot to Ubuntu I would hold down 'Shift' to load the Grub2 menu and select Ubuntu.

The problem is, every time I boot up the Grub menu won't load. I tried holding 'Shift' down, tapping repeatedly, but all that comes up is something like "Grub Menu...Loading" in the top left corner and then it boots to Vista. 

I just need a way to boot back to Ubuntu to change the timeout.

Please Help.
Thanks.

---

### Post by utnubuuser on 2010-06-06
tried "esc"?

I think I had a similar setup once, and it was a matter of using esc to access the menu, and then very quickly using the arrow keys to interupt the boot-loader. It's the arrow keys that stop the clock

---

### Post by insanity99 on 2010-06-06
welcome to ubuntu forums. i believe when it says 'grub loading' you press 'Esc'. i will look it up now.

EDIT: yes you want to press Esc, [https://help.ubuntu.com/community/BootOptions#Change Boot Options Temporarily For An Existing Installation](https://help.ubuntu.com/community/BootOptions#Change Boot Options Temporarily For An Existing Installation)

---

### Post by Leppie on 2010-06-06
have you tried both shift keys?
if it's not working you can always repair grub2 from a livecd.

---

### Post by Leppie on 2010-06-06
> **insanity99 said:**
> welcome to ubuntu forums. i believe when it says 'grub loading' you press 'Esc'. i will look it up now.

EDIT: yes you want to press Esc, [url]https://help.ubuntu.com/community/BootOptions#Change] Boot Options Temporarily For An Existing Installation[/url
i believe ESC is for grub legacy, grub2 uses the shift key (not sure why they changed this).

---

### Post by insanity99 on 2010-06-06
oh yes, your right.

---

### Post by fazio93 on 2010-06-06
I just installed 10.04 a few days ago. It installed GRUB v.1.98 (aka Grub2) so it should work with the shift button. Yes, I have tried using both shift buttons and I tried pressing 'esc' once I saw the "Grub...Loading". What am I doing wrong? When do I push the shift button down exactly? Right when I turn the PC on, when I see the bios, or after the bios?

So I can run the LiveCD of Ubuntu to repair the Grub menu? How?


Thanks.

---

### Post by Leppie on 2010-06-06
the shift button works for me (with timer set to 0), however as soon as the bios screen appears i have to press and hold the shift button as when the bios screen disappears it's already too late.

---

### Post by fazio93 on 2010-06-06
I booted off the LiveCD and used the terminal to edit /boot/grub/grub.cfg
I changed the timeout to 5.
When I rebooted, after the BIOS loaded, it stayed there for about 5 seconds, but the menu didn't appear.
?

---

### Post by Leppie on 2010-06-06
and pressing shift didn't bring up the menu either?

---

### Post by fazio93 on 2010-06-06
> **Leppie said:**
> and pressing shift didn't bring up the menu either?

nope.

i can't seem to get the menu to show. :-(

---

### Post by fazio93 on 2010-06-06
is there any way i can completely wipe/erase the grub install and  reinstall it?

---

### Post by fazio93 on 2010-06-06
After a couple hours of constant rebooting I finally solved it!

I completely wiped out the Grub2 bootloader in my mbr by running my vista repair disk (i used "bootrec.exe /fixmrb" in the command prompt, which re-wrote the windows bootloader).

Then I used this guide:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

I kind of tried a little of all of the 3 methods listed there, but the third method (CHROOT) I think did the trick.
When I rebooted, I held down shift. Like before, I saw "Grub" at the top left and even though the Grub menu wasn't displayed, I used the arrow keys to try and guess which one I was hitting. What do you know?

Ubuntu loads! I then reset the timeout to 10 seconds in the startup manager, rebooted, and the Grub Menu works like a charm.

Thanks everyone. :)

---

