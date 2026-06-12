---
title: "SDHC data recovery"
date: 2010-05-30
forum: General Help
---

### Post by macoklein on 2010-05-30
Hi everyone, 
Yesterday, my Windows 7 machine managed to somehow destroy a SD card with some pictures on it. Now, every time the card is inserted into a computer running windows, or the camera it came from, it asks to be reformatted. Obviously I would like to recover the pictures from the card. 

I tried a scanning the card with a windows program "[card recovery]("http://www.cardrecovery.com/")" and the program was able to scan the card and find the images on it. But I have to pay $40 to actually copy them from the card to the computer. 

So I did some digging and tried to find a way to recover the data for free using my Ubuntu machine. Some details about my hardware:
Running Ubuntu 9.04
SD card: 8Gb SDHC from PNY Optima
The camera was a Nikon D5000

What I have done so far:
I used ddrescue to create an image of the card. However, at this point, most of the instructions I found only have you try and mount the image. Then I used the testdisk utility and the mmls utility from the SluethKit to try and find a partition on the SD card image that I could mount. Both of these programs failed to identify a partition on the card. 

At this point I am stuck, and I would prefer not to have to pay to get the images off. Does anyone have any more suggestions?

Thanks!
-Viliam

---

### Post by _Mark_ on 2010-05-30
Try this [http://www.lc-tech.com/rescuepro/](http://www.lc-tech.com/rescuepro/) have never used it myself but know several people who have successfully recovered pictures from a card

Good Luck

Ah I just realised it needs activating with a code from a Sandisk card, do you have any Sandisk cards with this code? If not I may have one kicking around you can have

Let me know

---

### Post by prshah on 2010-05-30
> **macoklein said:**
>  and I would prefer not to have to pay to get the images off. Does anyone have any more suggestions?

Along with testdisk, there is a program called photorec; it is part of the testdisk suite, so if you have TD installed, photorec is also installed.

It is designed for such situations; it will scan your "damaged" SD card and recover any recognizable filetypes, such as JPG, DOC, etc etc.

It really easy and simple to use; give it a try. The only downside is that file NAMES will be lost; the names will be replaced with generic ones eg file000.jpg, file0001.jpg, etc.

Post back if you need more details.

---

### Post by frostschutz on 2010-05-30
Actually the loss of file name is not an issue with digital camera pictures ;

provided that your camera had its internal clock set correctly you can get the date and time the photo was shot from the JPEG EXIF data, producing useful file names.

It won't be sorted into folders anymore but as long as you still remember when you were where the pictures can be easily resorted into a proper file / folder structure.

So the situation is a lot less worse than with other file types.

Problems start if you had your camera set to RAW data...

---

### Post by macoklein on 2010-05-30
Solved!
I was under the impression that photorec required a valid partition to be loaded before it would recover the photos. However a simple search of the card image recovered all of the photos and more. 
Turns out when the camera reformats the card it only wipes the FAT table. Almost every picture that had ever been put on the card was recoverd!

---

### Post by prshah on 2010-05-31
> **macoklein said:**
> Almost every picture that had ever been put on the card was recoverd!

Just an alert; not all the files will be readable; so please check each file before you delete it thinking it is a duplicate. You should have lots of duplicate copies.

---

### Post by xmaneasy on 2012-04-25
If you want to find a cost-effective pictures recovery software, you can try this one "Yesterdata [Pictures recovery]("http://www.recovery-photo.com") ". The free photo recovery software may result in so many terrible problems. Because they are free. No Guarantee !

---

