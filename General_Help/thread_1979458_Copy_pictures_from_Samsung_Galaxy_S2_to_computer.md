---
title: "Copy pictures from Samsung Galaxy S2 to computer?"
date: 2012-05-13
forum: General Help
---

### Post by k999 on 2012-05-13
Has anyone managed to copy pictures from their Samsung Galaxy S2 to their Ubuntu 12.04 computer?

First I tried Kies Air, but I have like 500 pictures, and the "download all" just doesn't to work. I select the folder and click OK, then nothing happens, no errors, no files copied. I can download one picture at a time, but I can't be bothered!

So I dug out a USB cable, and connected it. The phone only gets detected as an audio player. I've changed the phone's settings so that it should show up as a camera, but Ubuntu always detects it as an audio player. I wouldn't care if I could just copy the pictures, but it only shows up with lots of folders named 0000000a, 0000000b, 0000000c, etc... and they're all empty. No pictures to be found.

I tried to enable USB debugging, but it doesn't even seem to work on the phone.

Finally I installed gMTP, but it just crashes when I run it as my own user, and running it under SUDO it complains that the USB device vendorid:deviceid are unknown.

Sheesh, this was difficult!

---

### Post by typos1 on 2012-05-13
I have the same phone, all I do is plug in the phone's lead (micro usb to phone, standard usb to pc). Then I drag down the menu on the phone (the one where you turn on and off wifi etc) and hit the "usb connected" icon and then "connnect usb storage" then the phone shows as a usb device on the pc.

---

### Post by k999 on 2012-05-13
What software version is your phone running? Mine is Android version 4.0.3, what you're describing sounds more like the version I had before.

---

### Post by typos1 on 2012-05-13
Right, I havent upgraded to icecreamsandwhich yet. 

Cant see why theyd change how it interfaces with the pc though, mind you its evil google we re talking about here so anythings possible. Nothing online about changes in icecreamsandwich ? You tried googling it ?

---

### Post by jawilljr on 2012-05-13
Try [these instructions.](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/)

Hope it works.

Jerry

---

### Post by typos1 on 2012-05-13
OMG!-what a load of hassle. Trust Google, I really cant wait til the Android and Linux kernels merge and ubuntu phone comes out, then I can junk that Google rubbish and put a proper Linux OS on my phone.

---

### Post by k999 on 2012-05-13
Yes, this is a lot of hassle! And those instructions don't work either, mtp-detect hangs and eventually fails. It finds the device, but then it tries to connect, and that fails. Here's what it looks like when I run with sudo:

```
$ sudo mtp-detect 
libmtp version: 1.1.3

Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note.
   Found 1 device(s):
   Samsung: GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note (04e8:6860) @ bus 2, dev 17
Attempting to connect device(s)
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
OK.

```

So no luck there either... Thanks for the tip, though!

---

### Post by k999 on 2012-05-13
By the way, I noticed now that I only needed that command to get VID/PID, so I continued with the instructions, but it doesn't work anyway. Now, after I run "android-connect", the phone is mounted:

```
$ mount
...
mtpfs on /media/GalaxyNexus type fuse.mtpfs (rw,nosuid,nodev,allow_other,user=ubuntu)
$ ls -l /media/GalaxyNexus
ls: cannot access /media/GalaxyNexus: Transport endpoint is not connected
$
```

The ls command hangs until it times out or something, perhaps 30 or 60 seconds? Listing the media folder looks like this:

```
$ ls -l /media/
ls: cannot access /media/GalaxyNexus: Transport endpoint is not connected
total 0
d????????? ? ? ? ?            ? GalaxyNexus

```

---

### Post by k999 on 2012-05-13
Seems my remaining options are:

1) reboot to windows and use kies, or
2) install dropbox, google drive, or something like that on the phone and copy everything via some online service, or
3) get an ftp or scp client on the phone, and copy pictures that way.

What an utter pain.

---

### Post by typos1 on 2012-05-14
Great, maybe I wont be upgrading to icecream sandwhich then.

---

### Post by na5h on 2012-05-14
I use [Airdroid]("http://airdroid.com/") myself...great app, no hassle! Just search for it on Google Play/Android market.

---

### Post by hounddog32 on 2012-05-16
No useful insight here, mainly a "me too" - updated my Samsung Galaxy S2 to ICS and now I can't mount it to sync music with my desktop music library. I can add new albums one at a time with AirDroid, which is fine, but updating the library with a new selection is not realistic. Frustrating that something that is easy to do in Windows (since XP) is impossible to do on Ubuntu - I'm not used to saying that!

---

### Post by typos1 on 2012-05-16
> **na5h said:**
> I use [Airdroid]("http://airdroid.com/") myself...great app, no hassle! Just search for it on Google Play/Android market.

It IS hassle, there was no need for an app beffore, you jsut plugged it in pressed connect on the phone and bingo, now theyve made even the most basic thing a load of hassle. 

They probably did it so they can play adverts to you on the app. 

Google are just as evil as Microsoft and Apple.

---

### Post by loklaan on 2012-05-16
Doesn't ICS have *USB mass storage* mode?

Sorry for the lack of help. I thought this option would be the same with ICS (I am still using Gingerbread).

---

### Post by loklaan on 2012-05-16
Oh and I got rid of Kies and the bollocks Samsung flavoured MTP. I just use the Mass Storage mode.

---

### Post by cortman on 2012-05-16
I have the same phone on AT&T, not upgraded yet- this concerns me. What exactly is the procedure for using the phone as a flash drive? Does it not have a "mass storage" option?

---

### Post by na5h on 2012-05-18
> **typos1 said:**
> It IS hassle, there was no need for an app beffore, you jsut plugged it in pressed connect on the phone and bingo, now theyve made even the most basic thing a load of hassle. 

They probably did it so they can play adverts to you on the app. 

Google are just as evil as Microsoft and Apple.

Airdroid is not made by Google...and as far as I can remember, it is also ad-free. I suggest you give it a try, it is a very useful app! It is also good for lots of other things, such as managing your text messages and contacts.

For the record, my Samsung Galaxy Xcover connects just fine via USB...

---

### Post by typos1 on 2012-05-18
No, but Icecreamsandwich IS made by Google.

Simply plugging your Galaxy into you pc is much easier and simpler than messing about installing an app. Making it so you have to have an app too do the simplest thing is ridiculous. 

What next, an app so you can make phone calls ?

---

### Post by loklaan on 2012-05-18
> **typos1 said:**
> What next, an app so you can make phone calls ?

I believe there is: Skype. :popcorn:

I think [na5h]("http://ubuntuforums.org/showpost.php?p=11946146&postcount=17") was just helpfully suggesting a *workaround*. ;)

---

### Post by typos1 on 2012-05-18
Lol, haha.

Basic functionality has been taken away and its stupid.

Like I said, I cant wait til kernels merge and I can have Ubuntu phone.

---

### Post by loklaan on 2012-05-18
> **typos1 said:**
> Lol, haha.

Basic functionality has been taken away and its stupid.

Like I said, I cant wait til kernels merge and I can have Ubuntu phone.

I'm up for patiently waiting until a Ubuntu phone comes out. :)

---

### Post by typos1 on 2012-05-19
> **na5h said:**
> Airdroid is not made by Google...and as far as I can remember, it is also ad-free. I suggest you give it a try, it is a very useful app! It is also good for lots of other things, such as managing your text messages and contacts.

For the record, my Samsung Galaxy Xcover connects just fine via USB...

Airdroid is useless if your pc hasnt got wifi.

Has your Xcover got icecreamsandwich ?

---

### Post by na5h on 2012-05-21
> **typos1 said:**
> Airdroid is useless if your pc hasnt got wifi.

Has your Xcover got icecreamsandwich ?
Well, the PC itself doesn't actually require wifi...but you do need a wireless router that the phone can connect to (the phone and the PC need to be on the same LAN). 

As for the Xcover, it's got Gingerbread.

---

### Post by spillin_dylan on 2012-05-21
I think the cloud storage idea has been covered, but I actually like the Ubuntu One integration on my Galaxy S2.  I don't think I've ever plugged it in to my Ubuntu laptop....

---

### Post by Zvlwab on 2012-05-21
I don't have a Samsung Galaxy S2, but I do have an ICS rom running on my Desire Z.
When I connect my phone using a USB cable, I can simply slide down the message pane and click "Turn on USB storage".
Then Ubuntu mounts it on /media/ANDROID/ and I can browse my files (including pictures).

---

### Post by typos1 on 2012-05-21
I dont see the point of using the cloud if the two devices are nest to each other.

Maybe its not google that are the problem (this time), but samsung ?

---

### Post by hazelnut on 2012-05-27
No need for wifi. plug your phone into usb, select internet pass-through.  You will get an ip on a subnet that your pc can see. You can then use airdroid.  Awesome program, btw.  

With internet pass-through, you get much higher transfer rates than over wifi anyway.

---

### Post by xyzzyman on 2012-05-27
> **hazelnut said:**
> No need for wifi. plug your phone into usb, select internet pass-through.  You will get an ip on a subnet that your pc can see. You can then use airdroid.  Awesome program, btw.  

With internet pass-through, you get much higher transfer rates than over wifi anyway.

I believe internet pass-through is just an HTC option...

I still always thought that mass storage mode was the proper way for copying files on/off Android devices. As I haven't used ICS much, I hadn't realized it was moved, but here's how to enable it now: [http://www.jayceooi.com/2012/03/14/how-to-enable-usb-mass-storage-on-android-4-0-ics-samsung-galaxy-s2/](http://www.jayceooi.com/2012/03/14/how-to-enable-usb-mass-storage-on-android-4-0-ics-samsung-galaxy-s2/)

And also a reason of why they are moving to MTP instead. It makes sense as I do find it a PITA to lose access to 80% of my apps while plugged in, and as a side benefit you can install apps w/widgets to your SD card now. Unfortunately Ubuntu needs to get up to date with MTP support:

[http://www.androidcentral.com/ics-feature-mtp-what-it-why-use-it-and-how-set-it](http://www.androidcentral.com/ics-feature-mtp-what-it-why-use-it-and-how-set-it)

---

### Post by typos1 on 2012-06-04
A friend plugged his ICS Galaxy S2 into my 12.04 and it worked the same as my GB Galaxy S2-ubuntu still opened 2 windows, 1 saying a music player had been detected and one saying a digital camera had been detected and files were browsable just the same. There was also an error box that said the camera could not be opened.

---

### Post by lostoam311 on 2012-12-20
My issue is similar...  The PREVIEW of my pictures is Not showing up...  Just an icon for all 1,000 of my pictures...  If I right click the icon (after plugging my phone into my computer) I can click on 'preview', but I want to see all my pictures when I'm trying to pull them up on my computer...  

I'm running windows 7 on my laptop and Android 4.0.4 on my phone...

I had an HTC EVO 3D before and I was able to view small pictures when I plugged it into my computer...  

Please help, thanks

---

