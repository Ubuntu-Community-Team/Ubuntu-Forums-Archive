---
title: "Just having an issue"
date: 2006-01-29
forum: General Help
---

### Post by l337killa07 on 2006-01-29
Hey guys,

I just recently installed a Ubuntu/Win XP dual boot following the guy from [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/") and it worked fine.  There was also a video on Google Video I watched, as well as taking notes.  I did all this just to be sure that I was installing it correctly.

I'm having just a few issues...:

I didn't have my internet cable plugged in when I was installing, so it didn't detect my network settings.  How do I go about doing this? I'm currently using my XP because I cant use the net on my ubuntu.

My other issue is that when I did the dual boot install, I was SUPPOSED to make the other file systemFAT32, which I didnt.  Since I don't want to have to reinstall again, is there any way of re-formatting the file system?

And just one more issue...After having the whole dual boot set up, on my ubuntu desktop I got 2 hard drive symbols, my C:/ (Main drive) and D:/ (backup drive).  When I click on these icons, it tells me the contents couldnt be displayed, but when I use the file browser I can see the content just fine...would this have anything to relate to with not formatting it into FAT32?

I thank you ahead of time for any responses..and I hope to have these issues resolved sooner than later :)

Thanks,
Killa

---

### Post by morphodone on 2006-01-29
[QUOTE=l337killa07]I didn't have my internet cable plugged in when I was installing, so it didn't detect my network settings.  How do I go about doing this? I'm currently using my XP because I cant use the net on my ubuntu.[/QUOTE]

Go to System > Administration > Networking
click on your ethernet connection
select properties and configure

[QUOTE=l337killa07]
My other issue is that when I did the dual boot install, I was SUPPOSED to make the other file systemFAT32, which I didnt.  Since I don't want to have to reinstall again, is there any way of re-formatting the file system?
[/QUOTE]

you would have to use third party software like Partition Magic. even then there is no guarantee it will work. 
i assume you are using ntfs, which is supposed to have advantages over fat32. the best solution is to have another partiton which is fat32 in addition to your windows/ntfs partition.

[QUOTE=l337killa07]
And just one more issue...After having the whole dual boot set up, on my ubuntu desktop I got 2 hard drive symbols, my C:/ (Main drive) and D:/ (backup drive).  When I click on these icons, it tells me the contents couldnt be displayed, but when I use the file browser I can see the content just fine...would this have anything to relate to with not formatting it into FAT32?
[/QUOTE]

you should be able to see the contents either way.  both ntfs and fat32 are readable. however, write ability is another story.

---

### Post by dcstar on 2006-01-29
[QUOTE=l337killa07].......
I didn't have my internet cable plugged in when I was installing, so it didn't detect my network settings.  How do I go about doing this? I'm currently using my XP because I cant use the net on my ubuntu.
.......[/QUOTE]
System-Administration-Networking select the Ethernet connection - Properties, fill in the required fields.

As for the formatting, don't worry about it (yet), get the networking going first.

---

### Post by aysiu on 2006-01-29
[QUOTE=morphodone]
you would have to use third party software like Partition Magic. even then there is no guarantee it will work.[/quote] Actually, you can format FAT32 from Windows: Control Panel > Administrative Tools > Computer Management > Disk Management. Select the partition and right-click.

If you prefer to do it from Linux, you need a live CD. I recommend using [DiskDrake on PCLinuxOS](http://www.ubuntuforums.org/showthread.php?t=114142), but QTParted on Knoppix should work fine, too.

> 
you should be able to see the contents either way.  both ntfs and fat32 are readable. however, write ability is another story. FAT32 is read/write with no restrictions. NTFS is read-only. You have to mount them with the correct permissions, though. For that, see the fourth link of my signature.

---

### Post by l337killa07 on 2006-01-30
Thank you everyone for your helpful and fast replies :)

In response to what morphodone said:

"you would have to use third party software like Partition Magic. even then there is no guarantee it will work.
i assume you are using ntfs, which is supposed to have advantages over fat32. the best solution is to have another partiton which is fat32 in addition to your windows/ntfs partition."

I was trying to do that, create a middle partition, in a sense with it being the 'bridge' between windows and linux.  But I was just trying to get Ubuntu to work first, and then after that I can make the changes that need to be made.

What I did was I had my main hard drive 60GB: I split that into 2 30GB sections.  One 30 gb section is my windows NTFS.  The other section I partioned in the Ubuntu partitioner..and following the guide I made a small (1GB) swap space, and installed ubuntu on the remaining space.  So I'm thinkng that I should have made the swap space bigger, and made THAT FAT32.

See the thing was I followed two different sets of instructions, one from the site in my first post, and one from [This video on how to dual boot ubuntu]("http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu"), so I may have gotten confused in between.  I even took step-by-step notes to make sure I didn't mess up, and they sure did come in handy.

If you guys say so, I can just re-install Ubuntu.  It didn't take all but maybe an hour on my 933 mHz comp, (even though the video said it took them an hour, and they were on a 3.0 GHz comp!).  That way I'll be able to print out the instructions you give me, and follow them more thorougly.  In a sense, I basically want to be able to read AND write to-and-from Windows..so if that is possible then I'd be very happy :)

Thanks again for the replies, and I hope my initial experience with Ubuntu can be a more...pleasureable one :)

Killa

*EDIT* Also I just wanted to point out that when I booted into Linux just now, and I went to try and access those same drives, not only did it not let me manually, but I tried going to the File Browser (which had let me access them before) and it wouldn't let me do it! I had wanted to make this post on Linux because I wanted to show the partition table using the sudo fdisk -1 command, but I guess not!

---

### Post by l337killa07 on 2006-01-30
Hey guys,

I ran the sudo fdisk command, heres the output in case it helps :

Disk /dev/hda: 61.4 GB, 61471162368 bytes
16 heads, 63 sectors/track, 119108 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       60945    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           60946       62890      979965   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/hda3           62890      119101    28330627+  83  Linux
Partition 3 does not end on cylinder boundary.

Disk /dev/hdb: 4311 MB, 4311465984 bytes
240 heads, 63 sectors/track, 556 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         555     4195768+   7  HPFS/NTFS


That last drive, hdb1, is my backup drive.  Its a physically sepearte one, so for the time being just disregard it, but what I want to do with that drive in the future is make THAT the FAT32 one that both Linux and Windows can read.  And since it is sepearte, I wont have to worry about making partitions.

---

### Post by morphodone on 2006-01-30
[QUOTE=l337killa07]What I did was I had my main hard drive 60GB: I split that into 2 30GB sections.  One 30 gb section is my windows NTFS.  The other section I partioned in the Ubuntu partitioner..and following the guide I made a small (1GB) swap space, and installed ubuntu on the remaining space.  So I'm thinkng that I should have made the swap space bigger, and made THAT FAT32.
[/QUOTE]

Swap space cannot be formatted with fat32.  It has its own filesystem.  It is analogous to the windows page file.  It is used when physical system memory is low.  1GB of swap should be fine.  You shouldn't need any larger.

As for your drives you have a couple of options for here:

1) Change the filesystem of the second hard drive to fat32. Either format it or use partition magic if you need to keep the data on the drive.  Parition magic works better on a drive with no windows install in my experience anyhow.

2) Reinstall ubuntu and parition your drive differently such as -
create logical partitions with the 30GB of space.  create at least three or four partitions.
  partition one - / (root) ~ 7GB
  partition two - swap ~ 1GB
  parition three - /home ~ 18GB to 22GB
  partition four (optional) - /bridge (fat32) ~ 4GB
You can partition the /home parition with fat32 but that is not recommended.  Performace will suffer...

:???: confused yet

---

### Post by morphodone on 2006-01-30
[QUOTE=aysiu]Actually, you can format FAT32 from Windows: Control Panel > Administrative Tools > Computer Management > Disk Management. Select the partition and right-click.[/QUOTE]

He does not want to reinstall again...so formatting is not an option.  

Also, you cannot format a drive in which windows is in use...which his of course  windows would be in his case.

---

### Post by l337killa07 on 2006-01-31
[QUOTE=morphodone]He does not want to reinstall again...so formatting is not an option.  

Also, you cannot format a drive in which windows is in use...which his of course  windows would be in his case.[/QUOTE]


Actually I really have no problem re-installing since the install didn't take that long.  I don't have any files on there yet or any settings saved, so I wouldn't be losing anything.

Man the installation seemed WAY easier watching that Video and reading that guide =\

---

### Post by morphodone on 2006-01-31
[QUOTE=l337killa07]Actually I really have no problem re-installing since the install didn't take that long.  I don't have any files on there yet or any settings saved, so I wouldn't be losing anything.

Man the installation seemed WAY easier watching that Video and reading that guide =\[/QUOTE]

Okay, I did not realize that.  Then you can just blow everything away and start over with whatever partition setup you like.  I know I've done that many times myself.

---

### Post by l337killa07 on 2006-01-31
[QUOTE=morphodone]Okay, I did not realize that.  Then you can just blow everything away and start over with whatever partition setup you like.  I know I've done that many times myself.[/QUOTE]

I don't think its necessarily what partition table I'd LIKE, but what table I NEED to perform what I desire, which is simple : being able to read from and write to Windows..and like I said, the install doesn't take that long at all, so once I get some of this schoolwork out of the way, I'm going to devote 2 hours to fixing the problem...

If anyone has any suggestions, feel free to add them :)

Killa

---

### Post by morphodone on 2006-01-31
Sounds like you figured out what you need to do.

You can install windows on fat32 and have write ability.
or
Just use a 'bridge' fat32 parition like you said.

---

### Post by l337killa07 on 2006-01-31
See thats the thing...I'm not quite sure how to do the "bridge", hence why I posted on here.  I think I'm going to study the instructions just a few more times...try and comprehend it better...and print out the important pages...and if I have any further dilemma I'll be sure to post on here.

---

### Post by l337killa07 on 2006-02-03
Well since I haven't gotten a reply for 3 days...just thought I'd update a bit...

I've been having trouble with the software for my MP3 player..and it seems to be AFTER I installed Ubuntu, so just for my sanity I'm going to uninstall Ubuntu, re-install windows, repartition everything, and hope that works.  I'm planning on hooking up another computer, so maybe that will be my Ubuntu computer.

Oh and also some good news : I have a friend whos learning programming and such, and I gave him an Ubuntu CD, he was pretty happy because he wants to learn to program in Linux, so I spread the word to at least one more person...maybe he can get the college to start using Ubuntu :P

Just trying to help spread the Ubuntu community....

---

