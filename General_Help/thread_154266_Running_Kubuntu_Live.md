---
title: "Running Kubuntu Live"
date: 2006-04-02
forum: General Help
---

### Post by NeoGreen on 2006-04-02
I just downloaded Kubuntu Live on to my computer and burned it on to a CD.  Here is my problem when I go to run it, it won't run.  I really don't know if i am burning the CD correctly can someone give me some tips on how to burn an .iso to a cd or what programs to use. When I burned mine on to the cd, all I did was download it to my documents, then copied the files to the cd.  Some please help:(

---

### Post by gingermark on 2006-04-02
Yeah, you need to find the "burn image" option in whatever cd burning program you use. An iso file is a cd image, think of it like a zip file. Burning the cd image is like burning the contents of the zip file (as opposed to just burning the file itself, which is what I think you've done).

If you just "copied the files to the CD" then I'm guessing you're currently running Windows, and are using Explorer's (is that what its called?) burning options. If so, I'm not sure if you have the burn image option. It's been a while since I used Windows, and to be honest I can't remember.

Anyways if that is the case, I seem to remember that [CDBurnerXP Pro](http://www.cdburnerxp.se) burns ISOs, and that's a free program you could download and use.

If you can provide more information on your OS, and the burning software you are using, then hopefully we can help you further on that one if I guessed wrong.

Also, when you come to boot the CD, you may well need to change the boot order in your BIOS so that your optical drive boots first.

Good luck!

---

### Post by NeoGreen on 2006-04-02
Yeah, I was running it under explorer to burn the disc.  I was actually burning the disk without even unzipping it.  I downloaded CD Burner XP Pro, and I am about to burn it on a disk.   I don't know if it will work, but I will give it a try.:)

---

### Post by gingermark on 2006-04-02
[QUOTE=NeoGreen]I was actually burning the disk without even unzipping it[/QUOTE]

Forgive the zip file analogy! Just to stress, you select the "Burn CD image" (or similar) option, select the iso file, and away you go (I can't remember the exact process).

But don't try to extract the iso yourself!

Hopefully you got what I meant, but I thought I'd post just in case :)

---

### Post by NeoGreen on 2006-04-02
Okay, I tried it and it didn't work.  After I burned the CD a got a message that the files were corrupt.  Did I do something wrong?  Another thing, I was reading up on how to burn an ISO on CDBurnerXP Pro and it told me that all I had to do is choose the file you want to burn add it to the files to be burned box and press the burn cd button.  Well, I tried that and it seem that it isn't working,  because when I ran the first time it asked me all sort of questions, like if the cd needs to be made bootable, and to finalize it after it has been burned.

---

### Post by gingermark on 2006-04-02
To be honest, I'm afraid I'm not going to be much help here. I don't run Windows, and haven't used it regularly for a long time.

Hopefully [this page](https://wiki.ubuntu.com/BurningIsoHowto) will help. Good luck!

---

### Post by NeoGreen on 2006-04-02
I got it!!!!!!!!  Thanks for the help:)

---

### Post by NeoGreen on 2006-04-02
Quick question, should I finalize the cd after I am done burning it?:-k

---

### Post by gingermark on 2006-04-03
[QUOTE=NeoGreen]Quick question, should I finalize the cd after I am done burning it?:-k[/QUOTE]
I would. I'm not 100% sure it matters, but you won't be writing anything else on the CD when you're done, so it seems like a reasonable idea.

---

### Post by NeoGreen on 2006-04-03
Okay, thanks:)

---

### Post by Al3xanR0 on 2006-04-03
[QUOTE=NeoGreen]Quick question, should I finalize the cd after I am done burning it?:-k[/QUOTE]

If you don't intend on writing to it then finalize; in the case of burning an iso image like Kubuntu live to a cd I would recommend that you finalize it. If you use Nero to burn cds, as soon as you cross the 700MB threshold even if it is as miniscule as 1kB over it will force you to finalize. Conversely, if you wish to write further to disk then do not finalize it, but be sure to establish the cd as a multisession cd first.

---

