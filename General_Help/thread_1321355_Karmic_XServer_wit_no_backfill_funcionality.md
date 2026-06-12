---
title: "Karmic XServer wit no backfill funcionality"
date: 2009-11-10
forum: General Help
---

### Post by ZaHACKieL on 2009-11-10
Hi everyone,

I just installed Karmic and got a bug I had for a long time in Jaunty and that was a delay when maximizing, restoring, alt+tabbing windows.

I solved that by installing the package XServer with no backfill funcionality from:

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

but now when I try to install that in Karmic, after adding the line to software source and refreshing them I get the error:

Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Is there another way to install that package or a way to solve that problem?

Thank you

---

### Post by DragonJar on 2009-11-10
Hello!
Have the same issue.
Badly needed ...

---

### Post by ZaHACKieL on 2009-11-10
> **DragonJar said:**
> Hello!
Have the same issue.
Badly needed ...

I sent an email to the guy who uploaded the package. If I get an answer I'll let you know. Also, if you make it work tell me how please =]

ZL

---

### Post by Giblet5 on 2009-11-10
Do you mean BackingStore (aka save-under, aka backing-fill)?

You can turn that off in xorg.conf.

Example "Device" section: ```
Section "Device"
    Identifier     "NVIDIA Geforce 8800GTX"
    Driver         "nvidia"
    Option         "FlatPanelProperties" "Scaling=centered, Dithering=enabled"
    Option         "UseEDIDFreqs" "true"
    Option         "UseEDIDDpi" "true"
    Option         "AllowDDCCI" "true"
    Option         "DigitalVibrance" "12"
    Option         "RenderAccel" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "HWCursor" "On"
    Option         "SWCursor" "Off"
    Option         "DPI" "96x96"
    Option         "AllowGLXWithComposite" "true"
    Option         "TripleBuffer" "true"
    Option         "EnablePageFlip" "true"
    Option         "ColorTiling" "true"
    Option         "EnableDepthMoves" "true"
    **[COLOR="DarkRed"]Option         "BackingStore" "false"[/COLOR]**
    Option         "DynamicClocks" "true"
EndSection
```



Edit: You don't need all of those options, but they show the BackingStore option in context. Also note that BackingStore is not unique to nvidia chips, like a few of the other options above.

---

### Post by ZaHACKieL on 2009-11-10
> **Giblet5 said:**
> Do you mean BackingStore (aka save-under, aka backing-fill)?


I'm not totally sure that's what I need. The package description says:

This PPA contains a variant of the xserver with background initialization disabled

Besides, I don't have that BackingStore line in my xorg.conf

=/ =/

---

### Post by Giblet5 on 2009-11-10
> **ZaHACKieL said:**
> I'm not totally sure that's what I need. The package description says:

This PPA contains a variant of the xserver with background initialization disabled

Besides, I don't have that BackingStore line in my xorg.conf

=/ =/

It's an option (hence, the name). You probably don't have any of those options in your xorg.conf file, even though most of them apply to any driver.

The default BackingStore value is "true", and it can cause problems when the XDAMAGE extension is enabled (and it probably is). It takes five minutes to test the option, an hour to argue about it, or two days to build from source with that feature disabled by default so that one doesn't have to edit xorg.conf. It's your time.

---

### Post by ZaHACKieL on 2009-11-10
> **Giblet5 said:**
>  It takes five minutes to test the option, an hour to argue about it, or two days to build from source with that feature disabled by default so that one doesn't have to edit xorg.conf. It's your time.

I guess I can try that ^^ . Thank you, I'll let you know if that works

---

### Post by ZaHACKieL on 2009-11-10
> **Giblet5 said:**
>  It takes five minutes to test the option, an hour to argue about it, or two days to build from source with that feature disabled by default so that one doesn't have to edit xorg.conf. It's your time.

Well, I added the line to the xorg file, reboot, but the problem is still there.

I'll keep trying. Thanx anyway!!

ZL

---

### Post by apocalypse80 on 2009-11-10
Get this for karmic : [https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

---

### Post by ZaHACKieL on 2009-11-10
> **apocalypse80 said:**
> Get this for karmic : [https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

Hi. I did the updated you told me but now I only get a black screen after the ubuntu white logo. I can´t even log in to ubuntu. How can I go back to my last configuration before the update?

Thanx

---

### Post by ZaHACKieL on 2009-11-10
> **ZaHACKieL said:**
> Hi. I did the updated you told me but now I only get a black screen after the ubuntu white logo. I can´t even log in to ubuntu. How can I go back to my last configuration before the update?

Thanx

Uuhh....well, I just want to report that I got my Karmic back on the road after reinstalling it. I first tried replacing the xorg.conf file with its backup...didn't work. I did the reconfigure thing for X11...didn't work either. I reinstalled the whole X11...guess what, didn't work.

So I didn't want to waste more time and I just reintalled Karmic in my root partition and since I have a /home side partition, everything went back to normal asap.

BUT I still have the delay issue and I'm afraid of installing again that package so, has anyone succeeded yet solving the delay problem?

Thanks!

---

### Post by DragonJar on 2009-11-12
Ufff ,lucky me, I don't tried this :) 
It's would be a catastrophe if my working station will need reinstall.
ZaHACKieL, thank you for taking such a risk.
But well, delay problem is quite annoying and as I understand it's touched many people.
For the moment I switched off the compiz, 
I can live without it, but would be nice to get it back with no terrible delays in unmaximizing windows.

P.S. If this option can be provided in config - this will be even more convenient. 
Installing non standard X is really not a good solution for that. 
But ... no any solution for the moment ...

---

### Post by ZaHACKieL on 2009-11-13
The only thing I can think about, beside the possibility of the package being the only responsible for my machine's demise is that simultaneously I downloaded more updates...maybe one of them caused it, I'm not totally sure but it's an option.

Anyone has tried the xserver-nobackfill no backfill from:

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

Please we need some answers here! =]

---

### Post by apocalypse80 on 2009-11-13
> **ZaHACKieL said:**
> Anyone has tried the xserver-nobackfill no backfill from:

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

I'm using that and it works just fine.
Issues with no-backfill are the same as they were in jaunty; huge memory leak and occasional garbage on screen.

To "fix" the memory leak I have the system monitor applet running and when memory gets too green I fire up glxgears (any 3D app will do).
That cleans the trash.

As for what I did overall.
- Fresh karmic install
- Installed fglrx through system->administration->hardware drivers
- Was greeted with a black screen on next reboot
- Went into recovery mode -> root terminal
- Ran "aticonfig --initial", got an error about xorg.conf
- Fixed that by manually editing xorg.conf (can't remember exactly how)
- Ran "aticonfig --initial" then "aticonfig --acpi-services=off"
- Reboot and presto it all works
- Bonus step ; went to compiz configuration and enabled "unredirect fullscreen windows", to get proper fullscreen video.
- Only then did I apply the no-backfill patch

My current xorg.conf

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Default Device"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Pretty slim ain't it?
IIRC when I first ran "aticonfig --initial" it complained about missing the "Device" part of the file.

---

### Post by Filipek on 2009-11-17
Just for the information not everything is bad. Installed that today, works like a charm (I mean the fullscreen/normal screen lag is gone).

Ubuntu Karmic, oficial latest ATI driver. No changes whatsoever.

---

### Post by latebeat on 2010-04-30
> **Filipek said:**
> Just for the information not everything is bad. Installed that today, works like a charm (I mean the fullscreen/normal screen lag is gone).

Ubuntu Karmic, oficial latest ATI driver. No changes whatsoever.

Well for me it didn't work out of the box. However this **[post]("http://phoronix.com/forums/showpost.php?p=125120&postcount=11")** had a ppa that did the trick for me.

```
ppa:info-g-com/xserver-xorg-1.7.6-gc
```
you can also try
```
ppa:bryceharrington/violet
```

---

### Post by ZaHACKieL on 2010-11-10
Hi this is an old topic I started over a year ago but I just want to say that after all that time now it's solved for Ubuntu 9.10 64 bits with the 10.7 version of ATI Catalyst driver.

I haven't tried with the new Ubuntu versions. When I do I'll make you guys know.

---

### Post by latebeat on 2010-11-10
> **ZaHACKieL said:**
> Hi this is an old topic I started over a year ago but I just want to say that after all that time now it's solved for Ubuntu 9.10 64 bits with the 10.7 version of ATI Catalyst driver.

I haven't tried with the new Ubuntu versions. When I do I'll make you guys know.


Even though it's old, still, that's good to know. 
Keep us informed if u try a newer release.

---

### Post by Yellow Pasque on 2010-11-10
Catalyst fixed this issue when it switched to a new 2D acceleration method in Catalyst 10-6 (actually, it started in 10-2, but you had to manually enable it in xorg.conf)

---

