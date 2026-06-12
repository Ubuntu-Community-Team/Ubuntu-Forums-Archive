---
title: "Experienced ubuntu users help, including admins"
date: 2010-12-14
forum: General Help
---

### Post by mmsmc on 2010-12-14
You'll have to excuse my gross incompetence and ignorance with  everything Linux related and if you dare, hold my hand through this  process, but I'm in need of some help and this seems like a great place  to try and get some.

I have a Dell Mini 10v that I previously installed Ubuntu 10.04 to  without a problem. After I figured out how to do little things like  enable Java, I was able to run the one program I installed ubuntu for in  the first place. Everything was great, life was beautiful, my program  ran without giving me the constant BSOD that was the case when I was  running it on Windows...

That is until yesterday, when I booted up the laptop and interrupted the  boot process by holding down the power button to make it shut off (I  was having power problems and didn't know the computer was booting until  it was too late). Now it won't boot and gives me an error akin to this  (pulled from a web search):

 	Quote:
 	 	 		 			 				[LEFT][COLOR=#000000]mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _


Read more: [http://pinoy-computing-tips.blogspot...#ixzz17xc8jUSu]("http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html#ixzz17xc8jUSu")[/COLOR][/LEFT]
 			 		 	 	 
so naturally I prepared a USB drive with ubuntu and tried to boot  to it to run Terminal. Well, that doesn't work either. The BIOS sees the  usb drive and lets me choose to boot to it, but then it hangs at the  purple ubuntu screen and I can get nowhere with it.

I also tried booting to a osx usb drive and using terminal included  there, but the commands don't translate and another web search I tried  for similar help yielded no positive results.

Is there anything I can do? at this point I would just start over and  lose my data, but I can't even do that since I can't get it to boot to  the USB. And yes, I tried the USB drive on another computer and it  booted into Ubuntu just fine.

Theres no cd drive and no external cd drive so cant boot up by live cd

---

### Post by Rubi1200 on 2010-12-15
Depending on your graphics card, you may need to use one of the boot options to get the LiveUSB going.

I would try nomodeset first.

The error message probably indicates some kind of file-system damage (hard shutdowns usually never end well no matter what OS you use).

---

