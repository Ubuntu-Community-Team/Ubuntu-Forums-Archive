---
title: "Open office tool bars and menus corrupted"
date: 2010-05-08
forum: General Help
---

### Post by Mr_Lazy on 2010-05-08
Hi,
I hope someone knows what is going on here. I am running 10.04 and I have a serious problem with the Open office menus and tool bars, as you can see from the screenshot, they are corrupted.

I have tried totally removing and re-installing Oo, but with no joy. Any ideas out there?

Many Thanks,
Stephen

---

### Post by meho_r on 2010-05-08
Try removing your settings. Open your home folder, press Ctrl+H (to show hidden files), find ".openoffice.org" folder (note the dot at the beginning) and rename it. After this, when you start OOo, it'll create a new .openoffice.org folder and use default settings. See if this helps.

---

### Post by Hagar Delest on 2010-05-08
See that one perhaps, several fixes about similar problems (read until the end): [[Solved] No text in OpenOffice menus](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183).

---

### Post by Mr_Lazy on 2010-05-09
Thanks for the ideas. Well, I have turned off Screen Font Anti-Aliasing and now Oo looks like it is from 1995... but, at least nothing is breaking. I am guessing this is a display driver issue... I have a nvidia card and I am using the latest recommended driver.

So do I wait until a new driver comes along, or is there something else I can do?

Thanks,
Stephen

---

### Post by Hagar Delest on 2010-05-09
I think that the Sun version doesn't have this problem but not 100% sure. Worth a try anyway: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by haydemon on 2010-05-14
Thank-you, thank-you! I was having the exact same problem (menus that appeared corrupted, dialog boxes with fuzzy fonts, etc.). I also tried uninstalling/reinstalling OOo, with no luck; then I tried the suggested fix (turning off anti-aliasing), and I got my menus back, but also the "vintage" look. I'm using Ubuntu 10.04. I'd like to completely uninstall OOo and do a fresh install. Can I use Synaptic to do that? I find it difficult to install packages off the Internet for some reason (still an amateur Linux user :confused:). Thx!

---

### Post by Hagar Delest on 2010-05-14
> **haydemon said:**
> I'd like to completely uninstall OOo and do a fresh install. Can I use Synaptic to do that?
It depends on what you want to do. If you want to keep the Ubuntu version, then use Synaptic to uninstall and reinstall. If you want to install the Sun version of OOo for example, use Synaptic to remove the Ubuntu packages of OOo. Then use dpkg to install the debs (just follow the tutorial).

---

### Post by Mr_Lazy on 2010-06-06
I am glad I am not alone. I have tried downloading and installing the packages from the OOo site, and the problem is still there.... does anyone have any ideas? I have OO on two other machines and they have no problem. Could it be a driver issue? I am using the latest recommended Nvidia driver...

Any ideas gratefully received.

---

### Post by Hagar Delest on 2010-06-06
have you checked the first link I gave?

---

### Post by Mr_Lazy on 2010-06-06
Yes, I followed those (your) instructions to the letter. OO installed apparently fine, and there were no problems, but then the top File, Edit etc bar started to corrupt. There are fewer font problems with this version, but when it happens, it renders the application unusable. Back to no screen font anti-aliasing for now.

---

### Post by Mr_Lazy on 2010-07-07
I am going to bump this as now it is starting to get unfunny. I installed Scribus from the repository and I am getting the same effect. Should I do a complete re-install of Lucid (which sounds a little Windoze-esque), or does anyone know what is going on here? (and how to fix it)

Thanks,
Stephen

---

### Post by haydemon on 2010-07-07
I haven't tried Scribus, but since I couldn't stand the look of the display in Oo, I went back to anti-aliasing. The menus work fine for a while, but begin to corrupt after a while. It is quite random, and I've learned to live with it for now. I'm hoping for a fix in the near future! However, I suspect it's a Lucid problem rather than an Oo one.[-o<

---

### Post by Mr_Lazy on 2010-07-11
> **haydemon said:**
> I haven't tried Scribus, but since I couldn't stand the look of the display in Oo, I went back to anti-aliasing. The menus work fine for a while, but begin to corrupt after a while. It is quite random, and I've learned to live with it for now. I'm hoping for a fix in the near future! However, I suspect it's a Lucid problem rather than an Oo one.[-o<

You might be right, but I don't know enough about this to figure out what is going on. I have now reinstalled Lucid because I went from Karmic and then through Lucid Alpha, and I wondered if that may have been the cause. But even with a clean install I get the same issue. 

Can anyone help? Oo may get uninstalled pretty soon, as it becomes pretty useless without the menus. :(

---

### Post by Hagar Delest on 2010-07-11
As a last shot, try the Sun/Oracle version. Make sure you've removed all the ubuntu packages of OOo.

---

### Post by Mr_Lazy on 2010-07-11
> **Hagar de l'Est said:**
> As a last shot, try the Sun/Oracle version. Make sure you've removed all the ubuntu packages of OOo.

Sorry I forgot mention I had tried your tutorial on the clean install of Lucid. I use Oo and Lucid at work with no issues, so this a real puzzle....

---

### Post by Hagar Delest on 2010-07-11
In that case, no idea. Or a last one: have you tried to change the fonts in the Gnome System>Preferences options?

---

### Post by haydemon on 2010-07-12
> **Hagar de l'Est said:**
> Or a last one: have you tried to change the fonts in the Gnome System>Preferences options?
I tried this one and it seems to work. At least, so far so good. Stay tuned... Thanks!

---

### Post by Mr_Lazy on 2010-07-12
> **Hagar de l'Est said:**
> In that case, no idea. Or a last one: have you tried to change the fonts in the Gnome System>Preferences options?

I have tried playing with several fonts, some seem to behave, and others do not... where can I check to see if a bug has been raised for this?

---

### Post by Hagar Delest on 2010-07-12
No idea. It may be related to Compiz also. Personally, I've never faced that on xubuntu.

Anyway, you can file a bug report and see what the devs say about that: [[Tutorial] Reporting bugs or suggestions](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=13490).

---

### Post by Mr_Lazy on 2010-07-13
> **Hagar de l'Est said:**
> No idea. It may be related to Compiz ...

I remembered you had said this, so I turned off visual effects, and so far no issues... I can live without effects, being able to use apps is the priority..

I might raise (but first look for) a bug report about this... I have added a recent screenshot to remind you of the horror....

Thanks for throwing those ideas around :)

---

### Post by Mr_Lazy on 2010-07-13
OK, I have found the bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492")

And the given wisdom is to disable compiz or:
> The problem is related to font rendering options. Choosing "Subpixel smoothing (LCD)" as font rendering option leads into the font corruption problem. Changing to "Best shapes" corrects the problem.
and subsequently:
> Just as an addition, when selecting "Best Shapes" and then setting the hinting to "Slight" in the Details options, fonts will look great and the OOO corruption is gone (can't say about Lotus Notes).
So when I get back to the machine with the problem I will try that.
Worrying thing is that the bug has yet to be assigned or given an importance level yet.

---

### Post by lordskid on 2010-07-13
did you recently change fonts under appearance preferences?

if so try using bitstream charter size 12 will do. at least temporarily, see if this works.

I encountered this problem after changing to symbol font. Notice the difference with the bug report screenshots with that of yours.

you can read the word default while the bug report screenshot got horizontal lines for each letter.

---

### Post by Mr_Lazy on 2010-07-13
The screenshot on the bug report is also what I am seeing...

---

### Post by lordskid on 2010-07-13
but I notice in your screenshot that I can read the font is Times new Roman

while on the bug report [http://launchpadlibrarian.net/45027048/screenshot.png](http://launchpadlibrarian.net/45027048/screenshot.png) the menu wordings are consistent to the fonts toolbar wordings.

---

### Post by Mr_Lazy on 2010-07-14
Well whatever the specific details of the screenshots are, it doesn't matter, changing the to "best shapes" and changing the hinting works fine. It means I can turn the effects back on AND use OO and Scribus. So I hope this thread helps others out there.

I hope there is a proper fix soon...

---

