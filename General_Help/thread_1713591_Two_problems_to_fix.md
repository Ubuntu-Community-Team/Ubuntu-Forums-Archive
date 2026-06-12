---
title: "Two problems to fix"
date: 2011-03-24
forum: General Help
---

### Post by magodiafano on 2011-03-24
Hello I have two problems which I can't solve.

1) when I install ubuntu's updates, the dual boot (when I choose between ubuntu o vista) changes... in particular new equal entries to enter in ubuntu are created!! so in the dual boot there are around 10 entries to enter in ubuntu all equal each others!!!they are really useless!! what's the reason of that? it could be the start-up manager I installed to control the dual boot?

2) when I enter in ubuntu when my laptop is not plugged in the current, the luminosity is low. The same, for example is in window, but differently in vista in the moment I plug the current the luminosity turns up. 
How could I change the luminosity in ubuntu?

---

### Post by Another Monkey on 2011-03-24
1) Probably new Kernel versions (an example of the erroneous entries would help).  Log into the most recent and use synaptic to remove the older kernel versions.  There should be plenty of threads showing how to do that ("linux-headers" etc)
**WARNING: [COLOR="Red"]DO NOT[/COLOR]** delete your current kernel!  You will be totally screwed on next boot!

2) Depends on your laptop and how well it is supported - the laptop brightness buttons might be supported.  Also check the power management settings.  If I were you, when running on batteries I would keep the brightness down to preserve battery power.

---

### Post by grahammechanical on 2011-03-24
With Linux the operating system (the kernel) is improved a little bit at a time. These kernel images are indeed all different. We do not have to wait years for the next Windows to be released and then wait months for the first service pack and the second service pack. Our operating system is being developed all the time. Each step in the development has its own code number. This helps the developers identify which modifications to examine if they get reports of an upgrade causing problems.

I use Grub Customizer. Its let you hide some of the options in the Grub menu. You can simplify the menu. It does other things as well. It is in the Ubuntu Software Centre.

Regards.

---

### Post by magodiafano on 2011-03-24
2) the problem is that I wanna keep the brightness down when I am running with the battery but not when I plug the current. Unluckly the button of the brightness does not work with my laptop! so is there an application or a way to control the brightness?? it is very boring to reboot everytime I start ubuntu with the battery...

---

### Post by plucky on 2011-03-25
I don't know if this will help you,but there is an applet that you can add to the panel for adjusting panel brightness.

Right click on the top panel and select **Add to Panel**.From the list select "Brightness Applet".

You might have to reboot.

Good Luck

---

