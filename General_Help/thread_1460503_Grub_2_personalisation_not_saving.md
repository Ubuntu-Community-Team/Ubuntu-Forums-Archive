---
title: "Grub 2 personalisation not saving"
date: 2010-04-22
forum: General Help
---

### Post by oxf on 2010-04-22
I tried to change the default colours in the Grub 2 Boot loader following instructions in:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)   "Spash images and Theming"

Specifically colors are set by:
set color_normal=**black**/black
"set color_highlight=magenta/black"
in  [I][B]/etc/grub.d/05_debian_theme

I opened as root and edited this file but the changes done** seem to stick. It's still all black/white** when I boot.

Any ideas??
 [/B][/I]

---

### Post by drs305 on 2010-04-22
After you made the change, did you run "sudo update-grub" to add the changes to the grub.cfg file?

Take a look at the lines in /boot/grub/grub.cfg. These are mine. Note the first set in  conditional only applies if the background image is in use. Which of the two sets reflect the changes you made? Are you using the bg image in your file? Did it show the backgorund image being found in the terminal when you ran update-grub:
> 
if background_image /docs2/computer/backgrounds/grub.backgrounds/bg_earth.1024x768.scaled.png ; then
  set color_normal=light-gray/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi


If you aren't using a background image, you would need to make the change to the other set in 05_debian_theme.

---

### Post by oxf on 2010-04-22
> **drs305 said:**
> After you made the change, did you run "sudo update-grub" to add the changes to the grub.cfg file?

No I didn't, I'll try that! 
Interesting no mention of that in the grub 2 documentation? I may have missed it though as its late here. I'll take a detailed look in the morning.


Thanks.!.

---

### Post by drs305 on 2010-04-22
I added some more things to check in the previous post which you may not have seen.

I wrote the Grub 2 documentation. I reference the update-grub command requirement often in the doc but will make sure it's mentioned in the theming section as well.

---

### Post by oxf on 2010-04-22
> **drs305 said:**
> I added some more things to check in the previous post which you may not have seen.

I wrote the Grub 2 documentation. I reference the update-grub command requirement often in the doc but will make sure it's mentioned in the theming section as well.
 
Thanks! will go through it in detail in the morning and report back
...

---

### Post by 2hot6ft2 on 2010-04-22
> **oxf said:**
> 
Specifically colors are set by:
set color_normal=**black**/black
"set color_highlight=magenta/black"
in  [I][B]/etc/grub.d/05_debian_theme
 [/B][/I]
You made sure to make your changes to the second set like that, NOT the first set right?

I followed the guide in the help pages too and I would have sworn it said to run sudo update-grub. It's been a while since I did it though.

**By the way nice work on the help page for it drs305. It looks real good.**

Something else I had to play with a little was be sure to resize your picture to the resolution that grub will be.
I set my pictures to 800x600 and it stretched them off the screen until I went to
System > Administration > Startup Manager
and set it to 800x600 to match the pictures.
Now it looks great.

---

### Post by oxf on 2010-04-23
> **2hot6ft2 said:**
> You made sure to make your changes to the second set like that, NOT the first set right?

I followed the guide in the help pages too and I would have sworn it said to run sudo update-grub. It's been a while since I did it though.



Well I did the changes to the first set "mono theme" settings at the top of the file. Since I dont have a personalised splash image, just wanted to change the colours at this stage, thats how I read it. I assumed the section further down the file was if you had a spalsh image loaded. Can someone clarify please?

Yes you are correct "sudo update-grub is referenced there, I missed it! Thats what come of messing with things before bed!

---

### Post by drs305 on 2010-04-23
oxf,

You are correct that if there is no background image found G2 should use the mono theme settings. If you change those, have no background image, and run 'update-grub' the colors should show up as specified.

The lines in 05_debian_theme to set, without a background image, are approximately lines 18-19. After updating grub, you should see the new color settings in /boot/grub/grug.cfg starting at approximately line 65.

---

### Post by oxf on 2010-04-23
> **drs305 said:**
> oxf,

You are correct that if there is no background image found G2 should use the mono theme settings. If you change those, have no background image, and run 'update-grub' the colors should show up as specified.

The lines in 05_debian_theme to set, without a background image, are approximately lines 18-19. After updating grub, you should see the new color settings in /boot/grub/grug.cfg starting at approximately line 65.

OK Thanks!

---

### Post by oxf on 2010-04-23
One further question...

I made the changes and updated grub. I did this on my two PC's. All OK, except for one thing...

Normally, when you get the Grub if you press the arrow keys it changes the election and the countdown timer halts until you select which OS you want and hit enter. On my laptop this is just fine as before.

However, on my desktop when I press the arrow keys it just boots imediately into Ubuntu (the first option). Should I wish to boot the other OS or memtest I cant! 

Thoughts?

---

### Post by drs305 on 2010-04-23
> **oxf said:**
> However, on my desktop when I press the arrow keys it just boots imediately into Ubuntu (the first option). Should I wish to boot the other OS or memtest I cant! 

Thoughts?

I experienced this a few times but the behavior never lasted for more than a day or two. I never isolated the problem. 

I'll assume it's not just a coincidental timeout at about the same time as you try to press another key.  ;-)

One thing you might try is to press either "c" or "e" to change modes and hope that doesn't trigger a selection.  If it doesn't you could then press ESC and see if the menu selections are scrollable at that point. You could also try holding down the SHIFT key to interrupt things during the initial boot. 

These aren't solutions but as a workarounds they might provide some relief.

---

### Post by oxf on 2010-04-23
> **drs305 said:**
> I experienced this a few times but the behavior never lasted for more than a day or two. I never isolated the problem. 

I'll assume it's not just a coincidental timeout at about the same time as you try to press another key.  ;-)

One thing you might try is to press either "c" or "e" to change modes and hope that doesn't trigger a selection.  If it doesn't you could then press ESC and see if the menu selections are scrollable at that point. You could also try holding down the SHIFT key to interrupt things during the initial boot. 

These aren't solutions but as a workarounds they might provide some relief.

No not a time out!

Hmm.. well that's interesting.  This only started to happen after I set the colours and ran update-grub (and only on the desktop) 

I tried hittng "c" and that  did again trigger the first Ubuntu selection. So obviously "any key" to halt the countdown timer no longer worked. Thought I'd better try "e" and "shift" just to be thorough before I resorted to reinstalling Grub2. But "e" took me into menu and Esc back out to a scrollable selection. Tried "c" again, then Esc and scrollable. Then the up/down arrow keys and everything is now scrollable! Seems like hitting "c" fixed it.

Well thanks :)

---

### Post by oxf on 2010-04-23
Seems like I spoke to soon... The "c" or "e" route fixes it but -only- if I kill the power before the OS selection has booted. Then on reboot its scrollable.

However, if I let it boot up and then shut down in the normal way we are back to square one. I'll keep playing with it and  may try reinstalling Grub

---

### Post by drs305 on 2010-04-23
> **oxf said:**
> Seems like I spoke to soon... The "c" or "e" route fixes it but -only- if I kill the power before the OS selection has booted. Then on reboot its scrollable.

However, if I let it boot up and then shut down in the normal way we are back to square one. I'll keep playing with it and  may try reinstalling Grub

The key selections I described were only to get it working once - not a permanent fix. 

However, we did learn something. When you kill the power, it interrupts Grub and it is probably sending a "recordfail" message to grubenv. So if you are willing I'd like you to try this before you shut down normally the next time.

First, you can try setting the /etc/default/grub "GRUB_TIMEOUT=" value to -1
> 
GRUB_TIMEOUT=-1

Save the file, update grub and then reboot and see if the menu is halted and selectable.

If that doesn't work, try setting it directly in 00_header, generating the same input as you would get with a "recordfail" event:
```
gksu gedit /etc/grub.d/00_header
```
At the bottom, make the following changes:
Change:
> 
cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF

To:
> 
cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
[COLOR="DarkRed"]**  set timeout=-1**[/COLOR]
fi
EOF



In either case, save the changed file, update grub and then reboot and see if the menu is halted and selectable.

I would consider this a temporary fix to allow you to select a menu item during boot. We haven't found the solution as to what is causing the actual problem.

---

### Post by oxf on 2010-04-24
> **drs305 said:**
> 
First, you can try setting the /etc/default/grub "GRUB_TIMEOUT=" value to -1

Save the file, update grub and then reboot and see if the menu is halted and selectable. 
Still not scrollable! 

But when I then press enter for first selection (Ubuntu) I get the following error. This may or may not be related? as I've seen it every time I boot but flashes by so quickly I ignore it and never had any consequences (assumed it was a Bios bug which I had with 9.04 too)

> USplash Setting Mode 1152x864 failed
USplash using mode 1024x768 instead
General error mounting file systems
A maintainnce shell will now be started
Control D will terminate this shell and re-try
[ 7.4223328 Acer-wmi   No or unsupported WMI interface, unable to boot root


I then do Control D and it boots as normal

[/QUOTE]
If that doesn't work, try setting it directly in 00_header, generating the same input as you would get with a "recordfail" event:
```
gksu gedit /etc/grub.d/00_header
```At the bottom, make the following changes:
[/QUOTE]

This worked.

---

### Post by oxf on 2010-04-24
Uhmm what's happened?  :confused:

I decided to reverse the changes in 00_header and /etc/default/grub since booting into windows is not that important right now. i.e go back to my original 2 second timeout. Made the changes back and updated grub.

Now it boots almost instantaneously into first selection. I Verified timeout was 2 seconds and tried again. Same result.

I decided to reinstall grub completely as per your instructions in Doc as the colors are not really that big a deal if it causes problems. Updated grub. I still have the color settings I made and the instantaneous boot. So something outside of grub got changed?

---

### Post by drs305 on 2010-04-24
> **oxf said:**
> Uhmm what's happened?  :confused:

I decided to reinstall grub completely as per your instructions in Doc as the colors are not really that big a deal if it causes problems. Updated grub. I still have the color settings I made and the instantaneous boot. So something outside of grub got changed?

When you reinstalled G2 it probably isn't recognizing Windows. If it thinks there is only one OS it by default will not display the menu and boot directly to linux.

Often running "sudo update-grub" after an install will cause G2 to find Windows and add it to the menu. At that point the menu will display if the settings in /etc/default/grub are set correctly.

I'm off on vacation but wanted to try to get this settled before pulling the plug on the computer for a couple of weeks.

---

### Post by oxf on 2010-04-24
> **drs305 said:**
> When you reinstalled G2 it probably isn't recognizing Windows. If it thinks there is only one OS it by default will not display the menu and boot directly to linux.

Often running "sudo update-grub" after an install will cause G2 to find Windows and add it to the menu. At that point the menu will display if the settings in /etc/default/grub are set correctly.

I'm off on vacation but wanted to try to get this settled before pulling the plug on the computer for a couple of weeks.

Yes Grub was updated. Windows and the other options like memtest are diplayed, just very quickly. Instantaneous was perhaps the wrong description. It may be just a one second timeout but seems a lot less than one sec to me.

Have a good trip :)

---

### Post by oxf on 2010-04-29
> **drs305 said:**
> I experienced this a few times but the behavior never lasted for more than a day or two. I never isolated the problem. 



Well just FYI. I eventually gave up worrying about it on the basis I hardly ever boot the windows partition any more and if I install another Linux partiton I'll deal with it then.
The Issue persisted for a day or two but today  almost a week later I checked again. Just like you its now resolved and grub is back to its old self... Strange!   :)

---

### Post by oxf on 2010-06-02
Further about this little quirk. At the weekend I edited some entries on my grub menu, and ended by updating grub. Sure enough the "problem" reappeared again. I ignored it and just like before it seemed to resolve itself after about 24-48 hrs. 

I was not messing with the grub parameters as before so whatever is going on is being triggered by running "sudo update-grub"   which then resolves itself in a couple of days anyway..

---

