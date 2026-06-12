---
title: "tether android phone (mytouch) with laptop, using proxoid. I got it to work!!"
date: 2010-03-28
forum: General Help
---

### Post by rhythmiccycle on 2010-03-28
It took me a while to get this working, and all the post I could find on this forum are about iphones. So I just wanted to post how i got it to work here, for anyone else trying to tether ubuntu to an android phone

my phone is a mytouch, using the standard OS (i.e. not rooted)
I have a netbook running ubuntu netbook remix, karmic.

I got the info from these two pages:
[http://code.google.com/p/proxoid/wiki/installationPhone](http://code.google.com/p/proxoid/wiki/installationPhone)
[http://code.google.com/p/proxoid/wiki/installationLinux](http://code.google.com/p/proxoid/wiki/installationLinux)

here are the steps:

1) on the phone, go to the android market and install "Proxoid"

2) on the phone, go to "home" screen, then goto Menu->Settings->Application->Developpenent
Be sure that "USB debugging" checkbox is checked. 

3) on the pc in a terminal, run this code to make a file
```
sudo touch /etc/udev/rules.d/09-android.rules
```

4)open the file you just created by running this in a terminal
```
gksudo gedit /etc/udev/rules.d/09-android.rules
```

5)you should see an empty file, copy and paste these lines into the file, 
but replace the text userName, with the name you use to login to the pc as, this is what ever it says before the @ symbol in the terminal.
```

SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", MODE="0666", GROUP="userName"
SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666", GROUP="userName"
SUBSYSTEM=="usb", SYSFS{idVendor}=="04e8", MODE="0666", GROUP="userName"
SUBSYSTEM=="usb", SYSFS{idVendor}=="18d1", MODE="0666", GROUP="userName"

```
after you changed the user name, save and close the file.

**make sure the phone is plugged into the pc via usb at this point.

6)Then, restart udev by issuing the command
```
sudo /etc/init.d/udev restart
```

note:if you get an error here about the "device" not working right, or something like that, try moving on to step 9, and reboot the pc with phone plugged in, like it says in the note for step 9.

7)Download the Android SDK from [http://developer.android.com/intl/fr/sdk/index.html](http://developer.android.com/intl/fr/sdk/index.html)

8) extract the Android SDK somewhere where you can find it. it really doesn't matter where, but it need to be extracted.


9) "Tunneling" this is the step where i had errors the first time I did it. using the "cd" command in a terminal goto the "tools" subdirectory of the extracted Android SDK directory. then in the same terminal run the code ```
./adb forward tcp:8080 tcp:8080
```

note: the first time I ran the code i got an error,
if you get an error, reboot you pc with the phone pluged in. then goto the "tools" subdirectory of the extracted Android SDK directory. then in the same terminal run the code ```
./adb devices
```

on my pc it looks like this
```

mike@mike-laptop:~$ cd '/home/mike/Desktop/android-sdk-linux_86/tools' 
mike@mike-laptop:~/Desktop/android-sdk-linux_86/tools$ ./adb devices
List of devices attached 
SH96JP301879	device

```

if you are getting the device to show up,
run the code from before, and this time you shouldn't get the error,
```
sudo /etc/init.d/udev restart
```
and then
```
./adb forward tcp:8080 tcp:8080
```
 then move on to the next step.

10) In firefox, go to Edit->Preferences->Advanced->Network->Settings

set the ratio button to "manual proxy configuration" and the http proxy to "localhost" and the port to "8080"

(see attached image)

11) Finally, run Proxoid on your Android phone, click "Start" and start browsing ... from firefox of course



----the end----

please let me know if this helps anyone, or if you have any questions

---

### Post by mmmthmtskier on 2010-05-25
Newbie here.  My stuff:
PC- Dell Mini-9 with NBR 
Phone- Droid Eris(Verizon)

Was able to get a proxy connection with this tutorial and this other one: 
 [http://ubuntuforums.org/showthread.php?t=1436525](http://ubuntuforums.org/showthread.php?t=1436525)

My biggest problem was using the "cd" command and directing it to SDK correctly(the link above helped me figure out the correct sequence).  
For me it was:   cd Desktop/android-sdk-linux_86/tools/ .  You need to know where that file is :redface: .
Everything else was pretty much step by step.

Thanks for all the help!
By the way, all info was available using the search feature :rolleyes:

---

### Post by fiddlerdiehl on 2010-06-03
Thanks so very much for this useful thread! Just posting to let you know that I got this trick to work for the t-mobile mytouch slide on an asus eee running lucid.

---

### Post by hortstu on 2010-09-04
Anyone get this to work with an htc evo?

---

### Post by hortstu on 2010-09-09
So I managed to get a free USB tether using easy tether and 10.04.  It's a little slow but easy tether gives you all the directions and tells you exactly what to enter into the terminal.  This is for an HTC evo 4G.

If you're trying this method and can't figure it out I'll try and help.  PM me if I don't see your post, but be sure to post and send me the link.

---

### Post by Tim_Crandall on 2010-09-10
I'm trying to get this to work for my Android Incredible. I am getting stuck at the part with the cd code (I think that's what it's called) It's telling me "No such files in directory". Anyone who can talk me through this. I'm new to all of this and I'm not to brightest person when it comes to this stuff.

---

### Post by rhythmiccycle on 2010-09-11
> **Tim_Crandall said:**
> I'm trying to get this to work for my Android Incredible. I am getting stuck at the part with the cd code (I think that's what it's called) It's telling me "No such files in directory". Anyone who can talk me through this. I'm new to all of this and I'm not to brightest person when it comes to this stuff.

cd is a code that is like opening a folder from the command line. 


i think you are talking about this part

```

cd '/home/mike/Desktop/android-sdk-linux_86/tools' 

```

if that is the case then the error message you are getting means that you did not put the android-sdk-linux_86 folder on your desktop. 

it doesn't need to be on your desktop, but if its not then you need to change the cd code to point to where it is.

so at step 8 "extract the Android SDK" where did you extract it to?

---

### Post by aysiu on 2010-09-11
I'm glad you got it working, but FYI rooting is a lot easier than what you had to go through, and most rooted roms include the ability to tether.

---

### Post by rhythmiccycle on 2010-09-11
> **aysiu said:**
> I'm glad you got it working, but FYI rooting is a lot easier than what you had to go through, and most rooted roms include the ability to tether.

i'm afraid of rooting, because I read I could brick my phone, and the warranty will be voided. My cell phone is my one and only phone, so if I mess it up, i'm 'up the creek' so to say.

---

### Post by aysiu on 2010-09-12
> **rhythmiccycle said:**
> i'm afraid of rooting, because I read I could brick my phone, and the warranty will be voided. My cell phone is my one and only phone, so if I mess it up, i'm 'up the creek' so to say.
I have the original MyTouch 3G, and my warranty has already expired. I guess if you have a more recent MyTouch, you have a legitimate concern.

That said, the chances of bricking are extremely low to almost non-existent as long as you're able to follow directions.

Bricking chances are much higher for the G1, since you have to actual flash an updated radio and SPL, which if you don't do properly really can brick your phone.

"Bricking" warnings for the MyTouch (which does not require a new radio or SPL) are really just a token gesture so that people don't get angry at the rooted rom developers in the off-case they *do* decide to flash radio or SPL instead of just using Androot and then just flashing a new rom.

Still, it's your choice.

---

### Post by 3rdalbum on 2010-09-12
Er... what exactly is this howto thingy for? I know you're saying "tethering", which I understand is the process of using your phone as a mobile broadband modem.

If I want to tether my Android phone (HTC Desire), I first turn on mobile broadband from the Settings, then plug in my USB cable. The phone asks me whether I want to charge, sync, mount the phone as a disk, or do USB tethering. I choose that.

Network Manager then shows "usb0" is connected, and I can use Firefox to surf the web on Ubuntu through my phone's connection.

My phone also allows me to do "wifi tethering" which I have not tried yet.

So what exactly does your HOWTO do? Is it for reverse-tethering or something?

---

### Post by rhythmiccycle on 2010-09-12
> **aysiu said:**
> 
 the chances of bricking are extremely low to almost non-existent as long as you're able to follow directions.


okay, I have a myTouch (original, I think, from t-mobile).

can you give me a link to a page that gives the directions.

---

### Post by rhythmiccycle on 2010-09-12
> **3rdalbum said:**
>  The phone asks me whether I want to charge, sync, mount the phone as a disk, or do USB tethering. I choose that.


with a mytouch, the only options are "mount" and "don't mount", 

so I guess with the HTC Desire none of these steps are needed.

---

### Post by aysiu on 2010-09-12
> **rhythmiccycle said:**
> okay, I have a myTouch (original, I think, from t-mobile).

can you give me a link to a page that gives the directions.
Here are instructions:
[http://wiki.cyanogenmod.com/index.php?title=Full_Update_Guide_-_HTC_Magic_%2832B%29](http://wiki.cyanogenmod.com/index.php?title=Full_Update_Guide_-_HTC_Magic_%2832B%29)

Apparently with Androot, it's even easier to root than when I did it months ago.

I used this method instead, which was also easy, and watching a YouTube video of the process made me feel a lot better that it wasn't too difficult:
[http://www.youtube.com/watch?v=GhVXmq15TbI](http://www.youtube.com/watch?v=GhVXmq15TbI)

---

### Post by Sub101 on 2010-09-12
> **aysiu said:**
> I'm glad you got it working, but FYI rooting is a lot easier than what you had to go through, and most rooted roms include the ability to tether.

Tethering on rooted phones is very easy, and Rooting an android phone is generally easy too. And I believe Froyo (Android 2.2) is supposed to have tethering built it, but I believe some carriers are removing it.

---

### Post by rhythmiccycle on 2010-09-12
thanks aysiu, I'm going to look into that, my warranty runs out in a couple months.

---

### Post by Tim_Crandall on 2010-09-16
> **rhythmiccycle said:**
> cd is a code that is like opening a folder from the command line. 


i think you are talking about this part

```

cd '/home/mike/Desktop/android-sdk-linux_86/tools' 

```if that is the case then the error message you are getting means that you did not put the android-sdk-linux_86 folder on your desktop. 

it doesn't need to be on your desktop, but if its not then you need to change the cd code to point to where it is.

so at step 8 "extract the Android SDK" where did you extract it to?


I extracted to my home folder. I tried moving it to my desktop, but I think I'm still getting something wrong with the code. Step 9 is what confuses me. Am I suppose to add something else to the code that is posted in the directions?

Sorry for the delayed reply. I work a lot. Thank you for your help!

---

### Post by Sub101 on 2010-09-16
> **Tim_Crandall said:**
> I extracted to my home folder. I tried moving it to my desktop, but I think I'm still getting something wrong with the code. Step 9 is what confuses me. Am I suppose to add something else to the code that is posted in the directions?

Sorry for the delayed reply. I work a lot. Thank you for your help!

If you extracted to your home folder then you need to run, in a terminal, something like;

```
cd $HOME // Places you in your home folder
cd android-sdk-linux_86/tools // Places you in the tools directory of the sdk

```

In this tools folder there should be a file named 'adb'. Running the command Rythmiccycle has given; ```
./adb forward tcp:8080 tcp:8080
```

means run the file 'adb' with the what are essentially 'variables' given.

If this doesnt work kindly post the error you are getting.

---

### Post by Hoopz on 2010-09-26
I got this working with my lg ally.  However I can't go to https: websites and I can't download ubuntu updates.  Any ideas?  If I had to guess I would say Https uses a different port then 8080.

---

### Post by rhythmiccycle on 2010-09-27
> **Hoopz said:**
> I got this working with my lg ally.  However I can't go to https: websites and I can't download ubuntu updates.  Any ideas?  If I had to guess I would say Https uses a different port then 8080.

to get updates, and to get the internet to work on more than just firefox, you can set up the same proxy setting in:
system> Preferences > network proxy 

then go to manual settings, using the same set up as Firefox.


just be sure to set it back to "direct internet connection" when you want to use normal internet again.

you don't need to change the 8080 part

---

### Post by starwed on 2010-10-20
> I got this working with my lg ally. However I can't go to https: websites and I can't download ubuntu updates.

For https, make sure you check "use for all protocols" in Firefox.  (Or manually enter exactly the same info in the https field, of course.)

Also, just wanted to let folks know that someone created an altered version of Proxoid from the source: [SuperProxoid](http://www.supermind.org/blog/660/solved-connection-reset-problems-with-proxoid).  It fixes the "Connection Reset" issue that would occur far too often for me.

---

### Post by farmerjohn73 on 2011-03-05
hi,

A very nice tutorial.  I am using Motorola quench xt3.  I tried your tutorial to tether my android device to ubuntu.

At step 9: when i use "./adb devices" command, adb is initializing but is not displaying my device.  Not even if I restart.

when I type "lsusb", it is displaying my screens as follows.

Bus 005 Device 003: ID 06a2:0033 Topro Technology, Inc. USB Mouse
Bus 005 Device 002: ID 12d1:140b Huawei Technologies Co., Ltd. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0489:c001 Foxconn / Hon Hai 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Of these, i think **Bus 001 Device 007: ID 0489:c001 Foxconn / Hon Hai** is my device. (I was not supplied with usb cable with package, I bought it from the service centre)

 I used this ID 0489 in dev rule files, and restarted the udev but still my device is not getting listed.

without getting recognised, tcp forwarding is not working.  says "no device found."

what should I do?   

Is there a way to add my phone to any list of devices on ubuntu?

I am going nuts to tether this device to my ubuntu 10.04.

Kindly somebody help me..

thanks in advance.

---

### Post by farmerjohn73 on 2011-03-07
No replies yet.  Some one please respond ...

---

### Post by sydsverre on 2011-03-11
i have the droid2 and at first i used droid tether sv which worked pretty good. 
(i have posted the link below if anybody want to tether this way, it should work for any android phone)  but last week i ordered a bluetooth dongle on ebay for 50 cents and after i plugged it in i noticed that my droid network popped up under available networks. when i connected to it it linked up and started tethering, no root, no cords, no hasle. thank you ubuntu! :D once again you do something for me automatically before i even thought of it!

[http://androidnexus.com/guides/tether-your-droid-or-incredible-to-ubuntu-or-fedora-pc-over-usb](http://androidnexus.com/guides/tether-your-droid-or-incredible-to-ubuntu-or-fedora-pc-over-usb)

---

### Post by Sub101 on 2011-03-11
> **farmerjohn73 said:**
> hi,

A very nice tutorial.  I am using Motorola quench xt3.  I tried your tutorial to tether my android device to ubuntu.

At step 9: when i use "./adb devices" command, adb is initializing but is not displaying my device.  Not even if I restart.

when I type "lsusb", it is displaying my screens as follows.

Bus 005 Device 003: ID 06a2:0033 Topro Technology, Inc. USB Mouse
Bus 005 Device 002: ID 12d1:140b Huawei Technologies Co., Ltd. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0489:c001 Foxconn / Hon Hai 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Of these, i think **Bus 001 Device 007: ID 0489:c001 Foxconn / Hon Hai** is my device. (I was not supplied with usb cable with package, I bought it from the service centre)

 I used this ID 0489 in dev rule files, and restarted the udev but still my device is not getting listed.

without getting recognised, tcp forwarding is not working.  says "no device found."

what should I do?   

Is there a way to add my phone to any list of devices on ubuntu?

I am going nuts to tether this device to my ubuntu 10.04.

Kindly somebody help me..

thanks in advance.


What worked for me is:

```
cd android-sdk-linux_x86/platform-tools
sudo ./adb kill-server
sudo ./adb start-server
adb devices
```

Also make sure you have development mode turned on in the phone. 
(Settings -> Applications -> Development -> USB Debugging)

---

### Post by farmerjohn73 on 2011-03-18
thanks, guys, Got it working ! :D

But it worked only after updating the sdk by running 'android' from plat-form tools and by changing the vendor id on android rules files to the cable id instead of motorola id.  

But to connect to internet, every time I need to change to the platform tools directory and forward tcp.  Is there a way to automate this?

Pls guide.

---

### Post by 3rdalbum on 2011-03-18
> **rhythmiccycle said:**
> with a mytouch, the only options are "mount" and "don't mount", 

so I guess with the HTC Desire none of these steps are needed.

Ahh, I think it might be because I bought my phone from eBay rather than from the carrier. Just for the record, Android 2.2's wifi tethering option (when available) works quite well, and I've also done wifi tethering using a Nokia E63 and a free program from the Ovi store; so if you could find a similar program on the Android Market you'd be set even if the inbuilt wifi tether option is disabled.

---

### Post by farmerjohn73 on 2011-03-28
> **farmerjohn73 said:**
> thanks, guys, Got it working ! :D

But it worked only after updating the sdk by running 'android' from plat-form tools and by changing the vendor id on android rules files to the cable id instead of motorola id.  

But to connect to internet, every time I need to change to the platform tools directory and forward tcp.  Is there a way to automate this?

Pls guide.


I got that working with help of proxoid.  but it kept disconnecting often.  so I did some research and changed my android OS to 2.2 with cynogenmod.  It has wifi tethering and i am testing it.  Hope it will work !

---

