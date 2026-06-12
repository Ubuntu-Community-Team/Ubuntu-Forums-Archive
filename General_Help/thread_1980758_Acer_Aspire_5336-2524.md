---
title: "Acer Aspire 5336-2524"
date: 2012-05-15
forum: General Help
---

### Post by mawil1013 on 2012-05-15
I can install latest Ubuntu, but the screen goes blank. I found this possible solution, but as a newby, it really doesn't help me.
First, how can I do this if I cannot see the screen and second, can someone walk me through the operation??


[http://askubuntu.com/questions/133894/ubuntu-12-04-backlight-problem-on-acer-aspire-5736z](http://askubuntu.com/questions/133894/ubuntu-12-04-backlight-problem-on-acer-aspire-5736z)

"As root edit /etc/default/grub
Change the line GRUB_CMDLINE_LINUX=""
by GRUB_CMDLINE_LINUX="acpi_osi=Linux"
save the file
and then sudo update-grub and reboot."

---

### Post by bryanl on 2012-05-16
First thing is to run a system to allow you to edit /etc/default/grub 

if you have a multi-boot setup then you should see the GRUB menu on boot. If you have only one bootable system on your machine, hold down the shift key during boot to bring up the boot menu (see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) )

There should be an option for a rescue system to allow you to boot to a menu where you can select a root command prompt. From there, you can proceed with the instruction.

If that doesn't work, then maybe a CD or USB boot of the distribution ISO can be used. The problem there is that the update-grub command gets a bit more complicated.

cd /etc/default, vi grub, scroll down to the end of the line specified, type "i" to insert text, type in the option specified, type <Esc> then 'ZZ' to write the file and exit. run update-grub and then reboot and see what happens.

I gotta' try this to see if my dual monitor laptop setup problem is fixed with this option ...

tried this and didn't get me past boot on my i3 laptop with external HDMI drive. rats. It'd be nice to use 12.04 on the laptop with an external monitor but that does not seem to be workable for my acer laptop. so far.

---

### Post by seabeepirate on 2012-11-15
Sorry, I know this is probably too late to help you, but I found this discussion while I was searching for a way to run dual display(stretched) on windows oddly enough. I also had an issue with the same laptop(Acer Aspire 5336-2524) and Ubuntu. I'm running Ubuntu Studio 12.04 now. The issue that I had was not that the screen shut off exactly, but that the backlight turns off which basically makes it impossible to see anything. I was able to get the backlight to turn back on(for each session) using the Fn keys to adjust the brightness. Try both up and down, that's Fn+Left Arrow or Fn+Right Arrow. Mine usually only turns on after I turn the brightness down but once it's on I can turn the brightness back up, strange right?

Before I upgraded to 12.04 I had a permanent solution but for the life of me I can't remember what it was, only that it had to do with the backlight and that I had to alter 2-3 different files to get the backlight to stay on after boot. I know this doesn't solve your problem, but it should at least point you in the right direction. Certainly try your link once you get the system to boot, I think the brightness keys should at least get your backlight to turn on so you can do that much. Also, if you're not worried about getting full performance out of your graphics card, the generic driver should run without a problem. I had a work around that involved modding the arguments in GRUB, which effectively caused the system to think it had an unknown graphics card and so it loaded the generic drivers instead of the proprietary drivers. Booted and ran just fine but I couldn't do anything with 3D.

---

