---
title: "Resolution reverts after Shut Down/Restart"
date: 2010-08-02
forum: General Help
---

### Post by SkulblakaSama on 2010-08-02
Hello again,

My preferred resolution is 1152 x 864, unfortunately it reverts to a different resolution and I have to manually change the resolution through the nvidia control panel after each restart session. 

Help would be appreciated. 

Thanks :)

---

### Post by prodigy_ on 2010-08-02
Not a proper solution, but as a quick and dirty hack, you can try to add a launcher with ```
xrandr -s 1152x864
``` command to your Startup Applications.

---

### Post by SkulblakaSama on 2010-08-02
I forgot to add, my graphic card does not support "Monitor" in the preferences tab.

---

### Post by SkulblakaSama on 2010-08-02
> **prodigy_ said:**
> Not a proper solution, but as a quick and dirty hack, you can try to add a launcher with ```
xrandr -s 1152x864
``` command to your Startup Applications.

Like a start up application? Would Ubuntu already start in 1152 x 864 or would it change once that "hack" starts running?

---

### Post by prodigy_ on 2010-08-02
I guess it'll change (if this method will work at all).

---

### Post by SkulblakaSama on 2010-08-02
> **prodigy_ said:**
> I guess it'll change (if this method will work at all).

Is there a different method perhaps? I really like to keep things tidy. ;) 

Thanks for your effort.

---

### Post by Cavsfan on 2010-08-02
This fixed it for me:

gksu gedit /etc/grub.d/00_header

and look to see if it contains "set gfxpayload=keep"
It is down a ways in the file, but look for this:

```
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  [COLOR=Red]set gfxpayload=keep[/COLOR]
```If you do not see gfxpayload=keep, add it where it is above.
Then enter "sudo update-grub" and reboot.

Have you set your resolution in /etc/default/grub  ?
You can set it to your native monitor's resolution with this command 
"gksu gedit /etc/default/grub"

Mine looks like this:  GRUB_GFXMODE=1920x1200x32
Just make sure there is no # to the left of it.

To see what your native resolution is or what resolutions are supported by your monitor,
when on the grub2 screen enter "c" to open up a command line and enter vbeinfo.
This will display all modes your monitor will support.

But, unless it has been fixed in the latest GRUB2 update the "set gfxpayload=keep" above should do the trick.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> This fixed it for me:

gksu gedit /etc/grub.d/00_header

and look to see if it contains "set gfxpayload=keep"
It is down a ways in the file, but look for this:

```
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  [COLOR=Red]set gfxpayload=keep[/COLOR]
```If you do not see gfxpayload=keep, add it where it is above.
Then enter "sudo update-grub" and reboot.

Have you set your resolution in /etc/default/grub  ?
You can set it to your native monitor's resolution with this command 
"gksu gedit /etc/default/grub"

Mine looks like this:  GRUB_GFXMODE=1920x1200x32
Just make sure there is no # to the left of it.

To see what your native resolution is or what resolutions are supported by your monitor,
when on the grub2 screen enter "c" to open up a command line and enter vbeinfo.
This will display all modes your monitor will support.

But, unless it has been fixed in the latest GRUB2 update the "set gfxpayload=keep" above should do the trick.

"set gfxpayload=keep" Didn't work, here's how it looks like for mine. 

if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  set gfxpayload=keep
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}

I added "set gfxpayload=keep" as you can see, but it didn't work, I'll make another attempt.

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> "set gfxpayload=keep" Didn't work, here's how it looks like for mine. 

if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  set gfxpayload=keep
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}

I added "set gfxpayload=keep" as you can see, but it didn't work, I'll make another attempt.


Forgot to mention did you enter "sudo update-grub" after the change to make it "stick"?
That is required.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> Forgot to mention did you enter "sudo update-grub" after the change to make it "stick"?
That is required.

Yes, I did that, without success. :(

---

### Post by Cavsfan on 2010-08-02
I don't think I am going in the right direction to help you.
You should probably submit this error on this thread [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Drs305 has a tutorial about grub issues and he knows a lot about it.
He will be able to sort it out. I tried.

I have created a tutorial on making a custome grub2 screen that is maintenance free if you're interested after you get this problem fixed.

Drs305 is logged on, so maybe he can fix you up.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> I don't think I am going in the right direction to help you.
You should probably submit this error on this thread [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Drs305 has a tutorial about grub issues and he knows a lot about it.
He will be able to sort it out. I tried.

I have created a tutorial on making a custome grub2 screen that is maintenance free if you're interested after you get this problem fixed.

Drs305 is logged on, so maybe he can fix you up.

Thank you for your assistance.

---

### Post by Cavsfan on 2010-08-02
> **SkulblakaSama said:**
> Thank you for your assistance.

You are very welcome! I am sorry if I wasted your time, but I thought for sure I could help, but I am sure **Drs305** will be able to and sometimes **Ranch Hand** helps on there too.
Between the two, you will be in good hands.

After you get that all sorted out and want to make your grub2 screen look like a wallpaper and have it be maintenance free, 
feel free to check out my tutorial [U][http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)
[/U]You won't have to update grub everytime a new kernel is installed. The only time you 
would have to mess with it is if GRUB2 is updated and the changes affect my changes.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> You are very welcome! I am sorry if I wasted your time, but I thought for sure I could help, but I am sure **Drs305** will be able to and sometimes **Ranch Hand** helps on there too.
Between the two, you will be in good hands.

After you get that all sorted out and want to make your grub2 screen look like a wallpaper and have it be maintenance free, 
feel free to check out my tutorial [U][http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)
[/U]You won't have to update grub everytime a new kernel is installed. The only time you 
would have to mess with it is if GRUB2 is updated and the changes affect my changes.

I've already did the part with custom wallpaper, I'll need to reboot to see how it looks. It's a great post. 

I'll be going onto the "maintenance free" part. I'll post any questions on there. :popcorn:

---

### Post by Cavsfan on 2010-08-02
I forgot to ask you if you went into System > Administration > Hardware Drivers and looked there for your issue.
I have an NVIDIA GeForce 9800 GT and when I first installed it was not on the recommended driver. Check that out. 
I put mine on the recommended driver and rebooted. Maybe that'll fix your problem.

---

### Post by SkulblakaSama on 2010-08-02
> **Cavsfan said:**
> I forgot to ask you if you went into System > Administration > Hardware Drivers and looked there for your issue.
I have an NVIDIA GeForce 9800 GT and when I first installed it was not on the recommended driver. Check that out. 
I put mine on the recommended driver and rebooted. Maybe that'll fix your problem.
Well, I have 2 graphic drivers listed there, I had a different version but now switched to a current version. But the problem still persists.

---

### Post by Cavsfan on 2010-08-03
> **SkulblakaSama said:**
> Well, I have 2 graphic drivers listed there, I had a different version but now switched to a current version. But the problem still persists.

As long as you are using the recommended version and still have the problem, hopefully **Drs305** can fix you up. I seen where you posted on his thread.

I thought maybe using the recommended driver would fix the problem.

---

### Post by SkulblakaSama on 2010-08-03
> **Cavsfan said:**
> As long as you are using the recommended version and still have the problem, hopefully **Drs305** can fix you up. I seen where you posted on his thread.

I thought maybe using the recommended driver would fix the problem.

Well, I was on a Recommended driver.

---

### Post by sydbat on 2010-08-03
> **SkulblakaSama said:**
> Hello again,

My preferred resolution is 1152 x 864, unfortunately it reverts to a different resolution and I have to manually change the resolution through the nvidia control panel after each restart session. 

Help would be appreciated. 

Thanks :)This is what I had to do - go into your nVidia settings (System > Administration > nVidia X Server Settings) and choose your resolution. THEN "Save to X Configuration File"...it should bring up an "Authentication" box asking for your password. This should save your settings properly.

As I say, it worked for me.

EDIT - Also try opening the nVidia settings via the terminal with "gksudo nvidia-settings". This will work if my first solution does not.

---

### Post by SkulblakaSama on 2010-08-03
> **sydbat said:**
> This is what I had to do - go into your nVidia settings (System > Administration > nVidia X Server Settings) and choose your resolution. THEN "Save to X Configuration File"...it should bring up an "Authentication" box asking for your password. This should save your settings properly.

As I say, it worked for me.

EDIT - Also try opening the nVidia settings via the terminal with "gksudo nvidia-settings". This will work if my first solution does not.

Well, I tried "Save to X Configuration File" but it says "Failed to Parse Existing X config File '/etc/X11/xorg.conf'!" 

After that, I'm given an option to save, which I did. Now to reboot...

---

### Post by SkulblakaSama on 2010-08-03
> **sydbat said:**
> This is what I had to do - go into your nVidia settings (System > Administration > nVidia X Server Settings) and choose your resolution. THEN "Save to X Configuration File"...it should bring up an "Authentication" box asking for your password. This should save your settings properly.

As I say, it worked for me.

EDIT - Also try opening the nVidia settings via the terminal with "gksudo nvidia-settings". This will work if my first solution does not.

It's hard to believe that I didn't do that earlier, this "X Configuration File" probably didn't exist so I had to save it. 

Now I boot into my preferred resolution, thank you for your assistance! :D

---

### Post by Cavsfan on 2010-08-03
> **SkulblakaSama said:**
> Well, I tried "Save to X Configuration File" but it says "Failed to Parse Existing X config File '/etc/X11/xorg.conf'!" 

After that, I'm given an option to save, which I did. Now to reboot...

> **SkulblakaSama said:**
> It's hard to believe that I didn't do that earlier, this "X Configuration File" probably didn't exist so I had to save it. 

Now I boot into my preferred resolution, thank you for your assistance! :D

> **sydbat said:**
> This is what I had to do - go into your nVidia settings (System > Administration > nVidia X Server Settings) and choose your resolution. THEN "Save to X Configuration File"...it should bring up an "Authentication" box asking for your password. This should save your settings properly.

As I say, it worked for me.

EDIT - Also try opening the nVidia settings via the terminal with "gksudo nvidia-settings". This will work if my first solution does not.

Great! This forum is great as there are a lot of helpful people on here!                                         
Someone always has an answer.

---

### Post by py8elo on 2010-08-04
Hi all,
I have the same problem but I cant get a solution to this issue...
I already has tryed all the tips I found on the forums but no success...
I use the Gforce 8400GS card with the latest Nvidia driver running on Ubuntu 10.04 LTS...
Can somebody help me please???

Thanks in advance and Best Regards,

Silva.
PY8ELO

---

### Post by Cavsfan on 2010-08-04
> **py8elo said:**
> Hi all,
I have the same problem but I cant get a solution to this issue...
I already has tryed all the tips I found on the forums but no success...
I use the Gforce 8400GS card with the latest Nvidia driver running on Ubuntu 10.04 LTS...
Can somebody help me please???

Thanks in advance and Best Regards,

Silva.
PY8ELO

You should probably go back to page two where **sydbat** posted about the nVidia X Server Settings and start from there. 
Your problem most probably has something to do with that.

If that doesn't solve your problem, you will need to start your own thread as this one has been marked solved.

---

### Post by py8elo on 2010-08-05
Hi Cavsfan,
Tnx for your reply...
I will try it rigth now and back to post the results...

EDIT:
I am sri...
Do not work here...
EDIT:
Solved at 06/08/2010 with help from another Brazilian guy.

Best Regards,

Silva.
PY8ELO

---

