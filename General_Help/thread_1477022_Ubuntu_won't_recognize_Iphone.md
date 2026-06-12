---
title: "Ubuntu won't recognize Iphone"
date: 2010-05-08
forum: General Help
---

### Post by Shadow12313 on 2010-05-08
So far I have been able to sync my Iphone songs with rhythmbox but, now ubuntu doesn't recognize my Iphone.  As a test I plugged in my old Ipod Nano and it did recognize that.  I plugged my Iphone into my windows 7 laptop and it worked so why doesn't ubuntu recognize it anymore?

Any help is greatly appreciated.

---

### Post by TheNerdAL on 2010-05-08
It doesn't recognize it at all, like there isn't no icon on the desktop for it or you can't sync?

---

### Post by Shadow12313 on 2010-05-08
There's no icon or any sign that it was mounted.

---

### Post by Shadow12313 on 2010-05-09
bump

---

### Post by Shadow12313 on 2010-05-23
bump

---

### Post by okey666 on 2010-05-23
When you plug it in for the first time, it must be unlocked, ie. on the home screen, not on the lock screen. I presume this is some kind of security thing. It should then appear on your desktop.

---

### Post by Shadow12313 on 2010-05-24
I tried doing that but, it did not work.  The iPhone knows it's plugged in but, Ubuntu does not.  Any other ideas?

---

### Post by Shadow12313 on 2010-06-04
Bump

---

### Post by leopadin on 2010-09-25
If you have a password set up on your device, **unlock it first** before connecting the USB cable, otherwise Ubuntu will not recognize it.

Please refer to [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by Ginsu543 on 2010-12-10
I have this exact same problem. I used to be able to plug in my iPhone 3GS and Ubuntu would recognize it and allow me to mount it to access its filesystem. Now, when I plug in my iPhone, my Ubuntu does not know it exists, although it shows up in lsusb, properly identified.

Reading the Ubuntu help file that leopadin linked, I think I may have found the problem. It says that Ubuntu can recognize the iPhone only up to iOS 4.0.1 without jailbreaking the iPhone. Ubuntu can access the filesystem with iOS 4.1 but not sync. Thinking back, I became aware of this problem after I upgraded the iOS from 4.1 to 4.2.1.

---

### Post by ray field on 2011-07-03
> **leopadin said:**
> If you have a password set up on your device, **unlock it first** before connecting the USB cable, otherwise Ubuntu will not recognize it.

Please refer to [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)


I just bought a 3GS with iOS 4.3.3 and despite what the above url holds, and every attempt to plug the phone in an unlocked state, Lucid refuses to recognize the iPhone.  I tried to install libimobiledevice1 but I get 

```
libimobiledevice1 is already the newest version.
libimobiledevice1 set to manually installed.
```

---

### Post by Akovia on 2011-07-05
Same problem here, though I am trying for the first time. Phone alerts when connected, but no sign from lucid. lsusb | grep Apple shows it's connected.

iphone 1 (v. 4.0.1)

---

### Post by ray field on 2011-07-05
Yesterday I came across a solution that works for me, with the help of [http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

unless there's some reason iFuse isn't desirable -- but now I can mount it and move files back and forth -- just moved some old photos to the iPhone, we'll see about getting mp3s onto it. curious if this works for you.

---

### Post by Akovia on 2011-07-06
> **ray field said:**
> Yesterday I came across a solution that works for me, with the help of [http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

unless there's some reason iFuse isn't desirable -- but now I can mount it and move files back and forth -- just moved some old photos to the iPhone, we'll see about getting mp3s onto it. curious if this works for you.

Thanks for the tip. I'm finding it difficult to find any solid info on interacting with an iPhone. Mine was a present and I wouldn't use it if I really had a choice, so for now I'm stuck and just trying to make the most of it. =\

So anyway, I am able to copy files to the iPhone now, but they are not recognized by the device. (not jailbroken, but would if again I could find some solid info to do so) I tried adding pics to the DCIM/100APPLE,
/Photos but they don't show. Actually now when I try to view the photos I had in there, the thumbs are fine but I get a black screen when I click on the photo. Controls still work but no picture.

I also tried some mp3s in a few folders to no avail. /iTunes_Control/Music, /iTunes_Control/Music/F00, /Downloads. It seems like there is no way to update the DB, or tell the phone to do so. I really wish I could get Banshee to work for music transfers, but I have updated to latest libimobiledevice and related, but still the same. Apparently it is not a Banshee problem as reported here. [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/705716]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/705716")

Hope you had better luck than me.

---

### Post by ray field on 2011-07-06
> **Akovia said:**
> Thanks for the tip. I'm finding it difficult to find any solid info on interacting with an iPhone. Mine was a present and I wouldn't use it if I really had a choice, so for now I'm stuck and just trying to make the most of it. =\

So anyway, I am able to copy files to the iPhone now, but they are not recognized by the device. (not jailbroken, but would if again I could find some solid info to do so) I tried adding pics to the DCIM/100APPLE,
/Photos but they don't show. Actually now when I try to view the photos I had in there, the thumbs are fine but I get a black screen when I click on the photo. Controls still work but no picture.

I also tried some mp3s in a few folders to no avail. /iTunes_Control/Music, /iTunes_Control/Music/F00, /Downloads. It seems like there is no way to update the DB, or tell the phone to do so. I really wish I could get Banshee to work for music transfers, but I have updated to latest libimobiledevice and related, but still the same. Apparently it is not a Banshee problem as reported here. [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/705716]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/705716")

Hope you had better luck than me.


I'm not unhappy with it -- the keyboard on my old Pre started to go, and as as much as I liked its UI, the lack of apps (and subpar performance of some of the most basic ones) made it clear it was time to move on. I would have preferred an Android, but they're too pricey compared to 49 bucks for the 3GS from AT&T.  For me, the apps really do make the thing, especially for reading, use of the GPS, browser stuff.

Anyway, I haven't played with the mp3s -- as much as I hate iTunes, which is a lot, I have a Windoze 7 partition & just bit the bullet & used iTunes to transfer mp3.

However, I'm not sure this is actually necessary: I had the same trouble as you did moving photos, but I Googled a resolution which worked for me -- there are a couple of database files which if you delete them, get recreated.  Once that's done, the photos you've imported, and their thumbnails, will become visible -- I'm not at home so I can't give you the link but it shouldn't be hard to find.  I don't know whether this will work for mp3s but it's probably worth looking into.

---

### Post by linuxuser12345 on 2011-07-06
That happened with my iPhone, too. Try updating your Ubuntu installation to the latest version, and then install the latest version of iOS.

---

### Post by Akovia on 2011-07-06
Thanks for the tip  again. I already hand edited the photo db file as a test and it worked. Knowing I can delete it and rebuild it makes sense, will give it a try.

> I'm not unhappy with it
I agree, it is a neat device, but I am very opposed to vendor lock-in, and the monopolization that goes with it. Id rather not use it for that alone.

I'm almost ready to give up on using Banshee to sync music. It seems there is a bit of a conundrum when it comes to using the most recent libimobiledevice. My system had libimobiledevice0 installed and from what I read it was supposed to support iPhones out of the gate, giving you an icon on the desktop and just work. I never saw the icon once so far, and read to make banshee work properly you need to use the latest libimobiledevice1. The problem is that if you try to uninstall libimobiledevice0, it removes Banshee as well. pfffft! (go figure)

Anyway, guess I'll put that on the back-burner for now. Now I'm trying to figure out how to get my *many* contacts transferred. It doesn't appear that the iphone supports vcards, and won't even receive a bluetooth beam from another phone. It also looks like transferring in a supported format is outta the question unless I jailbreak.

I will try every last resort to stay away from itunes. I just wish I could find a good place to help troubleshoot these problems. Most iphone questions on this board get little to no response, (understandably) and the libimobiledevice website is cryptic at best if not a dev. I really do hate mailing lists, but understand that it helps keep out the riff-raff. Same goes for banshee. Oh well I'm rambling now....

Thanks again!

---

