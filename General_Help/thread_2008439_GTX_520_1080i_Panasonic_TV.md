---
title: "GTX 520 1080i Panasonic TV"
date: 2012-06-22
forum: General Help
---

### Post by Sciaphobie on 2012-06-22
Heya all!
I'm really despreate and wondering if I can find some kinda help here since google did nothing but bust my nutsack ^^'

Now I build a new computer super silent and so on, so it could run through the night w/o naggin me.
Since I like to fall asleep watching series / movies.
Now, I got a Asus GT 520 GPU, after breaking my ballz cause the old ATI would just show up in Additional Drivers I found this: [http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html) and I got the drivers.

Now, the desktop is really messed up, I can neither see the top, nor the side bar. and theres a small bar'ish portion at the bottom of the screen constantly flickering.

The old ATI GPU [Was in a really noisy dell pc of 2008 the drove me nuts] would, after the installation of the additional drivers, upscale my hd ready tv to 1920x1080. Now doesnt matter if I use the upscale or native resoltuion, the mentioned problem remains the same. Any help? I'm starting to QQ here...

Thx in advance
Sciaphobie ^_^v

P.S.:
400W psu
120gb SATA 2 SSD
i3 2125
2x2gb Corsair Vengeance 1.5V 1600mhz
Gigabyte: B75M-D3H
Asus  GT 520

---

### Post by Sciaphobie on 2012-06-22
Forgot to mention: The TV is the only screen [always has been] and is connected by HDMI [Before it was connected by HDMI to DVI adapter.

---

### Post by papibe on 2012-06-22
Hi Sciaphobie.

If you installed a new graphic card, you may need to recreate your X configuration file. Open a terminal and run this:
```
sudo nvidia-xconfig
```
Then restart your computer.

Tell us how it goes.
Regards.

---

### Post by Sciaphobie on 2012-06-22
Well, it did something, my TV was redoing its aspect and so on, but the problem is precisely the same.

Flickering Bar at the bottom, side bar approx 1/5 visible, topbar not visible at all :(

But its there, i can click it in the void of the screens end ^^'

Any more ideas? :/ ty ;)

---

### Post by papibe on 2012-06-22
Could you post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by Sciaphobie on 2012-06-22
Well, since I ran you command, the BIOS screen is not in the proper dimension aswell. probably cause its running it in 1080i aswell instead of 720p, but regardless of the TV settings or the resolutions the probelm seems to be remaining Q.Q

Here are the two links:

[http://paste.ubuntu.com/1055189/](http://paste.ubuntu.com/1055189/)
[http://paste.ubuntu.com/1055191/](http://paste.ubuntu.com/1055191/)

TYVM for you help and gn8 for now 2 am here ^^'

---

### Post by papibe on 2012-06-22
Here's the problem:
```
[     7.840] (WW) NVIDIA(0): PANASONIC-TV (DFP-1)'s EDID does not contain a maximum image
[     7.840] (WW) NVIDIA(0):     size; cannot compute DPI from PANASONIC-TV (DFP-1)'s
[     7.840] (WW) NVIDIA(0):     EDID.
```
It looks there's some corruption on the TV's EDID data (resolution, timings, size, etc).

What kind of cable are you using to connect the TV?
Have you tried using another TV input?

Regards.

---

### Post by Sciaphobie on 2012-06-23
Good Morning ^^
Using HDMI cable hmmm.
I did use the old GPU dvi with an adapter to hdmi. initially didnt work either... kinda weird. I tried the DVI slot with the adapter, didnt make anydifference so far. hm, any idea?
And thx for your help :)

---

### Post by HiImTye on 2012-06-23
give either grandr (pre 12.04) or arandr (12.04) a try, see if any of the display modes it finds will work better

---

### Post by Sciaphobie on 2012-06-23
Hm, how do I do that? ^^'
Ah I just remember, in the old setup I had, the TV was recognized as Laptop, rater than "Panasonic Industry Company 65" " [It's not a 65" no idea why it shows that O.o] And I somehow got it to work back then by using a 2nd screen, really weird O.o

And how to I get to grandr or arandr? :)

---

### Post by HiImTye on 2012-06-23
for pre-12.04 versions use:
```
sudo apt-get install grandr
```
then run
```
grandr
```

for 12.04 swap out the 'g' for an 'a'

---

### Post by Sciaphobie on 2012-06-23
Giving it a shot ty :)

---

### Post by Sciaphobie on 2012-06-23
Well grandr I couldnt install, cause it told me "this software has been replaced or isnt avaiable anymore"

arandra I installed and ran, and got Screeb Layout Editor, but cant do much in there.... HDMI0 is detected hmmm.

I just saw, the error again I couldnt remember yesterday:
"Sorry, Compiz has been terminated unexpectedly"
/usr/bin/compiz

libnux-2.0-D 2.12.0-Dubuntu1

"Compiz crashed with SIGSEGV"

---

### Post by HiImTye on 2012-06-23
arandr replaced grandr in 12.04

in arandr, go to Outputs > your output (probably default) > resolution
(or right click on the big box below the menu and choose resolution)
to change between them

---

### Post by Sciaphobie on 2012-06-23
Doesnt matter which resolution I choose, the Sidebar is still only like 1/5 visible and no topbar =/

---

### Post by Sciaphobie on 2012-06-23
I plugged in an old 1600x1050 screen and it seems to work fine. The screen, now with the tvin the arandr settings, it seems like the screen is too wide, which is kinda weird, cause as mentioned before it worked in the last setup =/

---

### Post by Sciaphobie on 2012-06-23
Alright, solved the problem: It was definitely an issue with the NVIDIA card.

Kicked it out and put in the old ATI -> Works like a charm.

Figured since my GTX 680 in my gaming rig is a beast, a 2gb passive cooled gt 520 would do awesome for hd videos... no more nvidia to ubuntu for me ^^'
Ty all for you help :)

---

