---
title: "Video on youtube and other sites skipping."
date: 2009-08-08
forum: General Help
---

### Post by gavoby on 2009-08-08
Hi there, I am having some problems watching videos on websites. The sound is ok but the picture skips. If I leave it buffer before I watch it it gets better but still skips a bit. Any help would be appreciated.

Ubuntu 9.04 (Jaunty)
Memory: 497.5
Intel Pentium 4
-204 GHZ
Geforce FX 5500

---

### Post by khelben1979 on 2009-08-08
Report what version of flash you have (right click on the YouTube window).

---

### Post by gavoby on 2009-08-08
Adobe Flash 10

---

### Post by khelben1979 on 2009-08-08
Are you using native graphics drivers from nVidia? And if so, what version? Open source nVidia drivers are slower.

---

### Post by gavoby on 2009-08-08
I'm using the one from synaptic, 173 something I think. Can I install the original?

---

### Post by khelben1979 on 2009-08-08
> **gavoby said:**
> I'm using the one from synaptic, 173 something I think. Can I install the original?

The latest driver right now is 173.14.20, so it looks like you don't need that.

It might be that your x-server isn't correctly configured for optimized speed (post your output of /etc/X11/xorg.conf), or.. your video card isn't strong enough. 8-(

---

### Post by harry2006 on 2009-08-08
seems like some x-server issue!

---

### Post by gavoby on 2009-08-08
How should it be configured? Can you let me know?

---

### Post by khelben1979 on 2009-08-08
> **gavoby said:**
> How should it be configured? Can you let me know?

This section of the x server is interesting (taken from my system):
> Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Copy and paste the text into this thread (or just attach the conf file) so we can have a look at it. Some of these modules can speed up graphics but it should not look the same as mine, it all depends on what modules your video card supports. I'm not sure myself how it should look like.

---

### Post by gavoby on 2009-08-08
Is there a command I type into terminal to get that info?

---

### Post by diamondjim08 on 2009-08-08
Hi,
Same problem here... slow and skipping movies.  In fact, the scrolling of pages; loading of pages on my FF browser are slow.  System monitoring shows large amounts of CPU being used for simple functions.  Playing movies on Hulu is "jerky" and slow.  sound is OK.

System is Ubuntu 9.04 upgraded from 8.10.
Computer is Dell GX260, Pent 4, 2 ghz cpu, 1 gig ram, intel 845G video and/or Gforce FX 5200 video card (128mb ram)-tried both but little improvement.

Opera is faster browser but as it will not play movies for some reason.

Thanks for any help or ideas! :-)
<> Jim

---

### Post by gavoby on 2009-08-08
> **khelben1979 said:**
> This section of the x server is interesting (taken from my system):


Copy and paste the text into this thread (or just attach the conf file) so we can have a look at it. Some of these modules can speed up graphics but it should not look the same as mine, it all depends on what modules your video card supports. I'm not sure myself how it should look like.

sorry but how do I get that information? do i type something into terminal?

---

### Post by khelben1979 on 2009-08-08
Just choose to attach the file from > /etc/X11/xorg.conf to this thread. 

Do you know how to do that?

---

### Post by gavoby on 2009-08-08
SOrry no i don't :(

---

### Post by khelben1979 on 2009-08-08
Check out the attached picture.

---

### Post by gavoby on 2009-08-08
I dont know how to get the file. How do I get the information I need to attach?

---

### Post by gavoby on 2009-08-08
How did you get this?
This section of the x server is interesting (taken from my system):
Quote:
Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

---

### Post by khelben1979 on 2009-08-08
> **gavoby said:**
> I dont know how to get the file. How do I get the information I need to attach?

When you click you get a file dialog in which you browse yourself to it. First go **/** then **etc** then **X11** and then you choose the file **xorg.conf**.

If this doesn't work because of file permission problems: 
```
sudo cp /etc/X11/xorg.conf /home/[username]
``` ```
chown [username].[username] xorg.conf
```
Then you go from there and choose that file instead.

---

### Post by gavoby on 2009-08-08
I'm sorry I'm completely lost here haha sorry

---

### Post by gavoby on 2009-08-08
> **khelben1979 said:**
> When you click you get a file dialog in which you browse yourself to it. First go **/** then **etc** then **X11** and then you choose the file **xorg.conf**.

If this doesn't work because of file permission problems: 
```
sudo cp /etc/X11/xorg.conf /home/[username]
``` ```
chown [username].[username] xorg.conf
```
Then you go from there and choose that file instead.


When I click what?

---

### Post by khelben1979 on 2009-08-08
See post 15 in this thread.

(I rest my case)

---

### Post by gavoby on 2009-08-08
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Does this mean anything? this is the xorg.config file

---

### Post by gavoby on 2009-08-08
> **khelben1979 said:**
> See post 15 in this thread.

(I rest my case)

I know hoe to attach a file to a thread, I just don't know what file you want me to attach.
Ok thanks for trying to help me anyway

---

### Post by gavoby on 2009-08-08
> **khelben1979 said:**
> See post 15 in this thread.

(I rest my case)

Is this it?

---

### Post by gavoby on 2009-08-08
I asked a question here yesterday about youtube videos skipping. Which mine are. It improves when I let the video download fully anf then play but still skips a bit.
Somebody said it could be my x-server config. but I don't know what that is.
Any ideas?

Ubuntu 9.04 (Jaunty)
Memory: 497.5
Intel Pentium 4
-204 GHZ
Geforce FX 5500
Adobe Flash PLayer 10

---

### Post by Katalog on 2009-08-08
It depends. You'd need to find someone with the same video card you have and see how theirs is set up.

---

### Post by gavoby on 2009-08-08
When I play a video on youtube it skips, if I let it download fully then play it's better but still skips. The sound is ok.

Adobe FLash 10
Ubuntu 9.04 (Jaunty)
Memory: 497.5
Intel Pentium 4
-204 GHZ
Geforce FX 5500

---

### Post by gavoby on 2009-08-08
Ok thanks

---

### Post by gavoby on 2009-08-08
Does anyone have a geforce fx 5500? How is your x-server configured. My youtbe videos are skipping so was wondering if anyone was having the same problem?

Ubuntu 9.04 (Jaunty)
Memory: 497.5
Intel Pentium 4
-204 GHZ
Geforce FX 5500

---

### Post by Greg Xix on 2009-08-09
As much as I Like Ubuntu, this is one of my main criticisms. Try disabling Visual Effects.

On your desktop, Right-Click and select Change Desktop Background. Then select the Visual Preferences tab, and select "None".

This will disable your Compiz settings if I am not mistaken.



-GX

---

### Post by overdrank on 2009-08-09
Please do not create multiple threads on the same issue. Threads merged

---

### Post by gavoby on 2009-08-09
Ok sorry

---

