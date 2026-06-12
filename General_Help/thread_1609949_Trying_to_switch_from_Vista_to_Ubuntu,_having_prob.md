---
title: "Trying to switch from Vista to Ubuntu, having problems with uploads."
date: 2010-10-31
forum: General Help
---

### Post by TheAmazingDave on 2010-10-31
Hello all,

I've tried making the switch before, but always end up running into some trouble that has me going back to Windows.

I recently installed Ubuntu 10.10 and everything has been going fairly smooth, I've been using it for a few weeks with no complaints.

No complaints, that is, until I try to upload files...

My digicam shoots movies in AVI format. I have no problem uploading these files to YouTube from Vista, it works as it should. I cannot upload anything to YouTube from Ubuntu. Whatever I try to upload fails instantly.

I also cannot upload photos to PhotoBucket, with the same outcome. The transfer appears to start, but fails immediately afterwards. The Photobucket problem has me really intrigued, since it will upload some files directly from the hard drive, but most pics on the hard drive will still fail to upload, and all files on my SD card straight out of the camera fail to upload regardless, even though the computer reads the card and the files fine locally.

What gives? Really would like to make the switch permanently, but every time I try, I am always left disappointed by these lame troubles.

Any help is extremely appreciated.

---

### Post by fbhosted on 2010-10-31
It's issues with the Flash uploader than many of these websites use and the lack of full Flash support for Linux. Have you tried using a "simple" uploader option with many of these sites? I use Google Chrome, so it has it's own Flash plugin rather than dealing with the headache of Firefox plugin and Ubuntu's own plugin.

---

### Post by Verbeck on 2010-10-31
their uploader uses flash, so try installing flashplugin-installer
it's currently working fine when i try

EDIT: as suggested above, try chrome or chromium

---

### Post by TheAmazingDave on 2010-10-31
Thank you for a fast response fb. 

The "simple" uploader for YouTube won't even work in Ubuntu, I click the link and it goes right back to the regular uploader.

The bulk uploader came up on the screen for Photobucket I'm pretty sure, but it still failed. 

I'll give Chrome a shot I s'pose.

---

### Post by TheAmazingDave on 2010-10-31
> **Verbeck said:**
> their uploader uses flash, so try installing flashplugin-installer
it's currently working fine when i try

EDIT: as suggested above, try chrome or chromium

Pretty sure I've installed that. I'm about to boot Ubuntu and check it out.

Thanks again for the quick help!

---

### Post by TheAmazingDave on 2010-10-31
So I searched for all packages regarding Flash and installed them, no dice.

So I checked for software updates, and it found several for Java; downloaded them and installed them, no dice.

I then installed Chromium, which I'm posting this from. Photobucket upload still does not work. YouTube upload will start, **but makes my ethernet connection drop**, subsequently failing, after a minute or so. :confused:

edit: it's staying connected right now but is stuck on 14%. It's only a 75 MB file. :(

---

### Post by cpmman on 2010-10-31
Have you tried FLASH-AID - a Firefox add-on from lovinlinux?

---

### Post by TheAmazingDave on 2010-10-31
> **cpmman said:**
> Have you tried FLASH-AID - a Firefox add-on from lovinlinux?

no, but I will. Thank you.

edit: it looked promising but this nifty add-on wasn't able to help me. TYVM anyway, glad to know about that.

---

### Post by cpmman on 2010-10-31
Have you got the restricted extras in your repositories(sources list) ?

---

### Post by TheAmazingDave on 2010-10-31
> **cpmman said:**
> Have you got the restricted extras in your repositories(sources list) ?

I believe so, unless I don't understand properly. When I open Synaptic Package Manager, and go Settings>Repositories I see that the box is checked for Proprietary Drivers for Devices (Restricted) is checked. Is that what you're referring to?

---

### Post by kaldor on 2010-10-31
> **TheAmazingDave said:**
> I believe so, unless I don't understand properly. When I open Synaptic Package Manager, and go Settings>Repositories I see that the box is checked for Proprietary Drivers for Devices (Restricted) is checked. Is that what you're referring to?

That's restricted DRIVERS, not restricted formats :)

Ubuntu does not package things such as Flash, Java and multimedia codecs by default due to legal issues in countries such as USA and Japan. I believe the package is called *ubuntu-restricted-extras*. Make a search for it in the Software Centre and see how that works :)

Edit: If you want a more "out of the box" OS, try LinuxMint 10 when it comes out in a couple of days. It's based on Ubuntu (100% compatible with) and includes all the restricted extras by default.

---

### Post by cpmman on 2010-10-31
Sorry if I confused you - just checking you had the codecs etc. for conversion which are in the restricted extras packages.

If so - I haven't needed it myself but I understand avidemux from the repositories is flexible.

Oops - beaten to it.

---

### Post by TheAmazingDave on 2010-10-31
Well I installed the ubuntu-restricted-extras package, and it didn't help. Same instant failure with YouTube upload, and same trouble with Photobucket.

Although I've now recognized that the problem with Photobucket only seems to affect Jpeg files, bitmaps and PNGs upload fine. WTF?

Installing avidemux right now. Do I need this to convert my files, or am I hoping that the bundled codecs alleviate the issue?

---

### Post by kaldor on 2010-10-31
> **TheAmazingDave said:**
> Installing avidemux right now. Do I need this to convert my files, or am I hoping that the bundled codecs alleviate the issue?

If I understand correctly, your files are in AVI format. I believe the restricted extras allows those to work. After all, I have absolutely no issues with my camera that uses .avi as well.

Edit:

If you are into multimedia production and such, there are 2 great Linux distros that come to mind. Ubuntu Studio and Fedora Creative Design. Take a look into those, maybe you'll run into less media issues :)

---

### Post by TheAmazingDave on 2010-10-31
> **kaldor said:**
> If I understand correctly, your files are in AVI format. I believe the restricted extras allows those to work. After all, I have absolutely no issues with my camera that uses .avi as well.

That is correct, my camera (just a simple point and shoot) records directly to an AVI. These files will not upload to YouTube or Photobucket.

Also, JPG files will not upload to PhotoBucket, but BMPs and PNGs will.

The only exception is in Chromium, where the AVI upload will start for YouTube but not complete. It has not made it past 14% on a ~75MB file, and often makes the ethernet disconnect.

---

### Post by kaldor on 2010-10-31
> **TheAmazingDave said:**
> That is correct, my camera (just a simple point and shoot) records directly to an AVI. These files will not upload to YouTube or Photobucket.

Also, JPG files will not upload to PhotoBucket, but BMPs and PNGs will.

That's very weird.. but I think I recall that problem a while ago when trying to share photos using PhotoBucket. Is there any "basic uploader" method?

Maybe you could create a [deviantART]("http://www.deviantart.com/") account for storing your uploads if all else fails. It's pretty easy and useful :)

Edit: Have you used Chrome instead of Chromium? They're pretty much the same, but Chromium is developmental while Chrome is stable. Maybe the latest Chromium builds have some issues with this? I never had problems at all uploading to YouTube.. but then again I haven't tried within the last 2 years.

---

### Post by TheAmazingDave on 2010-10-31
If it can help anyone help me, the video in question is here:

[http://files.theamazingdave.net/PIC_0712.AVI](http://files.theamazingdave.net/PIC_0712.AVI)

I slapped it on my host since I needed to get it posted, but would rather have it on my YouTube.

---

### Post by Swagman on 2010-10-31
Wow.. That Celica has seen better days.

You restoring it ?

---

### Post by TheAmazingDave on 2010-10-31
> **Swagman said:**
> Wow.. That Celica has seen better days.

You restoring it ?

Yea, it's a project that my friend owns, I'll be helping him put it back together properly. It's actually in great shape, it looks rough because most of the interior is out.

No rust, only a few minor dents. Engine runs fantastic and has less than 100k on it. He just installed a new muffler the day after the video so now the car sounds as it should.

Back to the issue at hand...

---

### Post by TheAmazingDave on 2010-10-31
> **kaldor said:**
> Edit: Have you used Chrome instead of Chromium? They're pretty much the same, but Chromium is developmental while Chrome is stable. Maybe the latest Chromium builds have some issues with this? I never had problems at all uploading to YouTube.. but then again I haven't tried within the last 2 years.

Didn't see this... I'll definitely try Chrome as opposed to Chromium. I'll give anything a shot at this point.

---

### Post by Verbeck on 2010-10-31
> **TheAmazingDave said:**
> If it can help anyone help me, the video in question is here:

[http://files.theamazingdave.net/PIC_0712.AVI](http://files.theamazingdave.net/PIC_0712.AVI)

I slapped it on my host since I needed to get it posted, but would rather have it on my YouTube.

may i download it, and try uploading it to youtube? (just to check)

---

### Post by TheAmazingDave on 2010-10-31
> **Verbeck said:**
> may i download it, and try uploading it to youtube? (just to check)

sure, for me it fails instantly

---

### Post by Verbeck on 2010-10-31
[http://www.youtube.com/watch?v=UVmMxsJZSf4](http://www.youtube.com/watch?v=UVmMxsJZSf4)

wth.. 75mb and not even a minute long!!

edit: is the video somehow broken??

---

### Post by TheAmazingDave on 2010-10-31
> **Verbeck said:**
> [http://www.youtube.com/watch?v=UVmMxsJZSf4](http://www.youtube.com/watch?v=UVmMxsJZSf4)

wth.. 75mb and not even a minute long!!

edit: is the video somehow broken??

I don't believe it to be. I have the camera record 640x480 @ 30 FPS.

---

### Post by wainbee on 2010-10-31
"The only exception is in Chromium, where the AVI upload will start for YouTube but not complete. It has not made it past 14% on a ~75MB file, and often makes the ethernet disconnect."

There is no way for file formats or restricted codecs to make an internet connection fail.  Is your internet connection wired or wireless?  This smells like an incompatible hardware driver for the network interface card or the wireless interface.  Many Vista machines had hardware built exclusively for Vista such that XP drivers would not work either.  Perhaps you could tell us a little bit about your computer, especially network hardware and what type of internet connection you have.

---

### Post by TheAmazingDave on 2010-10-31
> **wainbee said:**
> "The only exception is in Chromium, where the AVI upload will start for YouTube but not complete. It has not made it past 14% on a ~75MB file, and often makes the ethernet disconnect."

There is no way for file formats or restricted codecs to make an internet connection fail.  Is your internet connection wired or wireless?  This smells like an incompatible hardware driver for the network interface card or the wireless interface.  Many Vista machines had hardware built exclusively for Vista such that XP drivers would not work either.  Perhaps you could tell us a little bit about your computer, especially network hardware and what type of internet connection you have.

The computer is a dv9010us, with the only upgrade being that I opened it up and added the stock HP Bluetooth radio. The connection is wired, and didn't have any problem moving the file to my host via FTP.

---

### Post by TheAmazingDave on 2010-11-05
Alright, well thanks to all who tried to help. Looks like I'll stick with Vista. As slow as it is sometimes, it just works. None of these stupid hoops to jump through...

Maybe I'll try again after a few more releases.

Thanks all.

---

### Post by TheAmazingDave on 2010-11-05
Back at home, uploads working as they should.

Same dv9010us computer, same ethernet network connection, just Vista as opposed to Ubuntu.

I'll miss my Compiz effects, but if you polish a turd, it's still a turd. Regardless, I am still open to advice to get this solved. I'll leave the Linux partition alone in hopes that someone can provide a solution.

---

### Post by Verbeck on 2010-11-05
this is my last suggestion as i'm out of ideas :(

could try using the live cd/usb to upload? and if you need flash, install it separately from the sofware center instead of the entire restricted extras package (while in live session)

---

### Post by TheAmazingDave on 2010-11-05
I can try that. I haven't erased the USB stick I used to install yet.

---

### Post by Malcolm Waterman on 2010-11-05
I just tried to upload an AVI file onto Youtube from Firefox. So far it's up to 40% with an estimated 5 minutes complete and it seems to be working fine.'m using Ubuntu 10.04 and not 10.10 and my current flash software is Gnash.
The file I've tried uploading is slightly different, 61 MB, though approx. 3 minutes long.

Edit: The file seems to have uploaded successfully.

---

