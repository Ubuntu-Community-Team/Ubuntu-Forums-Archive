---
title: "Ramdisk question"
date: 2009-11-09
forum: General Help
---

### Post by sc30317 on 2009-11-09
Hey all,

I just built a new computer with 4GB of ram->  I would like to take advantage of them.

I was wondering if there was a way that I could create a ramdisk within my system, and run my operating system from RAM instead of from the hard drive.

Any help would be appreciated.

sc30317

---

### Post by jerrrys on 2009-11-10
this any help?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ramdisk&as_qdr=all&sa=Google+Search&lang=en#1029](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ramdisk&as_qdr=all&sa=Google+Search&lang=en#1029)

---

### Post by JBAlaska on 2009-11-10
I know you can load the entire LiveCD of Debian or Knoppix in ram (with the "toram" boot option) and then mount your physical HD's, But I seem to remember this was somewhat buggy in Jaunty. I'm not sure if this was fixed in Karmic, but I would be interested in knowing as well.

Hopefully someone would be kind enough to update us on this??

---

### Post by sc30317 on 2009-11-10
jerrys- that didn't help.  If you don't have the answer, don't post smart-alec answers.

Anyone else?

---

### Post by jerrrys on 2009-11-10
> **sc30317 said:**
> jerrys- that didn't help.  If you don't have the answer, don't post smart-alec answers.

Anyone else?

nothing smart-alec about it, may just not what you wanted to hear.  lighten up dude

---

### Post by sc30317 on 2009-11-10
w/e.  Anyone else?

---

### Post by sc30317 on 2009-11-11
no one?

---

### Post by jerrrys on 2009-11-11
[http://ubuntuforums.org/showthread.php?t=1238693](http://ubuntuforums.org/showthread.php?t=1238693)

and if you tell me me im being smart-alec again, your off my Christmas list...

---

### Post by jbrown96 on 2009-11-11
It's not an easy thing to do. There are two ways to do this. 1) Use UnionFs. There are a lot of considerations here. You need to do some serious reading about it. 2) Alter your folder structure, create tmpfs at the regular location, and somehow copy all that data when boot first starts.

They are both very tricky. I doubt there's anyone on here that can be of much help to you. We won't be able to walk you through doing this. The scripts that are needed to copy the information are complicated, and need to be executed at very specific times. Boot and shut down times will be significantly longer. Furthermore, there are very real risks of data loss since so much is being held in ram. 

Your best bet is to use something like preload. It does this automatically with your most often used programs/libraries/files. ```
sudo apt-get install preload
```

I spent several hours working on this, and I decided that it just wasn't worthwhile. The speedup is insane, but the work to get there isn't worth it. Ubuntu will take advantage of that ram, and even better with preload install. The thing is that it takes preload a week or so to really figure out your system, so don't get upset when it isn't running faster right away.

---

### Post by jerrrys on 2009-11-11
jbrown96

bravo

---

### Post by jbrown96 on 2009-11-12
I've been thinking about it some more. Perhaps, I made it seem impossibly hard. That's not true, but it will take some work. There isn't a good guide for doing it. There is a how-to about putting your Firefox profile in ram. Apparently, it let's firefox start extremely fast. It's a long guide though. It's a great starting resource on how to do tmpfs. 

You should read this resource first [http://www.linux-mag.com/cache/7388/1.html]("http://www.linux-mag.com/cache/7388/1.html") to understand tmpfs. It might be good to read a couple more resources on just understanding file systems in linux. 

You can go down that road. If you got it working properly, there wouldn't be another computer experience like it. Everything would literally be instant. It would just take some work.

Preload is really good software, but it's really frustrating. I've used it before, but I just set up a new system a couple weeks ago. I got the feeling that everything was just taking too long. I tend to close and restart Firefox a lot because I don't have a lot of tabs open. It annoyed me so much that every time I would reopen it the disk would spin up. It was faster than starting it the first time, but still too slow. I installed preload, and nothing happened. I couldn't believe that nothing really seemed to change. It's frustrating at first, but it takes preload a while to learn which files to load. And when you finally sort of forget about installing it (like the 3rd day), it's so nice because everything just runs so much smoother. My disk doesn't spin up at all when reopening Firefox.

---

### Post by bobpaul on 2010-02-21
> **JBAlaska said:**
> I know you can load the entire LiveCD of Debian or Knoppix in ram (with the "toram" boot option) and then mount your physical HD's, But I seem to remember this was somewhat buggy in Jaunty. I'm not sure if this was fixed in Karmic, but I would be interested in knowing as well.

Hopefully someone would be kind enough to update us on this??

I think there might have been a "toram" option back in Breezy, but there hasn't been one in anything later (Breezy might not have even had it). Certainly Jaunty and Karmic do not have it, so it can't be considered "somewhat buggy"... it doesn't exist!

There's a page on the [Ubuntu Wiki]("https://wiki.ubuntu.com/BootToRAM") that describes remastering the LiveCD for this purpose. I really hope this gets added in to future LiveCDs, as it really streamlines doing work on multiple computers at once (ie, 1 CD can boot up 30 computers, which can then be imaged or have ubuntu installed from the packages on the ramdrive). Obviously it doesn't work on computers without enough ram to hold the squashfs image.

---

### Post by bobpaul on 2010-02-21
> **sc30317 said:**
> Hey all,

I just built a new computer with 4GB of ram->  I would like to take advantage of them.

I was wondering if there was a way that I could create a ramdisk within my system, and run my operating system from RAM instead of from the hard drive.

Any help would be appreciated.

sc30317


If you want a ramdisk, the [instructions are here]("http://ubuntuforums.org/showthread.php?t=707230"). The precaching suggestion might provide enough of a boost to make this unnecessary, though.

---

