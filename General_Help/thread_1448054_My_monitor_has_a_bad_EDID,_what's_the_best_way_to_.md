---
title: "My monitor has a bad EDID, what's the best way to make my own?"
date: 2010-04-06
forum: General Help
---

### Post by Spen on 2010-04-06
My monitor is a old CRT, on windows I can get a perfect 1280x1024, but I can't on ubuntu.

When I was checking the EDID, it was coming back as a error and my xconfig was pretty much blank.


Is there a good guide anywhere on editing the xconfig and letting me use the correct 1280x1024?

---

### Post by Spen on 2010-04-06
[http://ubuntuforums.org/showthread.php?t=1324239&highlight=resolution](http://ubuntuforums.org/showthread.php?t=1324239&highlight=resolution)

Is this all I have to do?

---

### Post by patchwork on 2010-04-06
That's certainly a good start.  You can find more information on the configuration file with ```
man xorg.conf
```

---

### Post by audiomick on 2010-04-06
Hi.
That guide looks pretty good. I haven't tried it personally, but from limited experience of messing around with xorg.conf, it looks correct.

Bear in mind the following: The author suggests a "bail out" for the event that you end up with a black screen which involves the command "rm". Look at
```
man rm
``` to inform yourself about this command, and bear in mind that it is a dangerous command if wrongly used. Type it very carefully.

You might like to mention here what graphics card you have. That would help people if you need further assistance.

---

### Post by Spen on 2010-04-06
Older monitor, older video card.


6600gt, apg

---

### Post by Spen on 2010-04-06
So, try that method of getting 1280x1024 first?

---

### Post by patchwork on 2010-04-06
Yes, start with that.  Anything else you need to do will build off of that new configuration file.

---

### Post by Spen on 2010-04-06
I found my monitors H and V.

H is: 63.9
and V is: 60


I tried entering that into the new xconfig file and it's still the same.

---

### Post by wojox on 2010-04-06
Have you tried making a new xorg.conf? If not this command will back up your old file and create a new one:

```
sudo nvidia-xconfig
```

Then configure it with:

```
gksudo nvidia-settings
```

---

### Post by Spen on 2010-04-07
Where should I be saving the new xorg.conf too?

---

### Post by audiomick on 2010-04-07
Assuming you used the "X -configure" command from step #4 of the guide that you posted the link to in post #2, the file should, I think, be created where it belongs.

I can't check right now, as I am not on my Ubuntu machine, but I am sure it is at
/etc/X11/xorg.conf

If you open it to edit with
```
gksu gedit /etc/X11/xorg.conf
```
and then just save after the changes, it should be in the right place.

As a suggestion, you might want to save a copy of the default file before you edit anything, or comment out any lines you want to remove like this
```
# a hash at the start of the line
```
instead of deleting.

I always do something like this
```
# this is what I added to achieve such and such
```
before the lines you add.

Lines with a # at the start are not read as part of the config file. They are only comments. Lots of comments makes it easier to go back if you need to, or see what you did if you look at it again in a years time.

---

### Post by Spen on 2010-04-07
In Windows, I'm running perfect 1280x1024.

I bring up my monitors OSD, and it says:

H: 63.9 KHz
V: 60   Hz

So, I should be editing it to look like this, right?

```
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    63.9
        VertRefresh  60.0
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
```


Also, I found this online:
```
[PV-1995S.AddReg]
HKR,"MODES\1600,1200",Mode1,,"30.0-95.0,50.0-160.0,+,+"
HKR,,ICMProfile,0,"998.icm" 

```

That doesn't give me any info, right?

---

### Post by Spen on 2010-04-07
Okay, so I used my Monitor's On Screen Display to show me the different H and V values.


I took theses values in the lowest possible res, and in the highest possible res.


The lowest H value I got was: 31.3
The highest H value I got was: 95.5

The lowest V value I got was: 60
The highest V value I got was: 70


So, I should change my xconfig to something like this?

```
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    31.3 95.5
        VertRefresh  60.0 70
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection
```


Would this be okay to do?

---

### Post by audiomick on 2010-04-07
Hi.
I am sorry I can't compare to mine at the moment, because I am away from home and my Ubuntu machine for the next week.

I think you are on the right track. Have you looked at the man page for xorg.conf?
try
```
man xorg.conf
```
in the terminal. I think that will bring it up.

I just found this in the Ubuntu Documentation. Maybe it will help. It is talking about xrandr, which is the mechanism that is taking over from the xprg.conf file. Have a look at that as well. Maybe it will suggest something to you.

See how you go with that lot. I don't know if I will be back tonight, I am pretty tired, but I will try and look in tomorrow.

---

### Post by Spen on 2010-04-07
I got it working!

I installed the recommend drivers, and then edited my xconfig.

Works flawless, thank you guys so much for helping.


I used theses settings:
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    31.3 95.5
        VertRefresh  60.0 70
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

---

### Post by audiomick on 2010-04-07
Hey, great to hear it. You might like to mark the thread as solved. That is under "thread tools" at the top of the thread.

I know the feeling. I still remeber clearly getting 1280x800 to work before it was available by default. Good on you!!

---

