---
title: "UNR Install Problems on 1201HAB"
date: 2010-01-05
forum: General Help
---

### Post by jeremy1138 on 2010-01-05
Hello folks!

I was trying to help a friend of mine install Ubuntu Netbook Remix on his new Asus Eeepc (model 1201HAB) today, and the install seemed to go fine but when I booted up the computer, I was disappointed to see that all was not right.  The computer is very very slow and sluggish and freezes every time I try to do an update or whenever I try to open the restricted drivers manager.  I'm not sure what the deal is with it.  I'm just wondering if anyone has had any similar problems and I was wondering what I might do to try to fix the problem.  I installed Ubuntu on the computer using a USB key which I prepared using the instructions found here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I used the Ubuntu usb-creator app to do it.  Like I said, the installation appeared to go fine but it's just so sluggish now that it's installed that I can't do anything with it.  Oh and the good news is that the wireless network card worked nicely out of the box so I can get on the intertubes with it without a problem.

OK I'm not sure what other info I should provide to help diagnose the problem; any help would be really appreciated.  I love Ubuntu, and I thought it would be really nice to get one of my friends going with it, but now I'm really upset that I've borked his computer and I don't know how to fix it.  Thanks!

---

### Post by jeremy1138 on 2010-01-06
Ok, well I took UNR off the computer and installed the regular desktop version of Ubuntu and it seems a little better but it still freezes up every single time I try to get updates.  The screen resolution won't set to the screens native resolution which is a 16:9 aspect, it instead gives me a generic 4:3 resolution that is stretched to fit the screen.  I really think the problem is with video drivers but I can't get an update to finish so that the computer will get the proper drivers itself and I'm unsure of how to manually do this.  Can I get some help?  Please?

---

### Post by spiderbatdad on 2010-01-06
I have no idea why your installation seems to be broken, but it sounds like you should try again with a new usb. I use a live-cd from 8.10 to run usb-creator, as  the program is broken on 9.10.
You might also consider easy peasy designed for the asus and built from ubuntu.

---

### Post by jlacroix on 2010-01-06
I am working with a friend that has this same netbook/issue. Any help would be appreciated.

---

### Post by jeremy1138 on 2010-01-06
> **spiderbatdad said:**
> I have no idea why your installation seems to be broken, but it sounds like you should try again with a new usb. I use a live-cd from 8.10 to run usb-creator, as  the program is broken on 9.10.
You might also consider easy peasy designed for the asus and built from ubuntu.

I have also tried creating the bootable USB with Unetbootin on Windows and I get the same problems.  I don't think it's a problem with the .iso used to create the bootable USB or with the process that I'm using the create said bootable USB.  I guess I'm going to have to try to put Windows back on the computer.  Hopefully I'll be able to put the DVD that was provided with the computer into an external dvd drive and get the computer to restore fully back to the way it was originally.  Right now the boot record is totally messed up and I can't get the computer to boot into windows or anything else for that matter.  I thought I'd be able to get some fairly prompt help on these forums as I used to a few years ago but it appears the Ubuntu Forums are not what they used to be.  Anyway, thanks to the people who did respond.

---

### Post by aelazenby on 2010-01-08
Ok, I have the same problem and have been playing a bit with it. I am still very green at Ubuntu, so roll with me for a touch. This is the problem and this is what I have found.

Problem:

[LIST]
[*]I put Ubuntu Netbook Remix (UNR) onto a Asus Eee 1201HA. Everything seemed to work ok, but the computer was moving very very slow.
[/LIST]

This is what I have found so far:

[LIST]
[*]The root of the issue seems to be the driver for the graphics chip set, which I believe is the GMA 500. I pulled this information from a forum discussion on the [Eeebuntu forum page]("http://forum.eeebuntu.org/viewtopic.php?f=1&p=23010"). That makes sense to me, seeing that everything else was working.
[LIST]
[*]I had never heard of the Eeebuntu project before, but it looks really nice. It is normal ubuntu on a Eee. On the 12 inch model, it is much nicer than the remix, at least I think so.
[/LIST]
 
[*]The people on Eeebuntu had no solution for finding a driver at this time. However they pointed to something interesting, [Jolicloud]("http://www.jolicloud.com/").
[LIST]
[*]From what I can tell this is just a reworked version of UNR. The interesting thing is that that they list the 1201HA as being fully functioning.
[/LIST]
 
[*]I installed Jolicloud and it worked perfectly out of the box. I did not get the chance to use UNR much, seeing that it did not work very well, but it seems very similar to me.
[/LIST]
My conclusion this far:

[LIST]
[*]It is a driver issue that is not letting the Asus Eee 1201HA work as it should, go figure.
[*]The driver must exists for Ubuntu (jolicloud has it), though I do not know how to get it into Ubuntu myself, or exactly were to find it for that matter.
[*]Eeebuntu seems very cool and I expect/hope that the next version will fully work on the the 12" Eee.
[*]Jolicloud works right now! and is almost the same thing as the UNR.
[/LIST]

And that is all I've got. Hopefully that is helpful to you. If we keep working together perhaps mainstream computers will again sell with ubuntu as the stock OS.

---

### Post by jeremy1138 on 2010-01-08
aelazenby, thanks for the response!  This is the same conclusion that I've come to and I've talked my friend into simply returning the 1201hab netbook in favor of another model that has a better reputation with linux.  I'm not sure what he's going to pick up but I'm sure that it will be better.  Thanks for the info on those other netbook oses as well.  Those are some really shiny nice netbook operating systems for sure.  I'm going to tell my friend about those as well so he can choose the one he likes best.

Anywho, I guess that's all there is to say on this problem.  It just isn't going to work with Ubuntu Netbook Remix right now and that's that.  Hopefully the problem will be corrected in the future but for now we need to work around the problem by either getting a different OS with better support or by avoiding the problem all together and getting a different netbook.

Thanks to everyone who replied!  I'll post back and let everyone know how things turn out with the new netbook that my friend is picking up over the weekend.

---

### Post by jeremy1138 on 2010-01-13
Well my friend sucessfully returned his 1201HAB for a 1005HAB over the weekend.  We installed Ubuntu Netbook Remix on it with no problems at all and everything is working great.  His wireless card worked out of the box with no fiddling around and there were none of the problems that we had with the 1201HAB model.

Also, I must say that Ubuntu Netbook Remix is a *very* nice operating system for a netbook.  I highly recommend it!

---

### Post by compu73rg33k on 2010-01-26
I also have a new 1201HAB and was a bit disappointed by the lack of support on Ubuntu. 9.10 froze quickly after logging into xserver so I tried 9.04. At least 9.04 didn't freeze, but the graphics were so sluggish that it was nearly unusable. UNR didn't preform much better.

I installed Jolicloud and can verify again that it has great support. Video works pretty smoothly and it can play SD videos. Unfortunately, contrary to what is listed on the website, it did not play 720p well at all. Way too jumpy.

Also on Jolicloud both the wifi and ethernet network cards worked out of the box. On 9.04 I had to install the backports package to get the network cards to work.

I wonder what Jolicloud is doing right where the standard flavor(s) of Ubuntu are failing? I hope 10.04 fixes these issues because tbh I prefer the standard Ubuntu over any UNR or UNR variant like Jolicloud.

---

