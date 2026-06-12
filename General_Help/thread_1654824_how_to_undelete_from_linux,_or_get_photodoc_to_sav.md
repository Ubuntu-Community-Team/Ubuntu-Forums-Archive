---
title: "how to undelete from linux, or get photodoc to save to other harddrive"
date: 2010-12-28
forum: General Help
---

### Post by thesnappysneezer on 2010-12-28
I feel like an idiot, I hate myself so much right now. A little information can be a dangerous thing. Installing wiped my hardrive, I tried selfbooting spotmau 2009, it froze, took forever then a power outage after 4 days, urgh, after finding 2,500,0000 files, but it was constructing a file list for those 3-4 days. This is approximately 600gb of 750ogb hardrive. this was Vista, 60,000mp3s, some photos that can never be replaced. Someone suggested puppy and I burnt it to disc and it seemed to be not capable of finding things, I may not have known hpw to properly use it but it seems like ti might have been a backdoor into windows, ?I do not know. I tried TestDisk, self booting, in Gpart or somesuch, it found nothing, photorec looked like it instructions said as such that it was finding something in a long search that was to take a few hours but stopped saying it had no place to put the file. I went ahead and spent money on a 1.5 Terrabyte harddrive for puppy as I understood that I needed it to recover the data but puppy did not function as I had thought. If I could get photorec to recgnize and place the files in that harddrive it would be great but it does not seem to no it is there even though the instructions said .media or .mnt neither were large enough. I am so frustrated and stressed right now. All I had really was my computer, I miss it so much, please help me. I have no more money. I do not have a Vista Cd and it would not restore that other more important data anyway. I do not have Windows anymore so programs that run on Windows will not work. Why do all ther google searches for linux and recover or undelete come up with Windows programs to recover linux? Please some one help me soon, I am a bout to go crazy, I'm crying like a little girl right now, please help, please, please, please.

---

### Post by mikewhatever on 2010-12-28
Here is just the howto you are looking for. Hope it works.
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

good luck.

---

### Post by thesnappysneezer on 2010-12-29
thanks for the response but unfortunately there seems to be no way to get the program from those links or test scan to actuallly work in mint, same goes for ndswrapper, could it be because I am downloading it from a windows machine? The test disk in gparted does not recognizer my other harddrive when selectiing where to put it, even in following the tail end of those directions, seems to loop up, the right buttton seems like it doesn't really do that. while running miint it recognized the other harddrive, actually while running test drive, it asks if that other hardddrive is what I want to put it on. God I am shaking right now. Please help. Someone.

---

### Post by mikewhatever on 2010-12-29
That last post doesn't make much sense.
Why can't you download testdisk? Why do you need ndisrapper now?
Just follow the howto step by step, nothing else, and if there are any problems, specify exactly what they are.
If you have to use Linux Mint, do make sure you download the correct files for your version, because the suggested links are for Hardy Heron (8.04).

---

### Post by thesnappysneezer on 2010-12-29
instructions make little sense, the thing trys to download the program and can't hook up to the internet rather than recognize that i have them on the computer double clicked them and they gave an error message, I used ones for linux from test disk site, I also installed another way that unpacked them but didn't go right either this whole thing is a mess to me, I'm using  my brothers laptop to download and communicate this and I'm not use to them, it keeps randomly opening links I think because the arrow is on top of them or something and buttons are missing on it, not used to laptops, hate them now so sorry if I am getting double frustrated, also the plug keep falling out. Nothing seems to be working or making sense. Somewhere I read some one thinking that someone with a similar problem was being affected by downloading the things on windows..I just realizewd though the libntsf I did not get proper, though I am having a hard time googling a proper one for my system which is mint 10 64 bit

Also I have said, I have photorec in a bootable disk and in it, pressign right on -- or whatever or any field does not give me the option to use my external harddrive. Hopefully whatever I put on here will but I wonder if it is worth the effort. I'd like to get online with the thing, it seems the instructions given were for those with online capabilites.

---

### Post by mikewhatever on 2010-12-29
Right, thank you for providing useful info. As Mint 10 is based on Maverick, here are the corresponding links for Maverick 64bit.

[Testdisk 64bit]("http://packages.ubuntu.com/maverick/amd64/testdisk/download")

[libntfs10 64bit]("http://packages.ubuntu.com/maverick/amd64/libntfs10/download")

Again, if you have any problems following the howto, specify exactly what the problem is. I am having a hard time understanding your posts.

---

### Post by thesnappysneezer on 2010-12-29
ok, thank you so much that worked, I was using the wrong type of files, should all programs I install have amd 64 in the title? Is there an nswrapper as such? I googled it and saw some links saying it wasn't working right but those were from 2005. 

oh, the libntfs one was actually already installed in the downloaded mint, hopefully they will include testdisk in the next one. 

Sorry, my blood pressure was up and this happening was the icing on the cake of several other bad things happening. I have also been without sleep.

Is it safe to fool around with the system while it is doing this, or is it best to leave it alone?

If the power blacks out will it have to be redone? Are the files I see counted already saved to the harddrive or will I have to wait until it is over and then get access to them?
If so, will a finalization of such a process take as long as the eta I see now or longer or less, in general, that is?

One problem, and arrgggh it told me I didn't have enough room on my empty 1.5 terrabyte drive after finding about 6000 files, I redid it just in case I made an error but it is running again, nearing that point once more but more slowly, is 15 hour eta for about 600gb, about right? I understand that this just recovers files but not the names, would you know if things like mp3 tags are stilll attached? Presumably all programs I have are a wash with this method. Would another service stillbe able to recover vista?

Acch, it stopped again.

---

### Post by thesnappysneezer on 2010-12-29
crickey now it says it only has 1500 / 1300 GiB (RO)

---

### Post by thesnappysneezer on 2010-12-29
ok, it did not save to the other harddrive, it save to my home folder and I can't delete anything there, says permission denied.

---

### Post by mikewhatever on 2010-12-29
> **thesnappysneezer said:**
> ok, thank you so much that worked, I was using the wrong type of files, should all programs I install have amd 64 in the title? Is there an nswrapper as such? I googled it and saw some links saying it wasn't working right but those were from 2005. 

Yes, almost all packages are available in 64bit architecture including ndiswrapper.
 

> Sorry, my blood pressure was up and this happening was the icing on the cake of several other bad things happening. I have also been without sleep.

Have a sip of water, it usually helps.

> Is it safe to fool around with the system while it is doing this, or is it best to leave it alone?

If the power blacks out will it have to be redone? Are the files I see counted already saved to the harddrive or will I have to wait until it is over and then get access to them?
If so, will a finalization of such a process take as long as the eta I see now or longer or less, in general, that is?

I wouldn't fool around too much, better be on the safe side here. Do let it finish, cause if you stop, it'll start all over again. It does take a while.

> 
One problem, and arrgggh it told me I didn't have enough room on my empty 1.5 terrabyte drive after finding about 6000 files, I redid it just in case I made an error but it is running again, nearing that point once more but more slowly, is 15 hour eta for about 600gb, about right? I understand that this just recovers files but not the names, would you know if things like mp3 tags are stilll attached? Presumably all programs I have are a wash with this method. Would another service stillbe able to recover vista?

Acch, it stopped again.

Odd, 1.5TB should be enough to recover 750GB. Could it be that the drive is filled with data from previous tries? File extensions should be recovered, but I don't know how to recover the names.

---

### Post by mikewhatever on 2010-12-29
> **thesnappysneezer said:**
> ok, it did not save to the other harddrive, it save to my home folder and I can't delete anything there, says permission denied.

The howto explains exactly how to avoid that. To delete the files open the file browser with the following command:

gksudo nautilus

That should allow full access to the saved files, or just reboot.

---

### Post by thesnappysneezer on 2010-12-29
will do but also I just rebooted the system and a red circle with a white line in it comes up and says could not update ICEauthority file /home/ (myname)/.ICEauthority


after closing that I get a Low Disk Space The Volume "Filesystem root has only 0 bytes disk space remaining

---

### Post by thesnappysneezer on 2010-12-29
did as you sais and it says Nautilus could not create the following required folders: /root/Desktop,/root/.nautilus

---

### Post by mikewhatever on 2010-12-29
Since the disk is now full, you'll need to boot from a live cd and delete files, or, perhaps the recovery mode will still work.

---

### Post by thesnappysneezer on 2010-12-29
live mint, or g parted?

---

### Post by thesnappysneezer on 2010-12-29
please tell me what to do

---

### Post by thesnappysneezer on 2010-12-29
omg, my 1.5 tb is reading as a 1.o mb filesystem

---

### Post by thesnappysneezer on 2010-12-29
also The panel encountered a problem while loading "OAFID:GNOME_Indicator Applet Do I want to delete applet

---

### Post by thesnappysneezer on 2010-12-29
do you reccomend trading in my harddrive, this may be broken or something, this keyboard laptop does not recognize it. also should I reinstall mint? oit seems broken so tired of everything. thank you for your help:cry:

---

### Post by mikewhatever on 2010-12-29
> **thesnappysneezer said:**
> live mint, or g parted?

Either should do. On the other hand, you could just boot a Mint disk and follow the howto step by step. Nobody said you had to work from an installed OS, in fact, the howto suggests working from cd.

---

### Post by thesnappysneezer on 2011-01-03
Hey been down a while, I tried Spotmau again, power outed then when it was four days running again Spotmau just rebooted and acted like nothing had happened. Starting photorec again. I got a new external harddrive, it seems the other one was buggered. Currently it is working and should be done in 9 hours. This being said, I still get those errors  and can't delete files dropped in my home for some reason. I can't get nautilus to run, also it keeps logging me out if I leave it idle too long , I need to get it not to do that but and ndswrapper working, and then wine and maybe all will feel better. I just hope I can recover some things right now. Thank you so much for all of your advice.

Now I wonder, if a file is recovered does that mean that it is works? 77000 files have been found, 9122 of my mp3s of 60000 so far, 9401 of my jpgs, 22502 txt, wow Reading Sector 152183000/1465149168, hmm, zip files 1214, those programs, files in them would be safe from renaming?

---

