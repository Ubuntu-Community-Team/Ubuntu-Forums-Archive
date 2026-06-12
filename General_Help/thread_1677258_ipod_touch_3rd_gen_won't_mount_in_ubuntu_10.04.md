---
title: "ipod touch 3rd gen won't mount in ubuntu 10.04"
date: 2011-01-28
forum: General Help
---

### Post by alex_dc on 2011-01-28
I have a 3rd gen 32g ipod touch with the latest firmware and restored to factory default settings. When I plug in the device via USB it will not mount. after plugging in the ipod my dmesg is as follows:

```
[  399.300032] usb 2-1: new high speed USB device using ehci_hcd and address 5
[  399.455746] usb 2-1: configuration #1 chosen from 3 choices

```

And lsusb shows the device as:

```
Bus 002 Device 005: ID 05ac:1299 Apple, Inc. 
```

The OS is obviously recognizing the device as an Apple product, but beyond that I don't know.

The device will connect fine with windows machines. I have not tried using it with Wine + itunes as I know that itunes under wine is buggy at best.

Any help on this issue is appreciated!

Thank you

---

### Post by newspaper on 2011-02-01
I second that. It mounted a few times before, then I installed iTunes under wine. Now it's not being recognized under ubuntu on any other lucid PC either. 

Works fine under iTunes-Mac/Windows. 

As I see it, something must have changed inside the iPod touch only, as it was working fine on a lucid till few days back.

Regards.

---

### Post by cascade9 on 2011-02-01
Updating the firmware can break linux compatibility. Blame apple for that, and remember this if/when you go to buy a new media player.

---

### Post by newspaper on 2011-02-01
But I did not update the firmware, it's the same 4.2.1 from the start... :(

---

### Post by markling on 2011-02-01
Why can't I even charge my Ipod with Ubuntu? Is it because Apple is pants?

---

### Post by moody_mark on 2011-02-01
Folks you may want to upgrade your libimobiledevice package. Not sure if this will affect iPods but as it runs the same firmware as iPhones then its likely.

We have a iPhone at home here and it worked just fine, mounting in Ubuntu, we could transfer music to / from and copy photos and videos from the device. We upgraded to ios 4.2.x and it stopped working. I found a useful thread [here]("http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421") which I unfortunately omitted to record what I done, but it was roughly the following proceedure:

- added the ppa:pmcenery/ppa repository
- done a apt-get upgrade etc

```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

```

- used synaptic to uncheck libimobiledevice0 and check libimobiledevice1
- possibly rebooted (cant remember now)

Hope this might help some of you

---

### Post by newspaper on 2011-02-02
> **moody_mark said:**
> Folks you may want to upgrade your libimobiledevice package. Not sure if this will affect iPods but as it runs the same firmware as iPhones then its likely.

We have a iPhone at home here and it worked just fine, mounting in Ubuntu, we could transfer music to / from and copy photos and videos from the device. We upgraded to ios 4.2.x and it stopped working. I found a useful thread [here]("http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421") which I unfortunately omitted to record what I done, but it was roughly the following proceedure:

- added the ppa:pmcenery/ppa repository
- done a apt-get upgrade etc

```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

```

- used synaptic to uncheck libimobiledevice0 and check libimobiledevice1
- possibly rebooted (cant remember now)

Hope this might help some of you
I can confirm, that using the ppa version and using libimobiledevice1 works! cheers!!!!

---

### Post by moody_mark on 2011-02-04
Your welcome, please mark the thread as solved then it helps others when searching the forums, also on google searches too.

---

### Post by dpwilson on 2011-02-05
Thanks Mark, I spent hours and hours doing websearches and trying everything from a-z and after a couple minutes here worked.  No more booting up Windows for me.:p

---

### Post by markling on 2011-02-06
False Alarm!

Seems my cable had gone kaput. Much apologies. It may have been the case that using an iPod with Ubuntu used to be pants. But it actually now seems rather good. Well, about as good as it gets in my limited experience of these things.

I still think Apple's pants though (because I can't copy my .flac files to my iPod). Am I allowed to say that? Oops. Aren't I naughty.

---

### Post by cascade9 on 2011-02-08
> **markling said:**
> I still think Apple's pants though (because I can't copy my .flac files to my iPod). Am I allowed to say that? Oops. Aren't I naughty.

Even if you could copy them, the ipod wont play them. Apple dont like open source audio codecs. 

You might be able to install roxkbox on your ipod if you really want to play flacs- 

[http://www.rockbox.org/](http://www.rockbox.org/)

---

