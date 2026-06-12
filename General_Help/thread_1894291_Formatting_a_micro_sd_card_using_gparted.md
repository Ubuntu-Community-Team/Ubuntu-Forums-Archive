---
title: "Formatting a micro sd card using gparted"
date: 2011-12-12
forum: General Help
---

### Post by rapattack1 on 2011-12-12
Hi i have been having trouble with a micro sd card(i put it in an adapter to make it an ordinary sd card). Not sure how to format it. I am not very good with gparted. I have used this in a blackberry and had so many problems then i tried to use it in a camera. More porblems. Some pictures or videos are viewable and some are not. Never seems to be anything that makes sense and sometimes i think i bought a dud card :0( Anyway don't ask for more information because it can be just classified as unstable. I know blackberry phones have all that encryption bullcrap and that is super complicated and i tried to solve this on two bb forums with no success. I thought i would format this using linux and then use it in my camera and forget about using it on my blackberry.

---

### Post by zero2xiii on 2011-12-12
Hay,

I will try to outline the process:

*Insert your SD card,

*Run "lsusb" to see if its picked up (if it does not auto mount and open a window showing the files) <in a terminal: Applications > Accesories > terminal on a <= 10.10 system>

*Run "gksudo gparted" (mine doesn't start without gksudo rights)

*In top right hand conner click the drop down list and select the SD card (should be the botom most one on the list since its detected last) - In my system with two Harddrives it will be showing as /dev/sdc

*Rightclick on the partition and unmount if it is mounted (shown by a key)

*Right click again and select delete partition

*Righclick again and select new

*On the right select create as "Primary partition"

*Filesystem "fat32"

*Type a lable if you wish

*Hit add

*The window should now be closed, hit the green mark at the top to apply all the pending operations, now just wait for the process to complete,.

That should be it. Your card should now be formated and ready for testing. If any of the above steps fail, we need to get more information for trying to solve the issue. Bad sectors cannot be repaired on solid state memory. But let us hope this is not the case.

Goodluck
Cherz

---

### Post by rapattack1 on 2011-12-13
Ah i suspect it is a bad sectors issue. Didnt know that happens on these little things. Gee i should have done this ages ago to determine if it was working or not so i could get a refund from the ebay seller. Anyway got almost to the end but then the attached image will show what happened on the very last point where i hit the green arrow:

---

### Post by zero2xiii on 2011-12-13
Hay,

Oka so I can see an error has ocoured, please move the pop up dialouge out of the way and then on the inscription in the log view, hit the left side arrows until all the details are displayed and recap a screen shot please. Might be something fixable, IF it is not bad sectors causing the problem.

CHerz

---

### Post by rapattack1 on 2011-12-13
Sorry i didn't quite understand what you meant. Is this right?

---

### Post by zero2xiii on 2011-12-13
Hay,

Not quite,
I will do the process on a 4gb thumb drive I have and upload a shot numbered with the information I require.

The descriptions is as follow:
1.jpg - Start screen
2.png - The new partition creation screen
3.png - After add has been clicked before the green check mark
4.png - The screen after a sucessful format where you get the error, this is showing the details,

Click on the "Save details" button and upload that information in the file (it should save as a htm/html file)

Cherz

---

### Post by rapattack1 on 2011-12-13
Hi i tried to upload the htm file but i think because it is from the root it won't upload. The upload applet said that it couldn't :0(

---

### Post by zero2xiii on 2011-12-14
Hay,

Just open the file in a web browser and copy-paste the content, that will be sufficient

Cherz

---

### Post by rapattack1 on 2011-12-14
GParted 0.5.1

Libparted 2.2
Delete /dev/sdc1 (fat32, 31.04 GiB) from /dev/sdc  00:00:00    ( ERROR )
     	
calibrate /dev/sdc1  00:00:00    ( SUCCESS )
     	
path: /dev/sdc1
start: 8192
end: 65095679
size: 65087488 (31.04 GiB)
delete partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Can't write to /dev/sdc, because it is opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.

========================================
Create Primary Partition #1 (fat32, 31.04 GiB) on /dev/sdc

========================================

---

### Post by ratcheer on 2011-12-14
I don't have a micro SD card handy to look at, but regular SD cards have a little slider switch on one side to make them read-only. If your card has such a switch, make sure it is not set to the read-only position.

Tim

---

### Post by rapattack1 on 2011-12-14
I think it is in the unlocked position. There is an arrow pointing down and i interpret that as if you push the slider down then it is locked. It is up so i think it is unlocked

---

### Post by zero2xiii on 2011-12-16
Hay,

SOrry I come back only now. Was not close to the computer yesterday.

Try the switch in the other position aswell, might be that. How ever I have had similar errors when the drive is always mounted read only. I have not been able to find a way to fix this, so if the error keeps occuring even after changing the position of the switch, I can not help you, then it might be damage or corrupt. But there might be a way around that "read only" situation.

Good luck

---

### Post by rapattack1 on 2011-12-16
Hi thats ok i am so busy i rarely log in myself :0)
I tried a different adapter today for the micro sd card as i tried to slide the slider and it broke off. I thought i would also try another micro card in the newer reader first and the gparted stuff worked. So it did also with the micro card that has had the error. So will go out and take some videos/photos to see if the whole thing has worked or not then report back. Another thing before i did the above it that i was able to copy paste files from the card to my hard drive so i don't think it was read only...am i right? I was able to do that today and the other times. Or does read only mean something else?

---

### Post by zero2xiii on 2011-12-17
Hay,

Read-only does exactly as the name implies, if a drive is read only the following is true:

Card > Other drive - Works
Other drive > Card - ERROR; read-only device or drive.

You can access the files and folders on a read only device, but cannot alter the data ON the read only device, so you can not add or delete or edit data or files stored on it.

Hope that clears things up,
Cherz

---

### Post by satanselbow on 2011-12-17
I must have missed this thread before.

I have been in the situation where the SD adapter causes read errors when there is in fact nothing wrong with the miniSD inserted.

I have seen this with 2 separate Sandisk adapters - a similar Kingston adapter has no such problems. A physical inspection of the adapter shows that the "Lock" (Read Only) switch is of weak construction and may flicker between the 2  states thus causing the errors.

If you can directly insert the miniSD in another device - such as a phone - are the same errors experienced?

---

### Post by rapattack1 on 2011-12-17
zero2xiii-OK i am a bit confused ...do we know that the card was read only? Sorry didn't read that anywhere. Maybe i wasn't paying attention. I was able to copy the files and edit what was readable. What was not readable i was not able to do anything with. Anotherwords some files were playable/viewable(depending on wether they were jpgs or avi's) but others were not. Same session and same transfer of files.

Anyway things might be working now. I say might because i have seen the card works for a bit then play up....can't explain this as it has been a hugely long wrong of inconsistencies. Today i can view all the files and transfer them onto the hard drive.

satanselbow- no whats happening is that the sd card was in a blackberry first off and i had huge problems for a very long time. I don't know if it was my lack of experience with the bb or the card. I will never really know! Gave up on that and now i have put the card(with adapter) in my good hd camera. The original adapters switch was stuck. I tried to move it but it broke off so using a different adapter now.

---

### Post by ratcheer on 2011-12-17
Those cards are very cheap these days. Why don't you just try a new one? That one seems to have a long history of flakiness.

Tim

---

### Post by zero2xiii on 2011-12-18
> **rapattack1 said:**
> zero2xiii-OK i am a bit confused ...do we know that the card was read only? Sorry didn't read that anywhere. Maybe i wasn't paying attention. I was able to copy the files and edit what was readable. What was not readable i was not able to do anything with. Anotherwords some files were playable/viewable(depending on wether they were jpgs or avi's) but others were not. Same session and same transfer of files.


Yes we do:

> GParted 0.5.1

 Libparted 2.2
 Delete /dev/sdc1 (fat32, 31.04 GiB) from /dev/sdc 00:00:00 ( ERROR )

 calibrate /dev/sdc1 00:00:00 ( SUCCESS )

 path: /dev/sdc1
 start: 8192
 end: 65095679
 size: 65087488 (31.04 GiB)
 delete partition 00:00:00 ( ERROR )
 libparted messages ( INFO )

 Unable to open /dev/sdc read-write **(Read-only file system)**. /dev/**sdc has been opened read-only**.
 Unable to open /dev/sdc read-write **(Read-only file system)**. /dev/**sdc has been opened read-only**.
 Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
 Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
 Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
 **Can't write to /dev/sdc, because it is opened read-only.**
 Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.

 ========================================
 Create Primary Partition #1 (fat32, 31.04 GiB) on /dev/sdc

 ========================================

But some devices (esp usb memsticks) I have had similar issues with because it was faulty and could not be opened. SO it is NOT to say that the "switch" is causing the problems, although it might. But since the SD card itself gave issues in numerous situations, I think it IS safe to say that there is problems with the card itself. (think those cards you could buy that said 32 or 64gig but when you actualy test them where only 2 or 4 gig... It gave the exact same type of problems, only some files are readable and transferable)

Cherz

---

### Post by rapattack1 on 2011-12-20
Hi well good news is the card seems to be working well. It is a 32g card so not cheap at all :0) Thanks for the help. This has been bugging me for many months!!!!

Thanks for the explanation as i didn't look at that file/text i sent you :0)
What did you mean about the size of the card? Is mine a 32g?

---

### Post by zero2xiii on 2011-12-20
Hay,

No worries, please marked the thread as solved.

What I meant about the size is: A while ago you could buy insanely large storage drives (64gig up to 2TB) flash drives, but when u got them the files started to corupt when u exceeded eg 2gig, what the ppl did was to change the "header" of the drive, telling the OS that its a 128gig drive (example) when in reality the hardware was only capable of 2gig storage. This was common for Chinese media players.

But glad it's sorted out now.
Cherz

---

### Post by rapattack1 on 2011-12-21
OK will do.
So how do i tell that this card is 32g?

---

### Post by zero2xiii on 2011-12-21
> **rapattack1 said:**
> GParted 0.5.1

Libparted 2.2
Delete /dev/sdc1 (fat32, 31.04 GiB) from /dev/sdc  00:00:00    ( ERROR )
     	
calibrate /dev/sdc1  00:00:00    ( SUCCESS )
     	
path: /dev/sdc1
[B]start: 8192
end: 65095679
size: 65087488 (31.04 GiB)[/B]
delete partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Can't write to /dev/sdc, because it is opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.

========================================
**Create Primary Partition #1 (fat32, 31.04 GiB) on /dev/sdc**

========================================

Haha again with the information you posted. Read the stuff you post aswell, that will help you learn and understand so next time you can try on your own ;)

Cherz

---

### Post by rapattack1 on 2011-12-21
No what i meant was i don't know what a header is therefore i don't know what information is correct. :)

---

### Post by zero2xiii on 2011-12-22
Hay,

Haha no problem :). Just pointing out the information in the post you need to pay attention to, if that was different from the claimed specs, you should have worried, but it is pretty close to the claimed 32gig..

Headers and firmware details and stuff is tricky to research, but google stays one's friend :). If you are curious and want to learn, start with files and file headers:
In broad:
[http://en.wikipedia.org/wiki/Header_(computing](http://en.wikipedia.org/wiki/Header_(computing))
More file specific:
[http://en.wikipedia.org/wiki/Header_file](http://en.wikipedia.org/wiki/Header_file)
[http://en.wikipedia.org/wiki/List_of_file_formats](http://en.wikipedia.org/wiki/List_of_file_formats)

From there when u click on a file format and such, more in depth explanation is given, including the header information and structure on most of them.

Cherz :popcorn:

---

### Post by rapattack1 on 2011-12-22
Ah cool so linux reports what the size is ....cool. Yeah i google stacks but when i don't know what to search for then i can't :0) Thats the time to get on the forums he he. I get real nerds to help out this amateur nerd lol. We have had a lot of heavy rain here so no chance to test the card in my camera further. Ah well will have to take it with me to shoot xmas;)
Thanks for the links. Will find time in the new year to do some reading :0) Have a great Xmas and thanks so much!!!!:popcorn:(vegan popcorn ofcourse lol)

---

