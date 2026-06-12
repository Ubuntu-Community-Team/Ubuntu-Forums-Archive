---
title: "Using Tellico - derived value as a filename path?"
date: 2011-09-11
forum: General Help
---

### Post by LackadaisicalLove on 2011-09-11
Right, me and my boyfriend recently decided to create a database to keep track of our Yu-Gi-Oh! card collection.

First I tried using LibreOffice Base, but that seems very buggy and it wouldn't let me add a new record. It also kept freezing.

I settled on using LibreOffice Calc to make a spreadsheet and gave up on the database idea, and this worked well, but I kept it on memory stick for easy switching between the PC and my laptop and it got corrupted. Should've made backups...

Then I saw Tellico in the Ubuntu Software Centre. It seems to work a charm, really happy with it. I was especially interested in the ease of adding an image via a derived path.

My boyfriend has scratched up something in bash that when you input the ID of a particular card, it will grab the image of that card from the Yu-Gi-Oh! Wikia and save it as its ID. To my understanding, I should be then able to use a derived path for an image field on Tellico to point it to the correct image.
I got this working a few days ago on a test image, but now I can't remember the syntax I need to use. It's really puzzling me!
I have tried the syntax of %{fieldname}, but this does not seem to work.

Value Template:
/home/dannie/Pictures/YGO/%{Card ID}

No luck at all with it. Any ideas?

---

### Post by gmargo on 2011-09-11
> **LackadaisicalLove said:**
> 
Value Template:
/home/dannie/Pictures/YGO/%{Card ID}


Do you need a file type suffix, like ".jpg" or ".png", appended to your template?

---

### Post by LackadaisicalLove on 2011-09-11
Yeah, I've tried it. The script saves them without a suffix, so I've tried changing the filename to have the suffix .jpg and gave it a go both with and without changing the derived value template to end in .jpg.

None of these combinations work. I'm honestly baffled.

---

### Post by gmargo on 2011-09-11
Does the field name "Card ID" really have a space in it?  Filenames and spaces don't mix well on Linux, so could be a problem.

Alternatively, at this point I would probably run tellico under **strace** to capture the actual filename that tellico is trying to open.

---

### Post by LackadaisicalLove on 2011-09-11
Yeah I thought it might be the space too, but I edited the field name to just "id" in lowercase and changed the template to match, but this didn't solve it either.

Hm, I just had a quick look at strace on the Ubuntu wiki, but what exactly would I be looking for after running Tellico using this?

---

### Post by gmargo on 2011-09-11
**strace** will show the system calls and results.  So you would see **open(2)** calls for each file opened etc.

I have done this.  I created a one-card collection and tried to duplicate your result, or lack thereof.

What I have found is that tellico searches the directory I gave it, finds the image, and then later searches in all the wrong places for the image.  It presumably then decides it doesn't know where the image is, since it doesn't get displayed.

Here's some of the output from strace, just showing file accesses:
```

$ grep fake_card_images out
14524 access("/home/gmargo/fake_card_images/001.jpg", R_OK) = 0
14524 open("/home/gmargo/fake_card_images/001.jpg", O_RDONLY|O_CLOEXEC) = 13
14524 open("/home/gmargo/fake_card_images/001.jpg", O_RDONLY|O_CLOEXEC) = 13
14524 stat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x2374418) = -1 ENOENT (No such file or directory)
14524 lstat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x7fff11502f10) = -1 ENOENT (No such file or directory)
14524 stat("/home/gmargo/.kde/share/apps/tellico/data//home/gmargo/fake_card_images/001.jpg", 0x2374028) = -1 ENOENT (No such file or directory)
14524 lstat("/home/gmargo/.kde/share/apps/tellico/data//home/gmargo/fake_card_images/001.jpg", 0x7fff11502f10) = -1 ENOENT (No such file or directory)
14524 stat("/home/gmargo/doc/CardTest1_files//home/gmargo/fake_card_images/001.jpg", 0x2374028) = -1 ENOENT (No such file or directory)
14524 lstat("/home/gmargo/doc/CardTest1_files//home/gmargo/fake_card_images/001.jpg", 0x7fff11502f10) = -1 ENOENT (No such file or directory)
14524 stat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x23770d8) = -1 ENOENT (No such file or directory)
14524 lstat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x7fff11503860) = -1 ENOENT (No such file or directory)
14524 stat("/home/gmargo/.kde/share/apps/tellico/data//home/gmargo/fake_card_images/001.jpg", 0x23770d8) = -1 ENOENT (No such file or directory)
14524 lstat("/home/gmargo/.kde/share/apps/tellico/data//home/gmargo/fake_card_images/001.jpg", 0x7fff11503860) = -1 ENOENT (No such file or directory)
14524 stat("/home/gmargo/doc/CardTest1_files//home/gmargo/fake_card_images/001.jpg", 0x23770d8) = -1 ENOENT (No such file or directory)
14524 lstat("/home/gmargo/doc/CardTest1_files//home/gmargo/fake_card_images/001.jpg", 0x7fff11503860) = -1 ENOENT (No such file or directory)
14524 stat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x23770d8) = -1 ENOENT (No such file or directory)
14524 lstat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x7fff115039c0) = -1 ENOENT (No such file or directory)
14524 stat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x23770d8) = -1 ENOENT (No such file or directory)
14524 lstat("/tmp/kde-gmargo/tellicoEUNaP4//home/gmargo/fake_card_images/001.jpg", 0x7fff11503890) = -1 ENOENT (No such file or directory)
14524 stat("/home/gmargo/.kde/share/apps/tellico/data//home/gmargo/fake_card_images/001.jpg", 0x23770d8) = -1 ENOENT (No such file or directory)
14524 lstat("/home/gmargo/.kde/share/apps/tellico/data//home/gmargo/fake_card_images/001.jpg", 0x7fff11503890) = -1 ENOENT (No such file or directory)
14524 stat("/home/gmargo/doc/CardTest1_files//home/gmargo/fake_card_images/001.jpg", 0x23770d8) = -1 ENOENT (No such file or directory)
14524 lstat("/home/gmargo/doc/CardTest1_files//home/gmargo/fake_card_images/001.jpg", 0x7fff11503890) = -1 ENOENT (No such file or directory)

```But since I see that it looks in a directory relative to my "CardTest1.tc" file, then using a relative pathname, instead of absolute, might work.


Later.... I tried a relative directory, but still the image won't display....

---

### Post by LackadaisicalLove on 2011-09-11
Ah! Thankyou for trying it, I couldn't find where I was supposed to be looking.

Hmm, I think what is the most frustrating thing is that I got it working a few days ago, and I can't seem to replicate those results now.

---

### Post by parys on 2011-09-12
Try using the *file:///path/to/image/%{Cover ID}* syntax as the template, with *file:///* being the important part. That's how Tellico knows it's a location.

If "Cover ID" is the field title, then that should work in the template string, I'm not sure why it didn't. I just tested with the file:/// and it seems to work for images, I'd never thought about using a derived value for the image location. :)

---

### Post by LackadaisicalLove on 2011-09-12
Success!
Typed in the card ID and immediately got a nice little image of Jutte Fighter after saving the record.

Thankyou!

---

