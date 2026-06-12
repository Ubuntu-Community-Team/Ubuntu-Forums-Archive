---
title: "Blackberry charging"
date: 2006-06-12
forum: General Help
---

### Post by tfandango on 2006-06-12
Hi-
I have a blackberry that charges off the USB.  This works fine in Windows, but the blackberry complains when I'm booted into Linux.  It says:

"USB charging current is not suffcient.  Verify that your handheld is connected to a powered USB charging source and that the proper USB driver is installed."

I know it's powered, but I suspect it's the latter part.  The Blackberry USB driver is not installed because, as far as I know, it doesn't exist for Linux.  Has anyone figured out a way to charge their blackberry via USB?  I suppose I can just plug the darn thing into the wall.  But I figured I should ask first.

-thanks!
troy

---

### Post by shadow07 on 2006-06-18
I have been using various linux distro's for a while, without any luck on finding any resolution or workaround.  I have tried to look for an "ndiswrapper" equivilent.  One does not exist.  The Windows driver instructs the USB port to supply more power to the Blackberry device, as well as instructs the Blackberry that there is a power increase with the USB connection to charge the battery.  Since a driver doesn't exist for linux, you will always see this messege.

However, IF you feel like waiting about 8-10 hours, you can leave your Blackberry plugged in, and it will charge.  Just VVVVEEEERRRRYYYYY slow.

---

### Post by thoffland on 2006-08-16
I was having this same issue, hopefully there will be a fix for it eventually.

---

### Post by shadow07 on 2006-08-16
@thoffland:

I don't think this will happen any time soon.  RIM doesn't have any solution for Linux users, as most email clients (Corporate that is) are not supported in a *nix environment.  Until then, we are left to using Windows, or VMware Workstation, to charge and backup our BlackBerries with Desktop Manager.

---

### Post by thoffland on 2006-08-20
> **shadow07 said:**
> @thoffland:

I don't think this will happen any time soon.  RIM doesn't have any solution for Linux users, as most email clients (Corporate that is) are not supported in a *nix environment.  Until then, we are left to using Windows, or VMware Workstation, to charge and backup our BlackBerries with Desktop Manager.

Are you able to charge/sync with VMware? I had mine setup but the usb connection would flicker connected/not-connected. I have a win2K server I play with and have been using that to charge and sync, but I'd really like to have everything taken care of with Ubuntu.

---

### Post by shadow07 on 2006-08-21
When VMware Workstation 5.0 was released, no.  I have not tested with Workstation 5.5.x yet.

---

### Post by saracen on 2006-08-23
[how about this?]("http://www.voncrud.com/?p=133")

---

### Post by sfischer on 2006-09-22
That url at least hits the nail on the head in terms of the device requirements.  Problem is, it doesn't effect a solution - basically recommends retrying til it works (wish and a prayer)

4.x (OS level) BlackBerry handhelds require 500mA to charge.  

You need to have the BlackBerry device driver (for windows) installed natively for this to work.  Lots of attempts I've seen with vmware haven't been successful at all.  

So, unless there's a switch that can be specified to force the usb port to 500mA, or unless RIM publishes the spec for their USB driver, we're stuck...

---

### Post by DoctorMO on 2006-12-08
If someone with a windows machine can use usb snoopy to see what windows is sending to the blackberry when it's plugged in because:

1) the blackberry tells the computer how much power it needs, it's not the computers job to do this.
2) the blackberry is configured to recognise something in the serial usb connection that tells it it's a valid connection and it can begin drawing full power.
3) the blackberry then tells the computer it needs more power.

this is the most ridiculous thing I've ever seen, it undermines the point of usb with no good reason what so ever, in short it's a lieing device. bad bad bad.

unfortunately I only have a linux machine so I can't do anything at all, not even sync, not once, not charge. I'm screwed.

---

### Post by cdfrey on 2006-12-29
You can now charge your Blackberry natively in Linux.

The Barry project has just released the standalone utility bcharge, which will use libusb to scan your USB devices for BlackBerries, and set them to 500mA.

You can find the SourceForge news announcement here: [http://sourceforge.net/forum/forum.php?forum_id=648040](http://sourceforge.net/forum/forum.php?forum_id=648040)

You can find the Barry project at [http://sourceforge.net/projects/barry](http://sourceforge.net/projects/barry) and [http://www.netdirect.ca/software/packages/barry/index.php](http://www.netdirect.ca/software/packages/barry/index.php)

Happy New Year, and happy charging! :-)

---

### Post by sanicki on 2007-02-28
Anyone know if Barry will let me use my Blackberry as a tethered modem? Also can someone please give me a quick and dirty on compiling Barry for Edgy? I'd hate to get stuck on that tangent while I'm on this task. Thanks in advance for any help.

Also, has anyone tried ndiswrapper with the drivers at [http://webpages.charter.net/gwgaston/BBTools.html?](http://webpages.charter.net/gwgaston/BBTools.html?) Any successes?

---

### Post by ssc351 on 2007-07-01
> **sanicki said:**
> Anyone know if Barry will let me use my Blackberry as a tethered modem? Also can someone please give me a quick and dirty on compiling Barry for Edgy? I'd hate to get stuck on that tangent while I'm on this task. Thanks in advance for any help.

?

Same deal...would love to have tethered modem...there is way to do it through windows which I found at blackberryforums.com but there must be a way in linux.

---

### Post by XulluX on 2007-07-24
> **sanicki said:**
> Anyone know if Barry will let me use my Blackberry as a tethered modem? Also can someone please give me a quick and dirty on compiling Barry for Edgy? I'd hate to get stuck on that tangent while I'm on this task. Thanks in advance for any help.

Also, has anyone tried ndiswrapper with the drivers at [http://webpages.charter.net/gwgaston/BBTools.html?](http://webpages.charter.net/gwgaston/BBTools.html?) Any successes?

No barry does not allow tethering, just as blackberry desktop manager does not allow you to tether. The tethering software is carrier specific, like i use verizon wireless and the software is VZAccess manager.  (Sprint uses something else, i don't know)  but i have heard of users setting there blackberry up as an modem and dialing out using kdial.  search the site for more info.

---

### Post by usererror on 2008-01-23
I just installed the berry utils + berry libs .deb package from the Berry sourceforge page, i am please to say it auto detects my 8800 series blackberry and is charging at normal speed on the USB port!

---

### Post by crtlbreak on 2008-07-10
I have an 8700V and with all the barry utils and libs installed I can charge (normal rate), backup and sync with evolution contacts. Awaiting the memo, tasks and calendar sync now.
One would think that the Blackberry (which is native linux!) would be easier to sync with a linux box - instead the commercial pressure on RIM to create microsoft sync software was greater than producing native linux sync software.
the mind boggles!! :confused::confused::confused:

---

