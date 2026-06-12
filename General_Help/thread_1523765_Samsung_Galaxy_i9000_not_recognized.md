---
title: "Samsung Galaxy i9000 not recognized"
date: 2010-07-04
forum: General Help
---

### Post by gidovans on 2010-07-04
Hello,

Just got my new Samsung Galaxy i9000 phone. When connecting to my laptop with an USB cable, the phone says "USB Connected", but Ubuntu does not see my phone.

I am using Ubuntu not yet for a long time, so I need some help here.

My laptop runs 10.04

Thanks already,
Gido

---

### Post by clrg on 2010-07-04
What would you like to do once your phone is connected?

---

### Post by gidovans on 2010-07-04
I want to transfer mp3 files from my laptop to the sd card in the phone

---

### Post by clrg on 2010-07-04
I see. Honestly, I don't know the solution to your problem. As a workaround, do you have and SD card slot? You could simply plug the card in there and transfer the files directly. That would be faster, too.

---

### Post by gidovans on 2010-07-04
From my laptop the only option is an USB port. I guess it is somekind of driver issue. I will google some more to see if there is a solution

---

### Post by seraerie on 2010-07-05
The phone won't auto-mount.

You need to pull down the notifications menu and hit the USB/Mount thingy and it will then proceed to make the internal memory available for you.

Works out of the box for me on Ubuntu 10.04.

---

### Post by TheBadger on 2010-07-08
Ive connected my phone with USB cable, phone says it is connected, it has the usb logo in the top corner


but nothing has happened on ubunutu...
help!

---

### Post by phyre-x on 2010-07-08
Hi, 

I too am struggling with the samsung galaxy on ubuntu. I can get the phone to mount fine when I enable it as mass storage (settings --> about phone --> USB Settings --> ask on connection)

When the phone is plugged in it will then ask how to connect. choose mass storage for a safe option. once connected you need to open the notification bar on the phone and mount the device. This should work for mass storage.

Only point I've had doing it this was is F-Spots insatiable need to try and import the camera part of the phone! 

I was wanting to use the MTP mode on the phone so that Banshee would detect it and make my syncing life so much easier but this doesnt happen. Before I started fiddling, FSpot thought the phone was still a camera and treated it as such when connected in MTP mode. A bit more digging and the phone appears in gnome-device-manager as on the screen shot. 


I've attempted to edit the files in /etc/share/media-player-info/samsung-galaxy.mpi to match the result of lsusb command when connected as MTP device but no Joy, now nothing loads when in MTP connection mode.

Any help or advice on where to go with this would be great, seems a shame that it wont all just "work".

Cheers for now,

Matt

---

### Post by mikeashelby on 2010-07-09
Same issue this end: Rhythm box does 'see' it, but as an unknown device with 0bytes of space...

guessing we need to wait for the mlt8 lib to be updated by some awesome person...

---

### Post by gator6666 on 2010-07-12
I have found solution for this problem :

#lsusb
Bus 001 Device 005: ID 04e8:681c Samsung Electronics Co., Ltd

Enable USB Debugging on your phone. 
Go to Menu -> Settings -> Applications -> Development and enable USB Debugging.

---

### Post by mikeashelby on 2010-07-15
Oh... I got all excited when I saw this, but alas, mine at least isn't showing up as a media player. It works, even without USB debugging (if you select mass storage) but this way I don't even get the option to show it as a media player :(

Again, to point out that Rhythm Box will show the device, but as having 0bytes of storage and no name... same happens in both media device and kies mode.

Any further guesses?

---

### Post by lymanjayan on 2010-07-15
Your problem is very different. I think you have to check your usb drivers. Check its working or not. If its not then you have to install usb drivers by simply going in hardware drivers or by rollback these drivers. If usb driver is already install then you must check your system configuration.

---

### Post by tribaal on 2010-07-16
Here are the exact steps for mine to be seen:

- Plug cable. (device says "USB connected" and an USB logo appears).
- On the phone, pull the notification area.
- Tap the USB notification
- Select "Mount".

Voilà!

To remove:
- Eject the mass storage on your computer (right-click -> Eject)
- On the phone: pull down the notification menu
- Tap the USB notification item
- Choose "unmount"

Voilà!

Hope this helps. Enjoy your phone :)

- Trib'

---

### Post by mikeashelby on 2010-07-16
Cheers tribaal - but I'd got that far! As I say, my galaxy s comes up with a menu asking how I'd like to connect my device, Kies, Media Player, Mass Storage, or PC internet.

Selecting Mass Storage works fine, but no good for using syncing.

Selecting Media Player doesn't work. I tried doing the mtp-detect and that gave me this:

```
libmtp version: 1.0.2

Listing raw device(s)
Device 0 (VID=04e8 and PID=68a9) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
   Found 1 device(s):
   04e8:68a9 @ bus 1, dev 27
Attempting to connect device(s)
ignoring usb_claim_interface = -110PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Connection timed out
outep: usb_get_endpoint_status(): Connection timed out
usb_clear_halt() on IN endpoint: Connection timed out
usb_clear_halt() on OUT endpoint: Connection timed out
usb_clear_halt() on INTERRUPT endpoint: Connection timed out
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
Unable to open raw device 0
OK.

```

lsusb gives:


```
Bus 007 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0819:0101  
Bus 005 Device 002: ID 056a:0000 Wacom Co., Ltd PenPartner
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 04a9:10b6 Canon, Inc. PIXMA iP4300 Printer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 027: ID 04e8:68a9 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any ideas?

---

### Post by jgorkos on 2010-07-16
I struggled with this too.  There is one step left on the phone after you plug it in that you need to take.

Here's how I got it to work, using Lucid Lynx Kubuntu.  Surely a Gnome desktop will be similar.

1)  On the phone, go to Settings->Applications->USB Settings and select the "Mass Storage" Options.
2)  Go back to Settings->Applications->Development and select "Stay Awake"

3) Plug in your USB cable to the phone and computer.
The phone will say "USB Connected in the status bar at the top, and a USB symbol will appear.
4) Drag down the notification bar from the top and hit the "USB Connected:  Select to copy files to/from your computer"
5)  You get a new window with "USB Connected:  You have connected your phone to your Computer via USB.  Select "Mount" if you want to copy files between your computer and your phone's SD card."   Select MOUNT.

6) Your notification applet on your computer will squawk about TWO new drives being attached.  There will be a little one, and a big one.  Mount the bigger of the two.

There will be a selection of existing directories/folders (if you think folders, stay off my lawn):
Android
Bluetooth
DCIM
kindle
mobi_drm
sd
slacker
twc-cache

If you want to add music, create a new directory (folder, youngster) called "Music" and copy your music into it.
Don't forget to use the device notification applet/command line/etc to unmount the drive when you're done copying.
7) Finally, drag down the notification bar on the phone again and hit "Turn off USB Storage" to tell the phone to stop making the SD card available to the host PC.  After you confirm that, your card will be scanned for new media, and it will be available for your consumption via the Music Player.

Enjoy your new Galaxy S/Vibrant/Whatever your carrier calls it.  I know I am.

John Gorkos

---

### Post by jgorkos on 2010-07-16
> **jgorkos said:**
> I struggled with this too.  There is one step left on the phone after you plug it in that you need to take.
6) Your notification applet on your computer will squawk about TWO new drives being attached.  There will be a little one, and a big one.  Mount the bigger of the two.

John Gorkos

A little clarification on this.  My phone is a Vibrant from T-Mobile, model number SGH-T959, and has "Galaxy S" written on the back.  Mine came with a 2GB mini-SD card and 16GB of internal storage.  When mounting the disks, the larger volume will be the internal phone memory, while the smaller will be the SD card.  In the case of T-Mobile, they sell the phone with an HD AVI of _Avatar_ on the SD card.  Of course, it's DRM protected, and T-Mobile can DIAF as far as I'm concerned for poisoning my phone with DRM content, but whatever.  I unmounted my SD card, pulled it out of the phone and put it in a SD reader, backed up the Avatar image to my desktop, and filled the 2GB card with music.  Again, I created a "music" directory in the root of the card, and copied my music (in individual directories, by artist, etc) into that.

Good Luck.
John

---

### Post by mikeashelby on 2010-07-17
Cheers John,

I'm not sure if I've been saying this right, but I've always been able to copy files to my computer setting the galaxy s as a 'mass storage device'.

The problem is that there is an option for calling it a media player - which should allow you to do all the clever syncing that you can do with Zen's and apple's efforts - and that option doesn't work. It appears in RhythmBox, but doesn't actually do anything - that is, it's not recognising it.

Now, I have just found a page about the libmtp compatibility: [http://libmtp.sourceforge.net/compatibility.php]("http://libmtp.sourceforge.net/compatibility.php")

So, it seems that at this time, it's not actually compatible, and wasn't able to blag it's way through.

Guess we're all stuck with the mass storage option for now :(

---

### Post by Tech2077 on 2010-07-18
I'm on a amd64 bit version of ubuntu and this doesn't work, does anyone else have amd64 that this works on.

---

### Post by jgorkos on 2010-07-19
> **Tech2077 said:**
> I'm on a amd64 bit version of ubuntu and this doesn't work, does anyone else have amd64 that this works on.

All of my systems are 64-bit.  Can you be more specific about "doesn't work"?

John

---

### Post by anu815 on 2010-07-19
Please see this link, it did the trick for me: -

[http://theironlion.net/blog/2010/03/23/nexus-one-rhythmbox-one-ubuntu-one-music-store/](http://theironlion.net/blog/2010/03/23/nexus-one-rhythmbox-one-ubuntu-one-music-store/)

From the article: -

"just create a .is_audio_player file on the root of the SD card for the Nexus One and put the following contents into it:

audio_folders=Music/
folder_depth=2
output_formats=audio/mpeg,audio/mp3,application/ogg"

---

### Post by mikeashelby on 2010-07-21
Works for me too!

Weird thing to have to do... but if it works, it works, right?!

---

### Post by mr_step on 2010-07-23
wow....  i read that and thought there was no way it'd work...

but it did.  (I just created the file on the internal SD card, and the external one is also now mounting).

*update*  It also requires debugging mode to be turned on if you haven't done that also.

---

### Post by tijs14tijs on 2010-07-24
> **gator6666 said:**
> I have found solution for this problem :

#lsusb
Bus 001 Device 005: ID 04e8:681c Samsung Electronics Co., Ltd

Enable USB Debugging on your phone. 
Go to Menu -> Settings -> Applications -> Development and enable USB Debugging.
hope this works, i'm going to buy one in three days, looks like its a good phone... this and the fast battery low were the only problems i found :D

---

### Post by mr_step on 2010-07-27
OK guys.... /facepalm. 

The above approach works, or you can do it the correct way:

Go to "Settings" > "About phone" > "USB Settings" and select "Mass storage" instead of "Samsung Kies".  (Seriously, who stores such a major setting such as "USB Settings" in the "About phone" section?!?)

Problem solved, you don't need debugging turned on or the ".is_audio_player" text file.

However you may still want to have that file, since that's the file that tells Rythmbox where to copy music to for drag and drop music adding.

---

### Post by s_raghu20 on 2010-08-06
> **mr_step said:**
> 
The above approach works, or you can do it the correct way:

Go to "Settings" > "About phone" > "USB Settings" and select "Mass storage" instead of "Samsung Kies".  (Seriously, who stores such a major setting such as "USB Settings" in the "About phone" section?!?)

Problem solved, you don't need debugging turned on or the ".is_audio_player" text file.

However you may still want to have that file, since that's the file that tells Rythmbox where to copy music to for drag and drop music adding.

Thanks for the useful post. The Mass storage option  worked for me, but not the audio player. could something else be there ??

---

### Post by lordjubblydave on 2010-08-08
> **mr_step said:**
> OK guys.... /facepalm. 

The above approach works, or you can do it the correct way:

Go to "Settings" > "About phone" > "USB Settings" and select "Mass storage" instead of "Samsung Kies".  (Seriously, who stores such a major setting such as "USB Settings" in the "About phone" section?!?)

Problem solved, you don't need debugging turned on or the ".is_audio_player" text file.

However you may still want to have that file, since that's the file that tells Rythmbox where to copy music to for drag and drop music adding.

It does not work for me, it will not mount in 10.04

Banshee does not recognise it either

---

### Post by petergraham on 2010-08-12
on a totally seperate note .. has anyone found a program on ubuntu that will let me sync with my samsung galaxy s .. as in sync contacts and things?

---

### Post by rp88 on 2010-08-16
> **petergraham said:**
> on a totally seperate note .. has anyone found a program on ubuntu that will let me sync with my samsung galaxy s .. as in sync contacts and things?

For syncing contacts and calendar events I switched all my stuff over to gmail when i bought my captivate. Then i just set it all up in evolution. Look on google for "caldav evolution gmail" and it'll show you how to sync evolution calendar with your gmail account. This way your phone is synced with gmail, which is synced with evolution. Same goes for contacts...

So with evolution + google you get contacts, email, calendar all synced nicely into ubuntu and your phone.

---

### Post by elymolko on 2010-08-27
Hi all,

I have the same problem with my Samsung Galaxy S in Ubuntu 10.04. But, It works with this solution: 

*sudo modprobe -r ndiswrapper*

In this case, you unload mod and your Galaxy will be mounted in the Ubuntu desktop by usb.

It's worked for me in 10.04.;)

Bye.

elymolko.

---

### Post by Ozdemon on 2010-09-03
> **mr_step said:**
> OK 

The above approach works, or you can do it the correct way:

Go to "Settings" > "About phone" > "USB Settings" and select "Mass storage" instead of "Samsung Kies".  (Seriously, who stores such a major setting such as "USB Settings" in the "About phone" section?!?)


Thanks, the correct way was quick and effective although really non-intuitive.  Good work mr-step ):P

---

### Post by jsoto67 on 2010-10-20
I just bought a Samsung Vibrant Galaxy S from tmobile. When first got it, I plugged it in via USB in order to tether it for internet access and it worked fine. The next day I tried it and nothing happened. Since I had just got it and had messed around with it a bit to get to know it I thought that maybe I had changed some settings so I did a factory reset, still no avail. Ubuntu network manager does not detect it. I even upgraded to ubuntu 10.10, still no connection. Right now I'm connected using easytether, but like I said, when I had just bought it worked right out of the box. Any body have any ideas? I hate having to connect through easytether. My previous phone was a samsung sgh-t339 and it connects without a problem.

thanx

---

### Post by inunu on 2010-10-22
My device is not listed under lsusb any ideas.. :(

---

### Post by Bjorg on 2011-01-23
My Samsung Galaxy S uses Froyo or Android 2.2

To access it from Ubuntu as an external memory device (to load pm3 or videos ...) go to (mine is in Spanish, in English the name of the options should be similar) Settings> Wireless Connections > USB Settings > and select Mass Storage (or better, select "ask when connected" so it will let you choose if you want to access the phone for managing files, multimedia files, or Kies). 

I still haven't been able to find where to put the mp3s in the phone

Hope it helps.

Beware of one thing. When finishing, in Ubuntu you will want to unmount the phone, but will unmount the cards inside the phone, the internal (the one which comes with the phone) and the external (the one wchich is removable, the minisd). I haven't been able to mount them again from the phone, I had to switch it off and on for that. 

Solved: Use in Ubuntu only the "Eject" option, this is fine, I have to do it twice, I guess because I also have an extra sd card. Do not use the "remove safely" (this one has the effect commented above and you will have to reboot the phone, I am afraid)


For some reason I am not able to use the extra sd card (external_sd) and get the music player to find the files. I can only put song files inside DCIM/Music if i want the music player to recognize them.

---

### Post by roby78 on 2011-02-19
So, I see that you ultimately want to manage your music on Galaxy S via an Ubyuntu machine. There is no Kies equivalent for linux (although I don't understand why the guys at Samsung are so lazy) but...

for those that want to connect their Galaxy S phone to an Ubuntu machine (any ubuntu release) there is a workaround. It is a simple app that is called "Kies air" and that works over wi-fi (home or office). You can download it from Samsung Apps on your phone and it will offer you the possibility to connect to Galaxy S via the browser window... you simply type in the browser the IP that this app gives you and you have the possibility to manage contacts, photo, music messages, video, etc.

Hope this helps...

---

### Post by Varun Vyas on 2011-02-27
Hi All,

After buying Samsung Wave II found that if I want to download new apps , either I have to download it via mobile itself or via pc.

When Tried to installed Kies, via wine it totally blew off.

Is there any way I could download samsung apps on my ubuntu ?

---

### Post by yaelg on 2011-03-31
Thank you !!! I've been struggling with this problem for quite some time. Yours was the most accurate answer!!! thank you!!!

IT WORKSSSSS!!!


> **jgorkos said:**
> I struggled with this too.  There is one step left on the phone after you plug it in that you need to take.

Here's how I got it to work, using Lucid Lynx Kubuntu.  Surely a Gnome desktop will be similar.

1)  On the phone, go to Settings->Applications->USB Settings and select the "Mass Storage" Options.
2)  Go back to Settings->Applications->Development and select "Stay Awake"

3) Plug in your USB cable to the phone and computer.
The phone will say "USB Connected in the status bar at the top, and a USB symbol will appear.
4) Drag down the notification bar from the top and hit the "USB Connected:  Select to copy files to/from your computer"
5)  You get a new window with "USB Connected:  You have connected your phone to your Computer via USB.  Select "Mount" if you want to copy files between your computer and your phone's SD card."   Select MOUNT.

6) Your notification applet on your computer will squawk about TWO new drives being attached.  There will be a little one, and a big one.  Mount the bigger of the two.

There will be a selection of existing directories/folders (if you think folders, stay off my lawn):
Android
Bluetooth
DCIM
kindle
mobi_drm
sd
slacker
twc-cache

If you want to add music, create a new directory (folder, youngster) called "Music" and copy your music into it.
Don't forget to use the device notification applet/command line/etc to unmount the drive when you're done copying.
7) Finally, drag down the notification bar on the phone again and hit "Turn off USB Storage" to tell the phone to stop making the SD card available to the host PC.  After you confirm that, your card will be scanned for new media, and it will be available for your consumption via the Music Player.

Enjoy your new Galaxy S/Vibrant/Whatever your carrier calls it.  I know I am.

John Gorkos

---

### Post by kaizen666 on 2011-04-29
Thanks, it worked.

Saved me as I have just reformatted my samsung netbook to unbuntu also.

Just to add though for my model of the phone (Samsung galaxy - gt-i9000) the USB settings was not under the Applications folder, It was in the 'About phone' a few options down.

The 'mass storage' options kinda makes sense as the previous one for me was set to kies, which still doesn't work on unbuntu...but then who cares I only really need it for upgrading the phone and from what I hear the upgrade on this model phone is still swarming with bugs.

It was really easy, I played with the phones folders and could even listen to the tracks without having to load them individually onto a player, so I also cleaned the library up as well.

Every day I love Ubuntu a little bit more...

---

### Post by nyteryder79 on 2011-12-16
> **gidovans said:**
> Hello,

Just got my new Samsung Galaxy i9000 phone. When connecting to my laptop with an USB cable, the phone says "USB Connected", but Ubuntu does not see my phone.

I am using Ubuntu not yet for a long time, so I need some help here.

My laptop runs 10.04

Thanks already,
Gido

Try [THIS]("http://www.reddit.com/r/Android/comments/ne6ud/mount_your_new_galaxy_nexus_from_the_unity/") if you have a Galaxy Nexus.

I wrote this a couple of days ago and it's working great for me and some other's who have tried it.

---

