---
title: "Urgent- Need help removing grub - USB installation gone wrong"
date: 2010-02-09
forum: General Help
---

### Post by 3XCALlBUR on 2010-02-09
Let me set the scene- A friend told me how you could install Ubuntu onto a USB flash drive and carry around your own OS in you pocket. So as soon as I got home, I ran Ubuntu as a live CD, and when it asked me where I wanted to install it, I selected my 16gb flash drive. It installed fine and then I re booted my laptop. After the normal ASUS screen flashed past, I expected Windows boot loader to pop up as usual (long story short, I didnt uninstall Vista properly so whenever I booted WBL popped up and asked which one I wanted to run -even though it ran Win7 nomatter what) but instead grub (grub 2 beta 4 from memory) pops up and gives me a selection- Ubuntu at the top, some disk checkers in the middle and Windows 7 boot loader at the bottom. If I select  Ubuntu, It loads Ubuntu from my USB. I I pick Win7 loader, *then *it runs boot loader as usual. If there is no USB in the port, it will say something about "Grub rescue failed - drive does not exist" (that is not exactly right). 
 
NOTES: After the abomination on the USB, I decided that I still wanted Ubuntu on my actual computer. This time I ran the installer from in Windows and it worked fine. This next part is quite Interesting. I told you before that if I select Win 7 loader from the first Grub, WBL (windows boot loader) pops up as usual. after I installed Ubuntu _in_ Windows there is a ubuntu option in the WBL. If I select it, another grub pops up. I do not have a problem with this- it is the first, USB grub that I want gone.

I really do not want to have to put my USB in every time I boot, or wait for grub to load. I want to get rid of grub at the very start, so that I can get to WBL without the USB inserted or grub popping up. Although I would prefer it if neither Ubuntu got deleted (USB or Internal), if they must go, I will remove them.

OK thanks guys for any time you put into helping me, all of it is greatly appreciated.
Nick B

PS. When giving me instructions, please note that while I am quite proficient with Windows, I am a complete noob with Ubuntu so if the instructions are even a little bit vague, a little explanation here and there would not hurt. 

_Important:_ If you can not or dont want to post, you can contact me at [EMAIL="nbarsha01@gmail.com"]nbarsha01@gmail.com[/EMAIL] - feel free to request a little more info if it will help or you are just curious.

Also sorry for the size of this post- It got a little bit out of hand but I cannot decide what to remove.
Thanks Again!!
Nick

---

### Post by warfacegod on 2010-02-09
> After the abomination on the USB

I'm guessing you should have clicked the Advanced button during the install process and told it to install GRUB to the USB drive.

This link *might* help.

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

