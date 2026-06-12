---
title: "Resolution issue with VGA splitter"
date: 2011-02-03
forum: General Help
---

### Post by nufan1121 on 2011-02-03
Hey guys and gals! Let me start off by apologizing if this is in the wrong section - trust me i have been scouring Ubuntu forums for the past 3-4 days straight and i have pretty much lost my sanity so forgive me if this is misplaced.

I'm running a Intel g31 chip set motherboard, and as far as i can tell have the correct drivers for special effects in compiz/making it a macbuntu etc. Over the past few nights i have battled with getting ubuntu back from being stuck in grub somehow we managed to get it into infra-something and it was possible to use again. Then i suffered the issue of windows 7 not letting me run the b****** OS due to a boot log error, but again that was fixed. Right now to the topic

I have a VGA splitter, a small Hansol h530 15" monitor, and a 40 " Samsung LCD HD tv (Which windows runs perfectly fine together with no resolution issues) and so does Ubuntu PROVIDING that i have the PC plugged straight into the monitor at first, and then only after Ubuntu has started up can i change everything back to going through the VGA splitter and just like magic! everything works fine.
This only becomes an issue when i restart my computer, then neither of the screens get past the ubuntu loading stage, not even if while its stuck there i proceed to change the cables back to step 1 wherein the computer is directly linked to the Hansol h530 once more, it just stays on the loading screen until i restart and then it goes back through the successful step 1.

Its a continuous albeit stressful situation i can tell you, and i have done my research to the extent of the xorg.conf file editing but to no avail including issues such as giving myself root privo and then trying to edit it and it not working after restart, also trying to rename the file but not being allowed to.

I'm at my wits end, and iv been a Ubuntu user for a long while, if it wasn't for my attachment to cubase i would of left windows a long time ago. But this whole resolution deal is draining my confidence in the OS as windows has no issue what so ever.

Maybe it's me? or maybe it's not possible? any help would be extremely appreciated and specs provided on request.

Hope you can help :cry:

~Lee

---

### Post by nufan1121 on 2011-02-04
Bump?

---

### Post by dcstar on 2011-02-05
> **nufan1121 said:**
> Bump?

Ubuntu tries to detect the monitor settings on boot up using EDID, you may want to create an xorg.conf file with this option disabled as it probably gets too confused with the splitter connected.

There are already numerous posts on the net for "Headless" boot ups for things like VNC without a monitor connected that will probably help.

---

### Post by nufan1121 on 2011-02-05
Hi dcstar, thanks for your response.

Being unsure what you meant by headless boot up i searched Google and could only understand that it;s a boot up without any hardware attached? forgive me if i'm mistaken on that topic but that's not what i'm hoping to achieve. 
I have tried editing the xorg.conf file before to avail as i can never seem to edit the code properly, or when i do it saves under a .conf1/2/3 save. I am not experienced when it comes to the editing or coding of protected files in linux. 

I am just a tad confused as to why it works fine after booting even when through the splitter, but will not boot while both are going through the splitter to start with.

Not to be spoon fed but could you give me some advice/help with either the process of and re coding of the xorg.conf file with the EDID disabled? I really wouldn't know where to start and tutorials i have read in the past of editing the file are always different and contain different ways/means to code it.

Thank you so much

~Lee

---

### Post by nufan1121 on 2011-02-05
Ok Since my last post i did some research, and found a good resolved thread on google from a guy stating the problem was in his /etc/default/grub file, so he edited it to include the intel chipset fix. I copied his information into my file by editing it, updated grub and did a restart to see if it was fixed.

Long story short, im now talking to you from windows =/. Ubuntu wont load graphicly, and instead offers me to login via command, so i do, then i recieve a message about checking my bios, along with a pre written script. I copy and paste the script and now recieve this message:

CPU is family 6, model 23 has NX capabilities but is unable to use those protective features because the bios is configured to disable.
Please enable

Wiki.ubuntu.com/security/CPUFeatures


I searched for a solution to this problem and found a code from someone:

Sudo rm /etc/update-motd.d/20/cpu-checker

This lead me into a blue command prompt where in i could refresh my grub loadings, so i did - this did not work.

On same page, i also checked packages for errors and fixed them - This also did not work.

Im even more stuck now i'v tried to solve my own problem. I need the 2 monitors to work, and windows is winning the battle of the best suited (for me) OS right now.

Someone please help me restore my faith in ubuntu!

Thanks

~Lee

---

### Post by dcstar on 2011-02-06
> **nufan1121 said:**
> 
.......
Not to be spoon fed but could you give me some advice/help with either the process of and re coding of the xorg.conf file with the EDID disabled? I really wouldn't know where to start and tutorials i have read in the past of editing the file are always different and contain different ways/means to code it.

Thank you so much

~Lee

[http://ubuntuforums.org/showpost.php?p=4563276&postcount=9](http://ubuntuforums.org/showpost.php?p=4563276&postcount=9)

```
sudo nano /etc/X11/xorg.conf
```

---

