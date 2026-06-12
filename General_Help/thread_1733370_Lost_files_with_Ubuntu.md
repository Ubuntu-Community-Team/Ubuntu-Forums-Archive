---
title: "Lost files with Ubuntu"
date: 2011-04-19
forum: General Help
---

### Post by Slorg on 2011-04-19
Hey, 

Recently my sister asked me if I could store some photo's on my computer because she had to do a re-install of Windows. 
I did copy the files to my computer, and they were stored there for a few days.

Then I had problems with a certain piece of software in 64-bit, so I wanted to re-install my computer with a 32-bit Ubuntu version. (I've only got 2GB of RAM, so it doesn't have any practical advantages to use 64-bit)

Then I decided to store the photo's on my Ubuntu One folder, so I told Ubuntu to synchronize the specific folder.
It did synchronize it, but then I decided to copy the folders to my USB drive.

And here's where the trouble started:
First I told Ubuntu one to unsync the folder, I don't want to waste too much space on my cloud. But then it somehow deleted the files. 
I do still got some files left (I believe it are the ones that weren't synced), but I lost most of it.

After some research I discovered a tool called photorec which can be used to recover deleted files, so I've burned a system-recovery OS. (I believe it's Gentoo-based, it's a Linux)
The distro has some useful tools, but I only needed photorec.

After some struggling, I was able to mount a usb drive and then I started photorec telling me to find all jpg, png, gif, bmp, mp3, flv, doc and pdf file extensions.

I've got now 2 usb disks full of data (one of 8gb, and one of 4gb, so 12gigs total). I did search all folders, but no success yet. I am pretty amazed how much it does find, including some Windows 7 wallpapers from over a week ago. (I even re-installed my computer with Ubuntu only)

The tool however is only at its beginning and I've already got gigabytes of data. I think I'll search for my 120gb iPod and hook that thing onto my computer.

So here's my question:
Does anybody has tips on recovering the files? (It are mostly jpg's I believe, I'm a fool for telling the program to look for mp3's and flv's too)
And is it possible to files are still stored on my hard-disk? I didn't delete them myself, I think Ubuntu One did.

P.S. Is there any why I could get them from Ubuntu one? (I did sync them earlier, they may still be at their servers. (Not on my account according the websites) But I believe they're not allowed to do anything like that)

Here are my specs:
AMD Athlon X4 3.0GHz processor (quad-core)
2GB DDR2 800MHz RAM.
500GB Hard-drive
I do use Ubuntu 11.04 (natty narwhal), but I believe that's not relevant to my problem.
And some more irrelevant stuff.

P.P.S.
I'm not sure I posted this at the right section, there are arguments to place it elsewhere. But I figured this section was the most relevant to my problem.

Thanks in advantage,

Sjoerd

---

### Post by Grenage on 2011-04-19
Since the files were on your disc, there is a reasonable chance that you'll be able to recover them.  Unfortunately, you will be looking through a lot of data if the system has been running for a while.

---

### Post by Slorg on 2011-04-19
Yes, it's working.
I stopped the whole thing, and then restarted it telling him to only do .jpg and .bmp files. (The files I needed where mostly photo's, all the other stuff is a lot easier to replace)
The time to complete the process has been reduced from really, really, long to a few hours.

It says it will take another 46 minutes, but it found the photo's I needed.
I have a lot of sorting to do, but I can describe this operation as successful :guitar:

I'm really happy because I felt kinda responsible for messing up somebody else's files. Especially because self-made photo's are irreplaceable.

---

### Post by Grenage on 2011-04-19
> **Slorg said:**
> Yes, it's working.
I stopped the whole thing, and then restarted it telling him to only do .jpg and .bmp files. (The files I needed where mostly photo's, all the other stuff is a lot easier to replace)
The time to complete the process has been reduced from really, really, long to a few hours.

It says it will take another 46 minutes, but it found the photo's I needed.
I have a lot of sorting to do, but I can describe this operation as successful :guitar:

I'm really happy because I felt kinda responsible for messing up somebody else's files. Especially because self-made photo's are irreplaceable.

That's handy, otherwise you might have found your sister at the door... with a shotgun. ;)

---

