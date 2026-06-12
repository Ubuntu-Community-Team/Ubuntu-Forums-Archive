---
title: "Corrupts images, lost all my summer holiday pictures..."
date: 2011-08-10
forum: General Help
---

### Post by TutenStain on 2011-08-10
This just stinks...

Plugged in my camera, copied (note: not moved) the photos to my HDD, disconnected the camera. Then I wanted to watch the pictures and saw that 95% were corrupt, they were just 0byte files. 

Well I thought no problem, I copy them over again...But Ubuntu corrupted the original pictures on my camera too! 

This have happened 2 times now. So I have lost all my summer pictures that were taken with either my DSRL or my compact camera. Great!! Freaking amazing! 

What to do? When will this "bugg" be fixed? What caused this? Im quite mad right now.

---

### Post by MG&amp;TL on 2011-08-10
What file format are you shooting? JPEG, I guess? JPEGs should be no problem, RAW or TIFF you might have more problems with but should still copy OK.

Report it on launchpad to get it fixed.

[https://launchpad.net/](https://launchpad.net/)

You need to make an account and be prepared to answer any questions the mods and/or developers may wish to ask.

Sorry about your photos. You could try a document recovery program on your card? Just a quick check-what file extension does the computer show the images as being?

---

### Post by haqking on 2011-08-10
> **TutenStain said:**
> This just stinks...

Plugged in my camera, copied (note: not moved) the photos to my HDD, disconnected the camera. Then I wanted to watch the pictures and saw that 95% were corrupt, they were just 0byte files. 

Well I thought no problem, I copy them over again...But Ubuntu corrupted the original pictures on my camera too! 

This have happened 2 times now. So I have lost all my summer pictures that were taken with either my DSRL or my compact camera. Great!! Freaking amazing! 

What to do? When will this "bugg" be fixed? What caused this? Im quite mad right now.


Did you safely remove your camera with the right click and safely remove or just unplug it ?

Quite common after copy and paste actions is that people disconnect the device by unplugging then corrupt the data or lose it altogether.

That is why the safely remove actions exists to perform a safe unmount.

---

### Post by ofnuts on 2011-08-10
> **TutenStain said:**
> This just stinks...

Plugged in my camera, copied (note: not moved) the photos to my HDD, disconnected the camera. Then I wanted to watch the pictures and saw that 95% were corrupt, they were just 0byte files. 

Well I thought no problem, I copy them over again...But Ubuntu corrupted the original pictures on my camera too! 

This have happened 2 times now. So I have lost all my summer pictures that were taken with either my DSRL or my compact camera. Great!! Freaking amazing! 

What to do? When will this "bugg" be fixed? What caused this? Im quite mad right now.
It could also be a defective memory card in the camera. Did you try to check the card by putting it in a card reader?

---

### Post by TutenStain on 2011-08-10
> **MG&TL said:**
> What file format are you shooting? JPEG, I guess? JPEGs should be no problem, RAW or TIFF you might have more problems with but should still copy OK.

Report it on launchpad to get it fixed.

[https://launchpad.net/](https://launchpad.net/)

You need to make an account and be prepared to answer any questions the mods and/or developers may wish to ask.

Sorry about your photos. You could try a document recovery program on your card? Just a quick check-what file extension does the computer show the images as being?


Tried recovery program but it did not work. The computer shows them as jpg. When i try to open them (0byte files...) i get "Error interpreting JPEG image file (Improper call to JPEG library in state 200)"

Here is an example of half corrupted file: [IMG]http://img153.imageshack.us/img153/8721/dsc0410vk.jpg[/IMG]

---

### Post by papibe on 2011-08-10
Sorry to hear that. Once happened to me in Windows. I stopped connected cameras using their provided USB cables long time ago. Now I remove the memory card and plug it to a card reader (included in most laptops, and very inexpensive for desktops).

To copy a couple of pictures the direct connection may work, but in order to copy a significant amount, I would recommend using the memory card.

Again, it really sticks.

---

### Post by MG&amp;TL on 2011-08-10
Whoah-that's umm...mucked-up? :shock:

Sorry, but I think the most likely thing is a bad mount/unmount.

---

### Post by TutenStain on 2011-08-10
> **haqking said:**
> Did you safely remove your camera with the right click and safely remove or just unplug it ?

Quite common after copy and paste actions is that people disconnect the device by unplugging then corrupt the data or lose it altogether.

That is why the safely remove actions exists to perform a safe unmount.

Thats true. But to my defense: I have never safely removed anything in my life. I always make sure that the copying is finished and check the activity light on my reader. Never had any problem until i switched to Ubuntu.

> **ofnuts said:**
> It could also be a defective memory card in the camera. Did you try to check the card by putting it in a card reader?

The card is fine and its working (no errors).

---

### Post by mike555 on 2011-08-10
So you plugged in your camera and viewed your pictures ? in what viewer ?  then how did you copy them? did you use a program or just picked the ones you wanted to copy and clicked copy , then opened your pictures folder and pasted them, did you see them after pasting ? 
   if we are going to help you we need as much info as possible.

---

### Post by TutenStain on 2011-08-10
> **mike555 said:**
> So you plugged in your camera and viewed your pictures ? in what viewer ?  then how did you copy them? did you use a program or just picked the ones you wanted to copy and clicked copy , then opened your pictures folder and pasted them, did you see them after pasting ? 
   if we are going to help you we need as much info as possible.

Basically. I plugged it in. Opened the folder on the memmorycard (Camera). Selected all photos and copied the over to my internal HDD (ctrl + c/v). It finished copying, I waited a few sec, watched the activity led, when it stopped flashing I just unplugged it.

Then I wanted too see my photos in Eye of GNOME 2.32.1...

EDIT: I did not view the pictures while they were on my camera, I wanted to view them after they have been copied over to my HDD and I disconnected my camera.

---

### Post by niko123456 on 2011-08-10
very odd. you didn't buy a cheap sd card off ebay did you? 

try taking a few pictures and see if they display ok on your camera.

(i'm not saying this isn't an ubuntu fault like you suggest, but worth making sure where the error is).

---

### Post by TutenStain on 2011-08-11
> **niko123456 said:**
> very odd. you didn't buy a cheap sd card off ebay did you? 

try taking a few pictures and see if they display ok on your camera.

(i'm not saying this isn't an ubuntu fault like you suggest, but worth making sure where the error is).

No its not a "cheap" SD card. Bought in a retail store. All new photos I take can be watched on my camera. As I told, this is the second time happening. First it was on my compact, now on my DSRL.

---

### Post by haqking on 2011-08-11
> **TutenStain said:**
> Basically. I plugged it in. Opened the folder on the memmorycard (Camera). Selected all photos and copied the over to my internal HDD (ctrl + c/v). It finished copying, I waited a few sec, watched the activity led, when it stopped flashing I just unplugged it.

Then I wanted too see my photos in Eye of GNOME 2.32.1...

EDIT: I did not view the pictures while they were on my camera, I wanted to view them after they have been copied over to my HDD and I disconnected my camera.


I would bet it is to do with the just unplugged it thing.

I mean i know youve done it before as have i in boith windows and linux, and for the most part it works fine.  It is one of those things, just when you need it to work OK it doesnt, the safely remove exists for exaclty this type of issue.

I would put it down to a lesson learned and see if you can pop you memory card into a reader and try recover the data.

---

### Post by TutenStain on 2011-08-11
> **haqking said:**
> I would bet it is to do with the just unplugged it thing.

I mean i know youve done it before as have i in boith windows and linux, and for the most part it works fine.  It is one of those things, just when you need it to work OK it doesnt, the safely remove exists for exaclty this type of issue.

I would put it down to a lesson learned and see if you can pop you memory card into a reader and try recover the data.

Lets say the problem was that I did not safely remove. Anyone have any technical explanations why this happened? I'm quite interested in it myself.

---

### Post by niko123456 on 2011-08-11
yeh but I don't get why the files you copied over (that now reside on your computer) are corrupted? the ones on the SD card I can understand if you believe that thing about unsafely removing media (which I don't).

---

### Post by JKyleOKC on 2011-08-11
> **TutenStain said:**
> Lets say the problem was that I did not safely remove. Anyone have any technical explanations why this happened? I'm quite interested in it myself.In the interests of getting speedier results, almost all systems (Windows, Mac, Ubuntu, all of them) don't try to write data directly to a drive (or to a USB device such as a camera that masquerades as a drive). This is because data transfer to a drive is much much slower than that same transfer to a memory buffer.

Once it's in the buffer, the original program thinks the write is complete. Later, usually over the next several seconds (but I sometimes see it taking more than a minute) the data actually gets written to the drive.

The purpose of the "safely remove" operation is to make sure that all of the data has been written to the drive, not just to the buffers. Waiting for the drive light to stop flickering isn't always a guarantee of completion, either, because the system has to update directory information in addition to writing the actual data, and that may be done in memory that waits quite a while to write to disk, rather than flushing it out immediately. That last part is why cutting power rather than doing a proper shutdown can actually make a disk unreadable.

This could easily explain why the original copy from camera to computer wound up being incomplete. However it would not explain why the files on the camera itself were corrupted also. That's the really mystifying part, from a geek point of view!

I'm not familiar with the Canon software; my cameras are Olympus and Casio, and I also transfer lots of Nikon images. It's possible that the software in the camera itself attempts to update information on the memory card, and pulling the plug too soon could cause the problem there -- but I doubt that the compact camera has the same software as the Canon, so it's still a mystery...

---

### Post by Black No. 1 on 2011-09-25
This is a bug with Nautilus.  Your SD card is not corrupt.  Try your card with a different linux distro or (dare I say) windows.  I am looking for a solution right now.  Will post results soon.

---

