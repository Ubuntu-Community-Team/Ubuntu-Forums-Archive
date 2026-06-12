---
title: "Kernel Panic - What to do?  Where to look?"
date: 2009-09-24
forum: General Help
---

### Post by x C0MMAND0 x on 2009-09-24
I have been getting a "kernel panic" a few times a week now.  I believe that's what it is anyways.  My system is 100% unresponsive to every command and trick I know, and also the caps lock / num lock lights flash on and off.

It happens randomly, so I haven't been able to recognize a pattern at all.  Is there a place I should look in the event logs to see what the heck is going on?  I must admit I don't really have any clue what to look for in the event logs and what everything means.  Any help would be greatly appreciated.

---

### Post by ibuclaw on 2009-09-24
I won't really repeat what I said a moment ago twice, but if you could download + run the script in this post I made a few moments ago: [http://ubuntuforums.org/showpost.php?p=8001296&postcount=35](http://ubuntuforums.org/showpost.php?p=8001296&postcount=35)

Then attach the output file in your next post, I'll have a look and will try to point you in the right direction in terms of resolving/bug reporting.

Regards
Iain

---

### Post by x C0MMAND0 x on 2009-09-24
I'm not sure what output file you want...so I'll just attach what I think you need.  There were 2 output files, "dsdt.dsl" and "ubuntu-bug-report.log".  I attached the log, let me know if you need the other part.

I had to upload the archive it is a part of, because I can't directly upload the .log file.  Thank you very much for your help.

---

### Post by ibuclaw on 2009-09-26
It looks like there may be an issue with the clocksource linux is using.

When you reach the grub stage when booting your machine, press **Esc** to stop the countdown and highlight the boot option you use to boot Ubuntu and press **e**; you will be brought to a new menu listing. Look for **kernel** and press **e** again and then try adding one of the following to the end of the line.
[LIST=1]
[*]hpet=disable
[*]clocksource=jiffies
[*]clocksource=pit
[*]clocksource=tsc
[*]apicmaintimer
[*]nohpet
[/LIST]
Press **Enter** to apply the new parameter (changes are not saved), then press **b** to boot Ubuntu.

Work through that list to see if any one of those options works for you - don't try to use multiple options, just go through them one at a time - and if one appears to stop the issue, just add it to your defoptions list.
```
gksudo gedit /boot/grub/menu.lst
```
find the following:
> # defoptions=quiet splash
And append the option you used to resolve the issue to the end of it.

ie:
```
# defoptions=quiet splash **hpet=disable**
```
Save and quit, then run:
```
sudo update-grub
```
To make it permanent.

The above fix won't work in Karmic/Grub2.

Regards
Iain

---

