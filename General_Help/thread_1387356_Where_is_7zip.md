---
title: "Where is 7zip?"
date: 2010-01-21
forum: General Help
---

### Post by Hman242 on 2010-01-21
I downloaded and installed 7zip but I can't find the application anywhere. Where is it?

---

### Post by michy99 on 2010-01-21
7zip is a command line program, but you can use the Archive Manager (Applications->Accessories->Archive Manager) with any installed archive program. Also, double-clicking on an archive will open up the Manager. If you want to use the command line, you can read the man page with```
man 7zip
```Use 'q' to quit the man page.

---

### Post by Hman242 on 2010-01-21
I don't have the Archive Manager listed in my accessories. I looked in **System>Preferences **and **System>Administration**[FONT=monospace] and it's not there either. The reason I want to use 7zip is because I want to use it to compress a file, not browse the directory.
[/FONT]

---

### Post by howefield on 2010-01-21
Try going to System > Preferences > Main Menu.

Then click on Accessories in the left pane, and place a check next to Archive Manager in the right pane.

Close your way out and you should have an icon in your Applications > Accessories menu for the archive manager.

---

### Post by jamesisin on 2010-01-21
I wrote a post about installing and using 7zip on Ubuntu:

[http://www.soundunreason.com/InkWell/?p=450](http://www.soundunreason.com/InkWell/?p=450)

If you have questions you can ask them here or there.

(The man page is actually located at man 7z.)

---

### Post by howefield on 2010-01-21
> **Hman242 said:**
> I want to use it to compress a file, not browse the directory.

You can probably right click on the file and choose the compress option.

---

### Post by michy99 on 2010-01-21
> **jamesisin said:**
> (The man page is actually located at man 7z.)

Oops, I should have checked before assuming. Thanks for the correction.

---

### Post by jamesisin on 2010-01-21
Oh, you are creating.  Even easier.

Right-click on a folder and choose "Create archive..." from the context menu.  The create archive should be very strait forward.  7zip archives will be at the top of the drop down.

You may still want to go over my post.

---

### Post by Hman242 on 2010-01-21
There isn't any results in the Package Manager for 7zip. I used Add/Remove Programs and it's listed under installed applications.
How would I go about compressing a file with the Archive Manager?

---

### Post by michy99 on 2010-01-21
In Karmic it is 'Compress' instead of 'Create Archive' (They must have been short on letters.)

---

### Post by howefield on 2010-01-21
> **Hman242 said:**
> There isn't any results in the Package Manager for 7zip.

Try p7zip

> p7zip is the Unix port of 7-Zip, a file archiver that archives with
very high compression ratios.

---

### Post by ron999 on 2010-01-21
> **Hman242 said:**
> There isn't any results in the Package Manager for 7zip. I used Add/Remove Programs and it's listed under installed applications.
How would I go about compressing a file with the Archive Manager?
 There is a front-end for file compression aps. It is called **file-roller**.
You can install it with Synaptic Package Manager.
It will appear in your accessories menu.

---

### Post by Hman242 on 2010-01-21
When I right-click on the file, there is not compress option.

Both p7zip and file-roller are marked as installed in the Package Manager. I'm a newb when it comes to Ubuntu, try and walk me through it.

---

### Post by jamesisin on 2010-01-21
It's "Compress" in 9.10; earlier it's "Create archive...".

---

### Post by Hman242 on 2010-01-21
I'm running 9.10. Could this have anything to do with the type of file I'm trying to compress?

---

### Post by ron999 on 2010-01-21
> **Hman242 said:**
> try and walk me through it.

Use file-roller.
Create an archive, then add file(s) which are to be compressed.

**Applications > Accessories > Archive Manager > File > New**

Then give your archive a name and choose the 'Archive Type' at the bottom, choose 7-zip if you want.
When you've created the archive add your file(s).

---

### Post by jamesisin on 2010-01-21
What kind of file are you trying to archive?

---

### Post by Hman242 on 2010-01-21
.iso

---

### Post by jamesisin on 2010-01-21
I had a feeling.  An iso is already an archive.  You can put it in a folder and create an archive of that folder.  Not sure you'll see much in the way of compression though.

---

### Post by Hman242 on 2010-01-21
I've been contemplating that, but is there a file type I can compress what I've extracted that I could put on a disc and still run it like the .iso would?

---

### Post by Leppie on 2010-01-21
you can do it from the cli:
```
cat /path/to/imagename.iso | gzip > isoimagename.gz
```

---

### Post by jamesisin on 2010-01-21
> **Hman242 said:**
> I've been contemplating that, but is there a file type I can compress what I've extracted that I could put on a disc and still run it like the .iso would?

I don't think so.  You'd have to unarchive the iso every time.  What is your objective in compressing the iso?  Maybe you'd be better off taking the files off the iso (by opening it with Archive Manager and Extracting) and putting those files into a 7zip archive?

---

### Post by Hman242 on 2010-01-21
I've heard that if you extract the files and recompile them it can make the file smaller. What's a good program that can recompile the files?
I want to compress it so it can fit on a disc. It's 800MB over.

---

### Post by jamesisin on 2010-01-21
I don't know that "recompile" is the correct term, but that's what I was describing above.  Extract the files into a folder.  Then use 7zip to create an archive (as we've been discussing) from that folder.

---

### Post by Hman242 on 2010-01-21
I'm wanting to put it back in an .iso archive. Can 7zip do that?

---

### Post by Leppie on 2010-01-21
> **Hman242 said:**
> I'm wanting to put it back in an .iso archive. Can 7zip do that?
you could burn a 7zip archive onto a cd, or use an application like brasero to create an iso containing the 7zip archive

---

### Post by Hman242 on 2010-01-21
But would that work? The .iso is a game archive and I don't know if I burned that to a disc I could set it up and etc.

---

### Post by Leppie on 2010-01-21
> **Hman242 said:**
> But would that work? The .iso is a game archive and I don't know if I burned that to a disc I could set it up and etc.
could you elaborate on what you exactly would like to achieve?
do the games have to run directly from the cd without unpacking? or does the cd have to be bootable? or something else?

---

### Post by Hman242 on 2010-01-21
They need to be unpacked by installation. I have no experience in this field and am sorry if I am vague or incorrect. I'm currently doing something, but will get back to you tomorrow.

---

### Post by jamesisin on 2010-01-22
I don't know the answer to your last question, so I'll someone else field that.  I can say that you will be able to take your files and create a DVD (instead of a CD) out of them.  That would solve your size problem.

---

### Post by Hman242 on 2010-01-24
Back from personal things. Putting it on a DVD is the root of my problems. It's too big.

---

### Post by jamesisin on 2010-01-24
What is the size of the iso?

---

### Post by Leppie on 2010-01-24
> **Hman242 said:**
> Back from personal things. Putting it on a DVD is the root of my problems. It's too big.
i thought you said the image was about 800megs?
a dvd can contain 4500megs... can't see how a dvd is too big...

---

### Post by jamesisin on 2010-01-24
So did I, but he actually said the iso was 800 MB too large.  Let's find out how large it actually is.

---

### Post by Hman242 on 2010-01-25
It's 5.5GB. I have a DVD5 that holds up to 4.7GB, and I'm thinking about just going and buying a DVD9. I've tried to mount the .iso before I spend the money on some but I keep getting an error. I get:

wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is wrong?

---

### Post by Leppie on 2010-01-25
> **Hman242 said:**
> It's 5.5GB. I have a DVD5 that holds up to 4.7GB, and I'm thinking about just going and buying a DVD9. I've tried to mount the .iso before I spend the money on some but I keep getting an error. I get:

wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is wrong?
you may have to install udf support first (some dvd's use this fs):
```
sudo apt-get install libudf0
```

furthermore, how do these games install? are these windows games, or linux games? if they're linux games, can you not create a script that unpacks the selected games?

---

### Post by Hman242 on 2010-01-25
It's a Windows game that I will be running in WINE. After installing that I still have the same problem. I get:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Leppie on 2010-01-25
> **Hman242 said:**
> It's a Windows game that I will be running in WINE. After installing that I still have the same problem. I get:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
what is the output of the command?
```
dmesg | tail
```

---

### Post by Hman242 on 2010-01-25
[FONT=monospace][13448.755726] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[13449.589922] i2c-adapter i2c-2: unable to read EDID block.
[13449.589926] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[13449.594411] i2c-adapter i2c-2: unable to read EDID block.
[13449.594414] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[13810.342945] ISOFS: Unable to identify CD-ROM format.
[14938.611519] ISOFS: Unable to identify CD-ROM format.
[14954.789592] ISOFS: Unable to identify CD-ROM format.
[15065.436892] ISOFS: Unable to identify CD-ROM format.
[19481.921794] npviewer.bin[16329]: segfault at a58018b0 ip 00000000a58018b0 sp 00000000ff8744ec error 14

[/FONT]

---

### Post by Leppie on 2010-01-25
what format is the iso/dvd?

---

### Post by Hman242 on 2010-01-25
Format? The .iso is a .iso. I don't know what you're asking.

---

### Post by Leppie on 2010-01-25
> **Hman242 said:**
> Format? The .iso is a .iso. I don't know what you're asking.
how was this iso created?

---

### Post by Hman242 on 2010-01-25
It was ripped from a disc.

---

### Post by Leppie on 2010-01-25
> **Hman242 said:**
> It was ripped from a disc.
in windows, in linux, whith which application?

---

### Post by Hman242 on 2010-01-25
I don't know how, but I know it was in Windows. Sorry, I wasn't the one who ripped it.

---

### Post by Leppie on 2010-01-25
> **Hman242 said:**
> I don't know how, but I know it was in Windows. Sorry, I wasn't the one who ripped it.
iso should be a direct representation of the data on the disk, but depending on the layout chosen to burn the disk you may need to install additional packages.
can you open it with package manager? if you can, extract it and create a new iso in ubuntu.

you could also try to install the hfs package:
```
sudo apt-get install hfsplus hfsutils
```

---

### Post by t4thfavor on 2010-01-25
Try ```
sudo mount /path/to/file.iso /path/to/mountpoint -o loop
```

where mountpoint is a folder you created somewhere.


Then it will appear to the system to be a cdrom, you can then use wine to install the game. They make most games bigger than a standard dvd on purpose to fight piracy.

Also you can remove some of the crap by deleting stuff from the mounted folder, and then re-creating the iso from the command line.

An easier solution would be to use ISO Master, and remove things with that, and saving it off to a new ISO.


You can install ISO Master from the software center, its really easy to use.

---

### Post by Hman242 on 2010-01-25
The

sudo mount /path/to/file.iso /path/to/mountpoint -o loop

worked. Thanks a million. I have ISO Master, but don't know how to create an .iso with it. Could you tell me incase I need to make one in the future?

---

### Post by TracyO on 2010-02-14
> **jamesisin said:**
> Oh, you are creating.  Even easier.

Right-click on a folder and choose "Create archive..." from the context menu.  The create archive should be very strait forward.  7zip archives will be at the top of the drop down.

You may still want to go over my post.

I just want to say thanks!  I've been trying to figure out how to get into Bzip or 7zip (thinking it was a program like you'd use for burning a cd or converting files), and this post finally cleared that up for me.  

I also just finished a few minutes ago sending one by one the files I hoped to compress.  Oh well.  Now I've got it for next time.  I had no idea it was this simple.  Thank you!

---

### Post by jamesisin on 2010-02-14
TracyO - Glad to be of service.  If you have questions about my instructions you can ask them either here or on my blog post.

---

