---
title: "How to Change boot default in Ubuntu9.10"
date: 2009-11-26
forum: General Help
---

### Post by laughabc on 2009-11-26
I originally had windows7 and ubuntu jaunty installed in my laptop, after I upgraded jaunty to 9.10, I found out some problems in the system. So I formated the jaunty partition and did a clean install of 9.10 in it. Now the grub manu have ubuntu 9.10 as default and I want to set windows 7 as default.

I did some research and tried to chagne the default by Startup manager, but it does nothing. 

Then I read the Grub 2 Guide in this forum and saw this

[LIST]
[*]**GRUB_DEFAULT="xxxx"** - An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: *GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"*
[/LIST]

so I tried changing the[FONT=Arial Black][SIZE=1][COLOR=DarkRed]/etc/default/grub[/COLOR][/SIZE][/FONT]:
**GRUB_DEFAULT=0** 
into
**GRUB_DEFAULT="**Chainload into GRUB 2"(I also tried changing it into "windows 7 (loader) (on /dev/sda3)" because im not sure which one is the correct entry)
and then I do sudo update-grub and reboot. But it doesn't work, nothing had changed.

I have also tried changing the default number in /boot/grub/menu.lst into the number of the entry of my Windows but still doesn't work.

Any idea what i am missing or suggestion?

I am a newbie in both Ubuntu and grub, so please write something I can understand and in detail!

Thanks in advance

---

### Post by MaxIBoy on 2009-11-26
I think the config file in Grub2 is now /boot/grub/grub.cfg or similar, instead of /boot/grub/menu.lst (which might have been left behind from an old Grub-legacy installation, or you might actually not be using version 2.) I know most distros stick with Grub-legacy so far.

I know that in Grub-legacy, you just move your preferred default entry to the top of the list. Try editing menu.lst and doing that. (And if that doesn't do anything, then you actually are using Grub2, which doesn't use menu.lst anymore.)

If you are using Grub2, you're not actually supposed to edit the grub.cfg file. It is correct that you edit /etc/default/grub. However, the GRUB_DEFAULT setting expects a number, by default the first entry in the menu.

Look at your grub.cfg and see which option you want to be default. If it's the third one, for example, you set GRUB_DEFAULT to 2 (counting starts at zero.)

---

### Post by audiomick on 2009-11-26
> **MaxIBoy said:**
> I know most distros stick with Grub-legacy so far.



A clean install of Ubuntu 9.10 will have grub2, unless that has specifically been changed during the installation.

---

### Post by laughabc on 2009-11-27
Thank you guys for your help, I seem to figured out the problem now.

ok here is the reason why I got confused:

on the top of the boot screen when I boot my computer, it says the current grub version is 1.97Beta which is Grub2

but when I log into Linux, running
grub-install -v 
to check the grub version it says 0.97, which means what I am using is the Grub legacy.

I upgradu to Grub2 following the instroction here:
[https://help.ubuntu.com/community/Grub2#Installation](https://help.ubuntu.com/community/Grub2#Installation)
and now the startup manger is wroking(at least the default system option is). Problem solved

---

### Post by laughabc on 2009-11-27
> **audiomick said:**
> A clean install of Ubuntu 9.10 will have grub2, unless that has specifically been changed during the installation.

I guess mine is an early version of 9.10 as said in the Ubuntu documentation it doesn't have grub2 installed by default yet. I do notice that in one of the updates earlier, it prompt me to change to a newer version of grub, which I ignored.

---

