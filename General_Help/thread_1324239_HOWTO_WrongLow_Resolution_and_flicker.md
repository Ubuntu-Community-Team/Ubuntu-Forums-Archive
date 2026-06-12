---
title: "HOWTO: Wrong/Low Resolution and flicker"
date: 2009-11-12
forum: General Help
---

### Post by Giblet5 on 2009-11-12
The Xorg server - the code that provides a graphic display - is very good about determining what an attached monitor can do. There are limitations.

This HOWTO explains one process for obtaining a rock-solid graphics screen within the constraints of your hardware's abilities. There are many other ways to do this.

**Overview of the problem:**
[INDENT]When Xorg starts, it tries to figure out what kind of monitor you have via [DDC/CI]("http://en.wikipedia.org/wiki/Display_Data_Channel") and [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data") protocols. If your monitor and cabling are first-rate, you will never need to care about any of this. (Yay!)

If not, Xorg will pick a "safe" [VESA]("http://en.wikipedia.org/wiki/VESA") resolution and use that: probably not at all what you expected, and not likely to be satisfactory. (Grr.)

Lucky for us all, Xorg is highly configurable and it's very easy to get the exact resolution(s) that you want, deserve, and yes, paid-for with your invested time.[/INDENT]

**Warning:** If you are terrified by a Linux command line, at least TRY to follow this procedure. It won't hurt you and it will help.

Still with me? Then let's proceed:


**Step #1: What kind of monitor do you have? What are its capabilities? What is its maximum resolution?**

[INDENT]Virtually every monitor vendor will publish the specifications for their products on the web. You can find them if you just look but first, you'll need the Vendor Name and Model of that monitor. It will be printed on a plate or tag, glued, screwed, or riveted to the back, top, bottom, or side of your monitor. Go look for it now. Write that information down and keep it handy.[/INDENT]

**Step #2: Fetch your specs.**

[INDENT]Bring up a browser window and search for that model eg, 'dell 3007wfphc'.

Look for any site with details and specifications; the vendor's site is best, but most review sites will provide specifications too.

Ideally, you will find the "Horizontal Sync" *range*, expressed in kilohertz (KHz or khz), and the "Vertical Refresh" *range*, expressed in hertz (Hz).

If you found that, write it down like: ```
HorizSync 49.31 - 98.71
VertRefresh 60
```
and proceed to **Step #4**.

If not, then look for the "Maximum Resolution". This will be listed as something like "[COLOR="DarkRed"]2560[/COLOR] x [COLOR="Green"]1600[/COLOR] at [COLOR="Blue"]60[/COLOR]Hz". Write that down.[/INDENT]

**Step #3: Calculate the frequencies from the specified resolution.**

[INDENT]Open a terminal window (Applications -> Accessories -> Terminal) and enter ```
cvt [COLOR="DarkRed"]2560[/COLOR] [COLOR="Green"]1600[/COLOR] [COLOR="Blue"]60[/COLOR]
```

Hit Enter. This will output the following ```
[COLOR="DimGray"]# 2560x1600[/COLOR] **59.99** [COLOR="DimGray"]Hz (CVT 4.10MA) hsync:[/COLOR] **99.46** [COLOR="DimGray"]kHz; pclk: 348.50 MHz
Modeline "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync[/COLOR]
```

Aha! The vertical refresh will be exactly 59.99Hz and the horizontal sync will be 99.46KHz. Write it down as:

```
HorizSync 99.46
VertRefresh 59.99
```[/INDENT]

**Step #4: Create a basic xorg.conf**

[INDENT]Write the following commands down on paper because we're going to turn off the GUI and run a few commands from the console.

Flip to the text console via Ctrl+Alt+F1 and log in.

Execute these commands: ```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo /etc/init.d/gdm start ; exit
```
(ignore any notices about the "new" way of starting/stopping services - those "new" ways work, and so does this way, but this way works on all releases)

You're back at the GUI login screen, so log in and bring up the rest of these directions.[/INDENT]

**Step #5: Edit the basic configuration.**

[INDENT]Edit the new configuration by opening a terminal window and running the following command:
```
sudo gedit xorg.conf.new
```

Scroll down to the entry ```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
```

Add lines after the Identifier label to include the values you found (or calculated). The entry for that Dell monitor will look like: ```
Section "Monitor"
        Identifier   "Monitor0"
        [B]HorizSync    49.31 - 98.71
        VertRefresh  60.0
[/B]        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
```

Note: If you appreciate details, fill in the VendorName and ModelName values (within quotes) like ```
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    49.31 - 98.71
        VertRefresh  60.0
        VendorName   "Dell"
        ModelName    "3007WFP-HC"
EndSection
```[/INDENT]

**Step #6: Save the new configuration.**

[INDENT]Save that file. Then click File -> Save As (in gedit) and save the file as /etc/X11/xorg.conf then exit gedit.

Now, you have a new Xorg configuration installed where Xorg can see it, and you have a backup in your home folder.
[/INDENT]
**Step #7: Restart X and test.**

[INDENT]In the terminal window, enter ```
sudo /etc/init.d/gdm restart
```

You'll be logged off and the login screen should appear a few seconds later at full resolution. Congratulations, you have just done what your graphics card tried to do, but failed.[/INDENT]

------

**YIKES**: If the screen goes black and stays that way, then you have either not provided the correct information for your monitor or your graphics card cannot run that monitor at these frequencies. Here's how you get back to low-res graphics mode:

Flip to the console via Ctrl+Alt+F1 and log in. Run these commands: ```
sudo rm -f /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart ; exit
```

Now you can start over from **Step #1**, and find YOUR monitor's specifications. If you're very sure you have the correct numbers, then it is possible that your graphics card can't operate at the required frequencies. Replace it.

--

For further information on xorg.conf, bring up a terminal window and run ```
man xorg.conf
```

For further information on the Xorg server, bring up a terminal window and run ```
man X
```

Comments are always welcome.

---

### Post by joe2005 on 2009-11-20
THanks for the excellent guide With its help I am able to configure my screen resolution in ubuntu 9.10 satisfactorily.

---

### Post by Grenage on 2009-11-27
Excellent guide, Giblet5.

---

### Post by dracoalutusvulpes on 2009-11-28
I followed you very easy guide and when i was done and restarted i had a problem. The screen was flickering and my keyboard when i typed was all out of whack. what did i do wrong. i am gunna try to reinstall again and try once more. Any answers would be grand. Thanks.

NVM. I realized that i had inverted the variables. I put the horizontal for the vertical. it doesn't seem to like that apparently. Thanks for your amazing guide again.

---

### Post by thomas9459 on 2009-11-29
Help! When I used the first command in step 4, my computer went into a full screen terminal with black background that I can't get out of and when I did the gedit command in step 5 it gives me a warning cannot open display. Please help!

---

### Post by jquilaton on 2009-11-30
Thanks... Newbie here!!! Works fine for me... I have a sis mirage 3 graphics card ang it works fine...
Excellent..., Giblet5

---

### Post by AmateurDev on 2009-12-01
I tried this, but knowing me, I probably messed something up. I have a Dell E773c monitor, the specs of which are located here: [http://support.dell.com/support/edocs/monitors/e773c/EN/ug/about.htm#Specifications](http://support.dell.com/support/edocs/monitors/e773c/EN/ug/about.htm#Specifications).
I entered this:
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    67.68
        VertRefresh  74.79
        VendorName   "Dell"
        ModelName    "E773c"
EndSectionI did not know how to find the range for HorizSync that you did, so I just ran
cvt 1154 864 75 and used those numbers. When I try to restart the GUI, a message pops up that says:
(EE) open /dev/fb0: No such file or directory exists.
(EE) Screen(s) found, but none have a usable configuration.

I'm not sure what I did wrong. Can you help? Thanks in advance.

---

### Post by AmateurDev on 2009-12-01
> Help! When I used the first command in step 4, my computer went into a full screen terminal with black background that I can't get out of and when I did the gedit command in step 5 it gives me a warning cannot open display. Please help!
The black screen is supposed to come up. You have to run the rest of the commands in Step #4 before moving onto Step #5. Alternatively, you can run:
sudo /etc/init.d/gdm stop
Then, after the black screen comes up, run
sudo X -configure
Now do Step #5, but change gedit to nano. After you save xorg.conf.new, run
cp /home/elijah/xorg.cong.new /etc/X11/xorg.conf
Now do Step #7 and this should work.

---

### Post by kismet77 on 2009-12-19
Thank yo so much Giblet5!

I had tried so many things to solve my problem. Then I read your post & followed your instructions.

Godbless!

---

### Post by kwanbis on 2009-12-19
Thanks for the guide, but it is not working for me.

The first thing is that if i go by my monitor specifications, it says: 

Synchronization
Resolution: 2048 X 1152@60Hz
Horizontal: 30 ~ 75 kHz
Vertical:   56 ~ 61 Hz

if i do the cvt i get: 

~$ cvt 2048 1152
# 2048x1152 59.90 Hz (CVT 2.36M9) hsync: 71.58 kHz; pclk: 197.00 MHz
Modeline "2048x1152_60.00"  197.00  2048 2184 2400 2752  1152 1155 1160 1195 -hsync +vsync

Horizontal 71.49
Vertical   59.83

Anyway, no matter what i try:

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    30-75
        VertRefresh  61.0
	VendorName   "Samsung"
	ModelName    "2343nwx"
EndSection

OR

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    71.49
        VertRefresh  59.83
	VendorName   "Samsung"
	ModelName    "2343nwx"
EndSection

I only get 1024x768, or a black screen.

Any ideas/help?

---

### Post by Silvestro Fantacci on 2009-12-28
> **kwanbis said:**
> 

Vertical   59.83

Shouldn't that be 59.90?

> **kwanbis said:**
> 

Horizontal: 30 ~ 75 kHz
Vertical:   56 ~ 61 Hz

What if you try:

HorizSync    30 - 75
VertRefresh  56 - 61

---

### Post by Beastlicker on 2009-12-30
I could only get one number for my Horizontal Sync Rate

```
Section "Monitor"
    Identifier   "Monitor0"
        HorizSync    55.93
        VertRefresh  59.89
    VendorName   "Acer"
    ModelName    "AL1916W"
```Actually, I looked at another forum site and found out that the horizontal sync is 30-82. I tried that, and still no luck.

And it can't be my video card, seeing how it is very modern and runs fine on windows.

---

### Post by kwanbis on 2009-12-30
> **Silvestro Fantacci said:**
> Shouldn't that be 59.90?

What if you try:

HorizSync    30 - 75
VertRefresh  56 - 61
Thanks.

I finally solved it by moving to fedora.

I still think it could be related to how i installed.

I installed ubuntu with the external monitor connected.

But i installed fedora using only the internal monitor.

---

### Post by cavalete on 2009-12-30
I just wanted to say thanks for the information!

This has helped me to restore resolution of my monitor to 1440 x 900

Best wishes


My post requesting help is at:

[http://ubuntuforums.org/showthread.php?p=8583688#post8583688](http://ubuntuforums.org/showthread.php?p=8583688#post8583688)

---

### Post by Onimishra on 2009-12-30
I hoped this would work, but *sigh* still no good.

Got
Ubuntu is running in low-graphics mode
(EE) open /dev/fb0: No such file or directory
(EE) Screen(s) found, but none have a usable configuration

This is something you know off?

---

### Post by Beastlicker on 2009-12-30
> **Onimishra said:**
> I hoped this would work, but *sigh* still no good.

Got
Ubuntu is running in low-graphics mode
(EE) open /dev/fb0: No such file or directory
(EE) Screen(s) found, but none have a usable configuration

This is something you know off?

I am getting the exact same error as you are, and I have no clue what's going on.

But I am able to log in without safe graphics mode, but if I do get into safe graphics, my resolution is higher.

---

### Post by Beastlicker on 2009-12-31
Bump...Anyone know a fix for the problem that Onimishra and I are having?

---

### Post by munnster on 2009-12-31
Thank you SO much Giblet5 for helping me fix my screw up!! I'm saving the link to the page in case I need it again. :P

---

### Post by iamme4eva on 2010-01-05
Fantastic guide, thanks! Followed to the letter, now have 1360x768 on my 42 inch tv, rather than 800x600. More realistic! :-). Running Ubuntu 9.10.
 
Nick.

---

### Post by jwalantsoneji on 2010-01-08
Thanks it worked great for my monitor HCM582.
Well, when I reached to step#3, the monitor section already had ranges of horizsync and vertrefresh given there. So, no changes were required in that .conf file. Followed the rest of the steps to reach to the complete restore to original screen resolution.

Thanks a lot.

---

### Post by jjinco33 on 2010-01-11
Great guide. Fixed my resolution problem with my Dell E153fp monitor. :P

---

### Post by sthames on 2010-01-17
Thank you! this work awesome it was great cause i went from 800 x 600 to 1400 x 1050. Talk about a change.

---

### Post by Tourdog on 2010-01-17
Giblet5,

I had such high hopes that this one would do the job?!  Not!   I still have to do the dozen key-strokes to get my screen on 1280x 1024.   It still comes up at 800x 600.

I have spent many many hours/ days trying all the offerings on the Forum including scripts but to no avail.  My Nvidia 6150Le will go up to 1920 by 1080 but of course my Samsung SyncMaster  931bf (19") flat panel can go to 1280 x 1024.   I used the specs given by Reviews:/.cnet.com.    They show the vertical sync. rate as 75.0 hz and Horizontal sync rate at 81.0 khz

Any ideas:   I'm using the 185 driver provided by Hardware Ubuntu.

You wrote up an excellent how-to..................  what is it with these Nvidia's and 9.10
kernel 2.6 31-18.

---

### Post by rotex13 on 2010-03-13
> **Giblet5 said:**
> The Xorg server - the code that provides a graphic display - is very good about determining what an attached monitor can do. There are limitations.

This HOWTO explains one process for obtaining a rock-solid graphics screen within the constraints of your hardware's abilities. There are many other ways to do this.

**Overview of the problem:**[INDENT]When Xorg starts, it tries to figure out what kind of monitor you have via [DDC/CI]("http://en.wikipedia.org/wiki/Display_Data_Channel") and [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data") protocols. If your monitor and cabling are first-rate, you will never need to care about any of this. (Yay!)

If not, Xorg will pick a "safe" [VESA]("http://en.wikipedia.org/wiki/VESA") resolution and use that: probably not at all what you expected, and not likely to be satisfactory. (Grr.)

Lucky for us all, Xorg is highly configurable and it's very easy to get the exact resolution(s) that you want, deserve, and yes, paid-for with your invested time.[/INDENT]**Warning:** If you are terrified by a Linux command line, at least TRY to follow this procedure. It won't hurt you and it will help.

Still with me? Then let's proceed:


**Step #1: What kind of monitor do you have? What are its capabilities? What is its maximum resolution?**
[INDENT]Virtually every monitor vendor will publish the specifications for their products on the web. You can find them if you just look but first, you'll need the Vendor Name and Model of that monitor. It will be printed on a plate or tag, glued, screwed, or riveted to the back, top, bottom, or side of your monitor. Go look for it now. Write that information down and keep it handy.[/INDENT]**Step #2: Fetch your specs.**
[INDENT]Bring up a browser window and search for that model eg, 'dell 3007wfphc'.

Look for any site with details and specifications; the vendor's site is best, but most review sites will provide specifications too.

Ideally, you will find the "Horizontal Sync" *range*, expressed in kilohertz (KHz or khz), and the "Vertical Refresh" *range*, expressed in hertz (Hz).

If you found that, write it down like: ```
HorizSync 49.31 - 98.71
VertRefresh 60
```and proceed to **Step #4**.

If not, then look for the "Maximum Resolution". This will be listed as something like "[COLOR=DarkRed]2560[/COLOR] x [COLOR=Green]1600[/COLOR] at [COLOR=Blue]60[/COLOR]Hz". Write that down.[/INDENT]**Step #3: Calculate the frequencies from the specified resolution.**
[INDENT]Open a terminal window (Applications -> Accessories -> Terminal) and enter ```
cvt [COLOR=DarkRed]2560[/COLOR] [COLOR=Green]1600[/COLOR] [COLOR=Blue]60[/COLOR]
```Hit Enter. This will output the following ```
[COLOR=DimGray]# 2560x1600[/COLOR] **59.99** [COLOR=DimGray]Hz (CVT 4.10MA) hsync:[/COLOR] **99.46** [COLOR=DimGray]kHz; pclk: 348.50 MHz
Modeline "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync[/COLOR]
```Aha! The vertical refresh will be exactly 59.99Hz and the horizontal sync will be 99.46KHz. Write it down as:

```
HorizSync 99.46
VertRefresh 59.99
```[/INDENT]**Step #4: Create a basic xorg.conf**
[INDENT]Write the following commands down on paper because we're going to turn off the GUI and run a few commands from the console.

Flip to the text console via Ctrl+Alt+F1 and log in.

Execute these commands: ```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo /etc/init.d/gdm start ; exit
```(ignore any notices about the "new" way of starting/stopping services - those "new" ways work, and so does this way, but this way works on all releases)

You're back at the GUI login screen, so log in and bring up the rest of these directions.[/INDENT]**Step #5: Edit the basic configuration.**
[INDENT]Edit the new configuration by opening a terminal window and running the following command:
```
sudo gedit xorg.conf.new
```Scroll down to the entry ```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
```Add lines after the Identifier label to include the values you found (or calculated). The entry for that Dell monitor will look like: ```
Section "Monitor"
        Identifier   "Monitor0"
        [B]HorizSync    49.31 - 98.71
        VertRefresh  60.0
[/B]        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
```Note: If you appreciate details, fill in the VendorName and ModelName values (within quotes) like ```
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    49.31 - 98.71
        VertRefresh  60.0
        VendorName   "Dell"
        ModelName    "3007WFP-HC"
EndSection
```[/INDENT]**Step #6: Save the new configuration.**
[INDENT]Save that file. Then click File -> Save As (in gedit) and save the file as /etc/X11/xorg.conf then exit gedit.

Now, you have a new Xorg configuration installed where Xorg can see it, and you have a backup in your home folder.
[/INDENT]**Step #7: Restart X and test.**
[INDENT]In the terminal window, enter ```
sudo /etc/init.d/gdm restart
```You'll be logged off and the login screen should appear a few seconds later at full resolution. Congratulations, you have just done what your graphics card tried to do, but failed.[/INDENT]------

**YIKES**: If the screen goes black and stays that way, then you have either not provided the correct information for your monitor or your graphics card cannot run that monitor at these frequencies. Here's how you get back to low-res graphics mode:

Flip to the console via Ctrl+Alt+F1 and log in. Run these commands: ```
sudo rm -f /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart ; exit
```Now you can start over from **Step #1**, and find YOUR monitor's specifications. If you're very sure you have the correct numbers, then it is possible that your graphics card can't operate at the required frequencies. Replace it.

--

For further information on xorg.conf, bring up a terminal window and run ```
man xorg.conf
```For further information on the Xorg server, bring up a terminal window and run ```
man X
```Comments are always welcome.





Hi sir, after installing my driver i got a  640x 480 as the highest resolution of my monitor then after doing your guide now I got a higher resolution at 800x600 then now I'm stuck with it I don't know what to do. I want to have a 1152x864 resolution.
thanks sir
-roque valmoria

---

### Post by zero-n on 2010-03-26
Thanks alot that fixed my problem

---

### Post by angry ogre on 2010-04-02
this needs to be a sticky as i'm a noob and this fixed all my monitor issues.

---

### Post by zimzee on 2010-04-07
when i enter sudo X -configure it says command not found so could someone please help 
as its doing my head in.:(

---

