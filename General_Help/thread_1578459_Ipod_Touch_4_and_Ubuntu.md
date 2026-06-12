---
title: "Ipod Touch 4 and Ubuntu"
date: 2010-09-20
forum: General Help
---

### Post by raafaell on 2010-09-20
Hi, I just got the new Ipod Touch 4, and I have somehow connect it to the Itunes for the first time, and I'm trying to do it under Ubuntu...

Does anyone know a way to do it? 
I tried installing Itunes 7.6 and it worked fine with Crossover Linux, but I guess it won't recognize as it's a old version of Itunes.

Any other App that I can use? Thanks

[IMG]http://farm3.static.flickr.com/2656/4096916895_8e338c4eee_o.jpg[/IMG]

---

### Post by raafaell on 2010-09-20
bump

---

### Post by scouser73 on 2010-09-20
You need to initialise the iPod on a Windows machine through iTunes, then it will be recognised by Ubuntu the next time that you plug it in.

---

### Post by Dustin2128 on 2010-09-20
I also heard that banshee has good support for the ipod, once you get the OS downloaded
//side-rant
why should you have to download the OS with that company's software to be able to use your portable media player?

---

### Post by raafaell on 2010-09-21
> **scouser73 said:**
> You need to initialise the iPod on a Windows machine through iTunes, then it will be recognised by Ubuntu the next time that you plug it in.

Yes, I had to do that

thanks

---

### Post by pbhill on 2010-09-21
> **Dustin2128 said:**
> I also heard that banshee has good support for the ipod, once you get the OS downloaded
//side-rant
why should you have to download the OS with that company's software to be able to use your portable media player?

I just tried my new iPod Touch v4 with Banshee. Doesn't recognize it. I have version 1.6.1 installed. I tried the latest version, 1.7.6  which does recognize v4, but it would crash after several seconds. I reverted to 1.6.1.
I hate to go back to iTunes, but need some music on this thing! Any ideas?

---

### Post by raafaell on 2010-09-21
> **pbhill said:**
> I just tried my new iPod Touch v4 with Banshee. Doesn't recognize it. I have version 1.6.1 installed. I tried the latest version, 1.7.6  which does recognize v4, but it would crash after several seconds. I reverted to 1.6.1.
I hate to go back to iTunes, but need some music on this thing! Any ideas?

Yeah I guess you will have to do it on Windows, I searched the web for a long time, and couldn't find nothing specific, Installed Itunes 7.1 on CrossOver Linux... that didn't help either, so I guess you WILL need the Itunes 10 to do it.

---

### Post by pbhill on 2010-09-22
I tried installing iTunes 10 with Wine after reading about how to do it... Don't bother... it crashed my computer!
Are there any other apps can I use (in Ubuntu) to synch the new iPod Touch?

---

### Post by scouser73 on 2010-09-22
I take it that your iPod Touch is 4th gen?, if so you need to check out this - [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

The guys at libimobiledevice are trying to enable sync for the latest iPods/iPads/iPhones.

---

### Post by pbhill on 2010-09-22
Thanks! Looks interesting!

---

### Post by raafaell on 2010-10-02
bump

---

### Post by pbhill on 2010-10-02
> **raafaell said:**
> bump

What is "bump"?

---

### Post by nlsthzn on 2010-10-02
> **pbhill said:**
> What is "bump"?

By posting in a thread it gets promoted up in the list of threads in a current topic... It gets "bumped" to the top... So there is more chance of it being spotted and replied to... 

Basically seen as "bad manners" if done to frequently... Good rule of thumb is one bump every 24 hours if no replies have been received...

---

### Post by seadao on 2010-10-06
i had the same problem, you need to download the closed source version of virtual box with usb support, install winXP into it(i recommend winXP LITE) google it.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

then you need to install the guest addons(look in the menu) then setup a shared folder new folder or just use "public" folder

download latest i tunes from apple, copy it to your shaded folder

set the network adepter inside vbox to NAT

install itunes in vbox,

connect your ipod to the computer, go into the "Devices"> "USB devices"

apple ipod should showup there, click on it

start itunes, it should recognize the ipod and activate it

Hope this helps, i really paniced, i had no idea apple sold bricked products

---

### Post by clipt on 2010-10-06
wouldnt songbird work? my friend uses it all the damn time and he loves it.

---

### Post by sendblink23 on 2010-10-06
> **clipt said:**
> wouldnt songbird work? my friend uses it all the damn time and he loves it.

Question.. is it the latest 4th gen ipod touch?

---

### Post by pbhill on 2010-10-07
Thanks for the reply seadao. I had previously done just as you describe, and it all works fairly well. I was hoping for a non-microsoft solution. Banshee works as a rule, and will recognize the new 4th Gen iTouch, but it doesn't allow transfers of music/video.
I'll give Songbird a try.

---

### Post by pbhill on 2010-10-07
On a slightly different note, we also use a Creative Zen mp3 player that has always worked perfectly in Banshee. Now the new version of Banshee [1.8] won't even recognize it. Can anyone tell me how to force Banshee to mount the Zen player?

---

### Post by pbhill on 2010-10-07
> **clipt said:**
> wouldnt songbird work? my friend uses it all the damn time and he loves it.

Ask your friend what OS he has. Songbird appears to be Windows only. I tried it with WINE but it wasn't a good experience.

---

### Post by seadao on 2010-10-07
about banshee and zen, try to go into options and turn on mtp device plugin,
my zen has always worked in rhythmbox with mtp plugin turned on

---

### Post by Sabonmu on 2010-10-09
I use Ubuntu 10.4 and just treated myself to a 4th gen iPod Touch. Great product, but what a bad move? I got it duty free at Heathrow, to play with on the flight over to Nepal. 
Couldn't do a thing with it as it was 'locked' and needed iTunes and a net connection to unlock. 
I've tried Banshee, Hippo, Gtkpod, Songbird, Rythymbox and every trick suggested and all it will do is read photos. I can't synchronise or copy anything over. If I lived in the UK I would return this to Dixons as they didn't advertise that you needed to purchase other software to use this product (Windows).
I've since 'borrowed' time on a windows xp machine and unlocked and synced some music over to it. Truly the iPod is marvellous, but why are Apply doing this?

---

### Post by clipt on 2010-10-09
ok i will ask him

---

### Post by pbhill on 2010-10-10
> **seadao said:**
> about banshee and zen, try to go into options and turn on mtp device plugin,
my zen has always worked in rhythmbox with mtp plugin turned on

I do have it turned on. It always worked until the last Banshee upgrade.

---

