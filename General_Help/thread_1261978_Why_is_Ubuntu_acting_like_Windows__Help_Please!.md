---
title: "Why is Ubuntu acting like Windows ? Help Please!"
date: 2009-09-09
forum: General Help
---

### Post by M!SF!TS on 2009-09-09
Hello Fellow Ubuntuer's

    I have ran in to a BIG issue here. I have a 250GB External HDD, a 350GB External HDD, and a 1TB External HDD. and when ever i tried to do a Backup in Windows to them (im talking entire disk Backup not my weekly, 'Touchup') they would always stop responding like half way threw or so, and then i would have to risk unpluging them, and move the remaining files, i.e. threw hard intensive manual computer labor! 

(i.e. point...click...point...click...point...click...point...click... you get my drift...)

    Well i am now, using ubuntu. i have been using ubuntu since 8.04 was released, and have been enjoying learning it and using it, a few hiccups with compatibility along the way, but i figure thats the nature of open source i.e. linux... i noticed from day one using linux that my download speeds, and file transfer speeds are 50% to 75% faster on linux then windows, and have been happy until now.

    Linux is acting like my windows box when i transfer a large ammount of data, i have not moved a massive amount of data like this yet on linux, but now i wish i have done so earlier... i gets not even half ways, and nautilus will freeze, i gave it the benifit of the doubt, that made the front end GUI froze but the background was still working... 2, 3, 5 HOURS LATER, nothing.

i was like okay, i can fix this... simple ! i activated my superpowers and summoned the Command Line.

@linux-box:/media/disk$ mv Files /media/1TB\ Storage/

i was like problem solved... nope.

it is a large amount of data here (i now realize i should have used the cp command and not the mv command. because if someone cannot help i maybe loosing alot of data)

well i was watching it move, all the way until 0200 in the morning and i was like im going to bed it will be done in the morning...

i check it and BAM! it is now frozen. and its like only 35% done.


why is linux acting like windows... i try to transfer large amounts of data, and i always freezes. (dont tell me its my 1TB HDD it is brand new. and it works)

---

### Post by NoaHall on 2009-09-09
Well, try connecting it to other USB/Firewire ports. Try moving it in blocks instead of one big thing (using cp from the command line).

---

### Post by P4man on 2009-09-09
What do windows and ubuntu have in common? Nothing, but they both run on the same hardware and have the same problem for you.. I guess that points to the actual problem, a hardware problem. Maybe your USB ports are underpowered, or the a problem with the drives, cables, hub or usb controller, but I suggest you stop moving (esp moving!) data around until you figured out what causes it.

---

### Post by M!SF!TS on 2009-09-09
> **NoaHall said:**
> Well, try connecting it to other USB/Firewire ports. Try moving it in blocks instead of one big thing (using cp from the command line).




That is waaaay to much work, i will be sitting here in front of my computer for at least a day and a half...

i built a back up script, i wouldn't have to do all this maunal labor. after all thats IS the beauty of linux, and that it the power of the Command Line is it not ?  

why should i have to do all the work ?  it is something my computer should be able to do, and reliably why should i have to do something my computer can do... thats one of the beautiful things about computers... right ? to make people lazy ?  thats one of the reasons why linux and the bash is so powerful right ?

why would i spend a day and a half too 2 days, pointing and clicking ? when i already spent 20 -30 minutes writing a back up script to do it for me...

time is money, money is time, time=valueable resource... i dont have the time to spend almost 2 days manually backing up my file systems!!!

no offense but...

ARE YOU INSANE MAN!!!

---

### Post by M!SF!TS on 2009-09-09
> **P4man said:**
> What do windows and ubuntu have in common? Nothing, but they both run on the same hardware and have the same problem for you.. I guess that points to the actual problem, a hardware problem. Maybe your USB ports are underpowered, or the a problem with the drives, cables, hub or usb controller, but I suggest you stop moving (esp moving!) data around until you figured out what causes it.

Hmmm...  this brings value to the conversation...

im thinking maybe my, WD Passport HDD, it draws power from my computer, my Seagate 1TB draws power from the wall, and is brand new, so i will rule that one out, but maybe my WD Passport,

im not thinking hardware, this computer in BRAND NEW, out of the box 2 months ago... the oldest piece of hardware i am working with are my 2 WD Passports, 1 x 250GB & 1 x 350GB   if it is a hardware issue, then maybe its coming from their... the cables are not being moved the computer is not being moved (just the keys when i type) i literally left it on all night, went to sleep and when i woke up it was frozen...

(i am glad it is not a server. i would be toast...)

---

### Post by M!SF!TS on 2009-09-09
i hope i don't get a bunch of flamers on my post just because of my title...

comparing ubuntu to windows, god that would be a nightmare, some idiots starting a holy war when I'm trying to get a issue solved, it would be like calling HP and and the rep, is in a pissing contest with another rep while im trying to get a issue resolved...


Quote:
"I don't get war, people should focus all that energy from hatred toward something else more productive we can all benefit from" -John Lennon

(honestly i don't know if John Lennon said that, it just sounded like something he would say, so im going to say he said that)

---

### Post by P4man on 2009-09-09
> **M!SF!TS said:**
> 
im not thinking hardware, this computer in BRAND NEW, out of the box 2 months ago... 

A piece of computer equipment failing after 2 months (or much sooner), that would be a world novelty wouldn't it ? :)

> WD Passport HDD, it draws power from my computer

Ding ding ding. Very good chance thats your problem. Especially on cheaper PC's, USB ports are often not be able to power harddisks without a powered hub or using 2 cables to draw power from 2 different ports.

---

### Post by NoaHall on 2009-09-09
....... You're a bit mean? I didn't say move it one at a time, I said in BLOCKS. Until you can locate the problem, no one can help you. So do what I tell you , and let us help you. You don't even have to sit around doing it!

cp /home/noah/Music /media/disk &&
cp /home/noah/Files /media/disk

the "&&" will stop the second command from being run until the first is completed.

---

### Post by 4Orbs on 2009-09-09
Is your Ubuntu partition formatted to ext4? Are the external hdd's formatted in ntfs? I had a similar problem a few months ago and the ext4 was the cause. I went back to ext3 and have not had any problem since.

---

### Post by moody_mark on 2009-09-09
Have a look in your /var/log/messages or syslog file are there any warnings or errors in there when you are transferring these large files?

---

### Post by M!SF!TS on 2009-09-09
> **P4man said:**
> A piece of computer equipment failing after 2 months (or much sooner), that would be a world novelty wouldn't it ? :) 

yeah LOL! if only...

> **P4man said:**
> Ding ding ding. Very good chance thats your problem. Especially on cheaper PC's, USB ports are often not be able to power harddisks without a powered hub or using 2 cables to draw power from 2 different ports.

i was thinking the same thing... im not ruling out anything else, but i think i will start here first... hmmm




> **NoaHall said:**
> ....... You're a bit mean? I didn't say move it one at a time, I said in BLOCKS. Until you can locate the problem, no one can help you. So do what I tell you , and let us help you. You don't even have to sit around doing it!

cp /home/noah/Music /media/disk &&
cp /home/noah/Files /media/disk

the "&&" will stop the second command from being run until the first is completed.


Sorry didnt mean to be harsh... i though you ment copy paste copy paste... point click point click... i was almost pulling out my hair LOL, didnt mean to sound rash


> **4Orbs said:**
> Is your Ubuntu partition formatted to ext4? Are the external hdd's formatted in ntfs? I had a similar problem a few months ago and the ext4 was the cause. I went back to ext3 and have not had any problem since.

I formatted my 1TB to fat32, because i dual boot, and i need a file system that i can use for storing not only my linux and windows files, but also my wife's windows files she wont convert she is afarid and also thinks linux and dumb a geeky :( 

sooooo in other words... my 1TB is fat32 my 250GB and 350GB is ext3, and yeah well i partitioned my Internall HDD in ext3 when i installed 9.04, due to the fact people were having issues on ext4 and it being new, and i need something stable with all the files i got i cannot afford to loose

---

### Post by NoaHall on 2009-09-09
Fat 32? Do you have any files bigger than 4GB by any chance?
I'd also use NFTS instead - quicker, and allows bigger file size.

Also - make sure you don't have Windows illegal characters in file names. Windows can't support the same file names as Linux, so make sure you get any thing that will conflict.

Use clonezilla. It will back things up for you

---

### Post by M!SF!TS on 2009-09-09
> **moody_mark said:**
> Have a look in your /var/log/messages or syslog file are there any warnings or errors in there when you are transferring these large files?

Ohhhhhh yeahhhhh alot of them....

dont pay mind to the last to lines:
Sep  9 13:32:12 linux-box kernel: [59288.103780] usb 1-2: USB disconnect, address 18
Sep  9 13:32:27 linux-box kernel: [59302.792490] usb 1-5: USB disconnect, address 7

they happened because i disconnected my USB HDD's

---

### Post by M!SF!TS on 2009-09-09
i will be back in about an hour i have to goto my work place and file some papers...

---

### Post by M!SF!TS on 2009-09-09
This issue was a file extension issue, im trying to  make fat32 ext3 and ext4 and my ntfs partition all try to play nicely with each other...

in conclusion... if you have issues with backing up, add this to your troubleshooting...

Check what format your drives are in, and ensure they all  play nicely with each other.

[SOLVED]

---

