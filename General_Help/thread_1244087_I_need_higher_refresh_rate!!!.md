---
title: "I need higher refresh rate!!!"
date: 2009-08-19
forum: General Help
---

### Post by AwesomeTux on 2009-08-19
Hello,

I am using a nVidia GeForce 6200 on a Gateway LE500 CRT currently at 60.02Hz. I know the monitor can go higher than that, because it does so in Windows. I don't know if this is a nVidia thing, or a X.Org thing. I am currently running the 190.18 nVidia Linux-x86_64 beta video driver. I've tried different versions of the drivers, no luck.

Is there a way to ABSOLUTELY FORCE a higher refresh rate, even if it may damage my monitor? :confused:

---

### Post by CatKiller on 2009-08-19
> **AwesomeTux said:**
> I don't know if this is a nVidia thing, or a X.Org thing.

It's a monitor thing. Monitors advertise their capabilities through EDID.

> Is there a way to ABSOLUTELY FORCE a higher refresh rate, even if it may damage my monitor? :confused:

Within reason, you can specify the refresh rate ranges that your monitor is capable of yourself, by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to [this page]("http://support.gateway.com/s/MONITOR/7002702/700270210.shtml"), the values for your monitor are 
```

        HorizSync       30-69
         VertRefresh     50-120
```

You may also need to tell X to ignore whatever the monitor is telling it. You can do this by putting ```
        Option          "UseEDID"                       "False"
``` in the Device section.

As far as I can tell, your monitor can only do 75Hz at 1024×768, not at 1280×1024.

---

### Post by AwesomeTux on 2009-08-19
> **CatKiller said:**
> It's a monitor thing. Monitors advertise their capabilities through EDID.



Within reason, you can specify the refresh rate ranges that your monitor is capable of yourself, by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to [this page]("http://support.gateway.com/s/MONITOR/7002702/700270210.shtml"), the values for your monitor are 
```

        HorizSync       30-69
         VertRefresh     50-120
```

You may also need to tell X to ignore whatever the monitor is telling it. You can do this by putting ```
        Option          "UseEDID"                       "False"
``` in the Device section.

As far as I can tell, your monitor can only do 75Hz at 1024×768, not at 1280×1024.

Nope, didn't work. Man... I know it can go as high as 1280x1024 at 70Hz, because I've done so in Windows.

---

### Post by philinux on 2009-08-19
What version ubuntu you running?

What does system>admin>nVidia settings tool give?

Is the crt connected directly to the pc. i.e not through a switch?

---

### Post by AwesomeTux on 2009-08-19
> **philinux said:**
> What version ubuntu you running?

What does system>admin>nVidia settings tool give?

Is the crt connected directly to the pc. i.e not through a switch?

The System>Preferences>"NVIDIA X Server Settings" is basically useless, it's there but doesn't offer much. And my CRT is connected through a switch.

---

### Post by AwesomeTux on 2009-08-19
CatKiller, that link helped me alot, I set my "max" kilohertz to 69, which gives me 65Hz at 1280x1024, more, but no 70-75Hz.

Also I used this in my xorg.conf:
```
    Option "UseEDID" "FALSE"
    Option "ModeValidation" "AllowNon60HzDFPModes, NoEdidModes, NoEdidDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoDFPNativeResolutionCheck"
```

---

### Post by philinux on 2009-08-19
Try connecting your crt directly to the pc. I seem to remember that switches can interfere with ubuntu resolution and refresh being applied correctly.

---

### Post by AwesomeTux on 2009-08-19
> **philinux said:**
> Try connecting your crt directly to the pc. I seem to remember that switches can interfere with ubuntu resolution and refresh being applied correctly.

Yeah, I seem to recall that too. But it made no difference in my case, perhaps it used to happen with older switches.

I'm starting to think my monitor can only do 65Hz at 1280x1024. And when I go into Windows and change the refresh rate it tells me it set it to what I want, but actually only goes as high as 65Hz, you know, one of those stupid Windows things that Windows pulls all the time :P

Or that the GNU/Linux power management only allows me to put it as high as 65Hz, because that's what's "safe" you know?

Make any sense?

---

### Post by philinux on 2009-08-19
As long as it looks ok to you, thats the main thing. :)

---

### Post by cascade9 on 2009-08-19
I would guess that your monitor is limited to 65hz @ 1280x1024. Thats typical of lower end 17''s and almost all 15''s. 

Gateways support page doesnt make it clear what the limit is-
[http://support.gateway.com/s/MONITOR/7002702/700270210.shtml](http://support.gateway.com/s/MONITOR/7002702/700270210.shtml)

If you check the 'using your le500' page it doesnt even list 1280x1024-
[http://support.gateway.com/support/manlib/cmponts/Monitors/8507025/07025.htm](http://support.gateway.com/support/manlib/cmponts/Monitors/8507025/07025.htm)

Probably because 1280x1024 is considered kinda strange (on 15'' and most 17'' that is, 1280x1024 was pretty much standard on 19'')

BTW, I have had issues with linux refusing to go as high in refresh rate as windows, my 107P does 1600x1200 @ 75Hz in windows, only goes to 70Hz in linux. Never really figured out why.

---

