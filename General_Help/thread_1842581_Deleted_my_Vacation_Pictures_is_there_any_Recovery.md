---
title: "Deleted my Vacation Pictures is there any Recovery?"
date: 2011-09-11
forum: General Help
---

### Post by solaralchemy on 2011-09-11
Ok I did something really dumb.
I deleted a whole bunch of photos on a SD card.
I originally intended to just delete one image but failed to notice until it was to late that I had all images selected therefore I lost all the pictures I took today on my vacation.
I have read that once a file is deleted in Linux it's gone for good
but I'm hoping in this case that I might be wrong and that there might be some miracle method to recover my photos because they are pretty important to me.
I'm pretty sure I'm going to be told it't hopeless but if anybody does have any possible fixes it would be greatly appreciated.

---

### Post by WorMzy on 2011-09-11
Stop using the partition immediately.

Boot into a Live CD or something, then check back here.

---

### Post by solaralchemy on 2011-09-11
unfortunately I'm over in the UK and I don't have a live CD and I can't burn an ISO I left my CD burner back in the states.
Also I didn't put this in my OP but I also unmounted the card for a second then tried to put it back in to get the computer to recognize it.
I have manged to do one dumb thing after another.

---

### Post by WorMzy on 2011-09-11
Forgive the shortness of my post above, I missed the point about the partition being on an SD card, but it is *crucial* that you limit the amount of data written to the partition after accidentally deleting something. Once something is deleted, that space on the partition becomes available to the operating system for writing to. And once data has been written over the space that old data used to occupy, you can't recover the old data any more. At least, not in it's entirety.

There are ways to recover deleted data, assuming, of course, that you just did a simple deletion, and not a data shred. Personally, I recommend using [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") for the job.

Using it is pretty self-explanatory, but here's a tutorial, just in case: [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by coffeecat on 2011-09-11
> **solaralchemy said:**
> 
I'm pretty sure I'm going to be told it't hopeless but if anybody does have any possible fixes it would be greatly appreciated.

No, it's not hopeless.

As WorMzy said, don't use the SD card so as not to overwrite anything.

Have a look at this link:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Scroll down past the testdisk section which won't help you. Testdisk is for recovering lost partitions. Your partition will still be OK - it's the files that have been deleted. Go to the photorec section (photorec comes with testdisk). That will recover all your lost images so long as you let photorec restore them to another physical medium.

Yours is a more straightforward situation than many people have since you will only have photos to recover. The recovered filenames will not be what the camera assigned, but the EXIF data will be intact and you will be able to rename all the recovered files with suitable software.

The alternative is to see if you can find some file recovery ("undeleting") software that runs in Windows, but I don't know of any.

**EDIT**: I see that WorMzy has posted again while I was typing. Use both the link that WorMzy provided and the one I posted. WorMzy's is more comprehensive - mine is a little more user-friendly!

Also - about not having a bootable CD. Since the files to be recovered are on a SD card, you can use Ubuntu from your hard drive.

---

### Post by WorMzy on 2011-09-11
Actually, after re-reading the first post properly, there's a chance that the files weren't actually "deleted". Open up the SD card again, and press Ctrl+H to show all files. Look for a folder named ".Trash-1000". If you have that folder, then you may well find the photos inside the "files" subdirectory.

Good luck.

---

### Post by warehouse@karmickoala on 2011-09-11
Hey there ! First af all, I do not know your configuration but anyway I suggest you install undelete software. I am sure that you will be able to find such programs in let's say ubuntu.com or sourceforge.net you know these kind of sites. Also do not forget that you have Google search or any Search-engine based web search in your hands. Hope I helped :-)

---

### Post by solaralchemy on 2011-09-11
Thank you for the advice it's getting late over here and I only had a little time to go over suggested options.
But from what I understand as of right now if I don't add any files
to the card there is still a possibility of file recovery on it.
I can get another sd card and take photos on this one and try to recover the lost data on the first card at a latter point hopefully.
I think in the future I'm going to start using the move to trash option because I have been very liberal with using delete and now it has cost me for the first time.
I always had a feeling I would end up doing something like this at some point.

---

### Post by solaralchemy on 2011-09-11
> **WorMzy said:**
> Actually, after re-reading the first post properly, there's a chance that the files weren't actually "deleted". Open up the SD card again, and press Ctrl+H to show all files. Look for a folder named ".Trash-1000". If you have that folder, then you may well find the photos inside the "files" subdirectory.

Good luck.

I tried this and it only showed three pictures and they where all crappy blurry ones that I took.
Bummer

---

### Post by BakerCook on 2011-09-12
The first thing to do when you lost data is to stop using the drive any further to increase the chances of recovering data. The next thing is to use a good data recovery tool to recover the data. There are so many tools available some are free and some are paid. its hard to say which is better because there are situation when a particular tool is not available to recover data but other tool can recover efficiently but in other situation the same software recovers your data. So go and try the software yourself. demo versions are available to check the preview of data which can be recovered. Here i would suggest you to try "Kernel for Linux " an efficient tool for recovering data

---

### Post by solaralchemy on 2011-09-12
Thank You Very Very much Coffee Cat Photorec did the job and saved
my pictures.
I'm grateful for the help.
The only issue I have now is that it left a file behind called

recup_dir.1 and it has a pad lock on it and I do want to delete  this since I moved the saved pictures to another directory.

---

### Post by solaralchemy on 2011-09-12
Thought I would share some pictures
in thanks

---

### Post by solaralchemy on 2011-09-12
Some more pics from Avebury

---

### Post by solaralchemy on 2011-09-12
A few more
Once again thank you

---

### Post by WorMzy on 2011-09-12
I take it those are all from the UK?

I can tell because it's overcast. [IMG]http://i.imgur.com/lW7JO.gif[/IMG]


The file in question, have you tried deleting it as superuser?

```
sudo rm /path/to/recup_dir.1
```

---

### Post by westie457 on 2011-09-12
> **solaralchemy said:**
> Thank You Very Very much Coffee Cat Photorec did the job and saved
my pictures.
I'm grateful for the help.
The only issue I have now is that it left a file behind called

recup_dir.1 and it has a pad lock on it and I do want to delete  this since I moved the saved pictures to another directory.

Hello
to remove the recup_dir you will have to open nautilus as root from a terminal using ```
gksudo nautilus
```_Be very careful with what you delete_.
select the directory and use Shift=Del to completely remove otherwise it will be hidden on your hard drive taking up space.

---

### Post by coffeecat on 2011-09-13
@solaralchemy, I'm glad you managed to recover your pictures, and thanks for sharing.

> **WorMzy said:**
> I take it those are all from the UK?

I can tell because it's overcast. [IMG]http://i.imgur.com/lW7JO.gif[/IMG]

Do you know Gilbert & Sullivan's Trial by Jury? When the jury are sworn in, they sing.

> To all of this we make reply
By the dull slate of yonder sky:
That we will well and truly try.

Our Victorian forebears had as much fun complaining about the weather as we do. :)

---

### Post by solaralchemy on 2011-09-13
I tried nautilus in root but it only gives me access to my desktop and file directory. 
I put the file that needs to be removed in my Pictures Directory and that does not show up.
I put cd pictures in the terminal before I put in the command but it still only  opens to the desktop and file directory.

---

### Post by solaralchemy on 2011-09-13
> **WorMzy said:**
> I take it those are all from the UK?
[/CODE]


Yeah Yesterday I got pictures of Glastonbury Tor and the isle of Avalon which is part of the Arthur Legend.
Today I'm going to Stonehenge. 
I been going to a lot of the Neolithic places around the UK.

---

### Post by solaralchemy on 2011-09-13
The weather has been strange here.
it has been fluctuating between sunny and cloudy and back again in a matter of minutes.
I even saw a rainbow over silsbury hill.
  Apparently the remains of Katia are hitting parts of the UK.

---

### Post by WorMzy on 2011-09-13
> **solaralchemy said:**
> I tried nautilus in root but it only gives me access to my desktop and file directory. 
I put the file that needs to be removed in my Pictures Directory and that does not show up.
I put cd pictures in the terminal before I put in the command but it still only  opens to the desktop and file directory.

Nautilus as root should be able to go (practically) anywhere on the filesystem. The SD card should be mounted under /media/, so have a look in there.

---

### Post by coffeecat on 2011-09-13
When you run "gksudo nautilus, it opens in root's home, so the desktop folder you are seeing is root's. You need to go up a level into the root (different meaning!) of the filesystem and then open the /home folder and then your account folder.

Alternatively...

> **solaralchemy said:**
>  
I put the file that needs to be removed in my Pictures Directory and that does not show up.

If you mean the Pictures folder in your hard drive, open nautilus with:

```
gksudo nautilus ~
```

That will open a root nautilus but in your home folder.

Another thing to beware of. If you simply hightlight the file you want to delete and press the delete key it will merely be sent to root's trash, not yours. So use the shift+delete combination to do an immediate delete.

---

### Post by solaralchemy on 2011-09-13
Thank you that worked out well.

---

