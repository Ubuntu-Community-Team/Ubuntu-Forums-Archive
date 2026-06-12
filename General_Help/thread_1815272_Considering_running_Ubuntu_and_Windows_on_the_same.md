---
title: "Considering running Ubuntu and Windows on the same machine. Advice?"
date: 2011-07-31
forum: General Help
---

### Post by trogdor458 on 2011-07-31
This isn't really a question, but any feedback will still be greatly appreciateed.

A little backstory for those interested: I am using a moderately priced laptop about a year old (64-bit, 500 GB HD, 4 GB RAM, Intel Core i3-350M processor, which I think is quadcore and over 2 GHz). It originally had Windows 7 installed, but a couple of weeks ago I got a very nasty rootkit kind of malware, which inevitably led to a complete wipe (I rescued my important files first). It would shut down my computer before even reaching the login screen, so this was not a thing I could live with. Anyways, this prompted me to use a rewritable CD I had lying around to make an installation disk with (I decided on Linux, since it would be easier obtain), and I wanted to make sure I didn't have any hardware problems. Low and behold, I am now an Ubuntu user.

I've been quite impressed with Ubuntu so far, and must say you've done a very good job with it. =)
The only problems I've had have all revolved around emulation and virtualization. I know now if I want to play any 3D Windows games, Virtual Box nor Wine will cut it (Virtual Box has troubles, and Wine seems to lack hardware acceleration). I am considering backing up my files once more, partitioning my hard drive, and using Ubuntu for most purposes, while reserving Windows for games only. I have a few concerns though, as well as questions. Feel free to answer which ever ones you can (several will reflect my inexperience). Bulletin time!

1) Will they be friendly to each other?
I recall reading that Ubuntu will play nice, but Windows might not, and could mess with the partition holding Ubuntu's OS and files. This is a BIG concern of mine.

2) Viruses?
I plan on denying the Windows OS internet access, but on the off-chance I get another rootkit, would it cause problems with both OS's, or just Windows? Another big concern.

3) Will they share?
Ideally I'd like to have Windows running in the background to handle my occasional need to play a game, like with Wine. Otherwise, I'd want a shared folder of some sort.

4) If Windows ever poops out, could I reinstall the OS as easily as I do with Virtual Box?
Seriously, Virtual Box makes it pretty easy.

5) Should I choose Windows 7?
XP 64-bit seems like it would have less support when dealing with games.

6) Should I choose Ubuntu 10.04?
I have 11.04 right now, but I've gotten used to the Gnome interface, and again feel like 10.04 will be more stable overall. The "long-term support" also sounds interesting.

7) Is it worth it?
I'm considering holding this off until my next computer purchase otherwise.

I think I had more questions, but I've forgotten several after typing all of this. You may also ask me questions about my plans to make sure I don't overlook anything. Please treat it as if though you're planning on doing this to your computer, and you've tasked me with the job. =)

Thanks for any help you may provide!

---

### Post by mikewhatever on 2011-07-31
1. Friendly? They are two different OSs, you might talk about friendliness if they needed to interact, but they won't when dual booting. Windows doesn't mess with Ubuntu partitions, it can't even see them properly.

2. No, Windows malware doesn't work on Linux.

3. If you want two OSs running at the same time, virtualization is the way to go. There is no other way you can run Ubuntu and Windows (in the background). 
Ubuntu will have full read/write access to NTFS partitions. Share that way if you want or create a separate data partition.

4. Installing in Vbox is pretty much the same as installing on real hardware. Regardless, I'd advise imaging the partition, so that a reinstall is never needed.

5. Not sure really. 

6. Probably not. Test it, but I doubt 10.04 will have good support for the latest hardware.

7.That's for you to decide.

---

### Post by techtabu on 2011-07-31
How are you using the Ubuntu now? Are you using through virtual box/ installed using wubi? Your Windows installation method may sometimes mesh up everything. For example, if you use HP machine they use all four primary partions for their purposes like Hp utilities, recovery etc. Then if you try to parallel boot linux it may mesh up with windows bootloader and you may not be able to use windows. If you want to use both, i may recommend you to use wubi to install linux. Wubi install linux as another software within windows, but during booting it allows you to select windows or linux. Still, i don't think you can run Windows in the background as said by mikewhatever. 
There will always less support for 64 bit OS, since it is new. 
I don't know about 11.04... I'm still using 10.10 and fine with it.. 
Linux is always worth it... Windows as well depending on your need..

---

### Post by trogdor458 on 2011-07-31
techtabu: Ubuntu is currently my primary OS. I am virtualizing Windows through Virtual Box, but have never heard of wubi until just now.

mikewhatever: It's good to know you don't think they'll mess with each other, but just in case, I'll be looking for a guide from someone with a similar setup. Also, 10.04 might be alright with my hardware, since it came out shortly before I got my computer. I will consider keeping with 11.04 though, since I already have it written to a disk.

Note that this would be a kind of luxury for me, and I do not need Windows for playing high-end games. My college is filled with plenty of people who will gladly let me play. =)

---

