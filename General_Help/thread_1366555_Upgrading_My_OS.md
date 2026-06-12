---
title: "Upgrading My OS"
date: 2009-12-28
forum: General Help
---

### Post by Justin91 on 2009-12-28
I'm upgrading my OS from Ubuntu 7.1 to Ubuntu 9.10
--
My problem is that my system isn't/won't write the ubuntu 9.10 to the disc.
And when I thought it did finally write the disc,
i couldn't get my system to boot from the disc.  
So then i booted regularly and now it says there is nothing on the disc....

....I tried writing the disc as an image, and as a file.
Neither of them worked.
--Please help!

---

### Post by s.fox on 2009-12-28
Hi have you checked the MD5SUM?  [Here]("https://help.ubuntu.com/community/HowToMD5SUM") is some useful things to try on both the iso and the cd.

-Silver Fox

---

### Post by Justin91 on 2009-12-28
You mean MD5SUM?  lol
its ok.  lol i never even heard of it til now so...
let me do this then, and i'll post back.

---

### Post by s.fox on 2009-12-28
> **Justin91 said:**
> You mean MD5SUM?  lol

Haha,  sorry yes.  New laptop has slightly bigger keys than my old one.  Sorry for confusion :lolflag:

-Silver Fox

---

### Post by tom.swartz07 on 2009-12-28
> **Justin91 said:**
> I'm upgrading my OS from Ubuntu 7.1 to Ubuntu 9.10
--
My problem is that my system isn't/won't write the ubuntu 9.10 to the disc.
And when I thought it did finally write the disc,
i couldn't get my system to boot from the disc.  
So then i booted regularly and now it says there is nothing on the disc....

....I tried writing the disc as an image, and as a file.
Neither of them worked.
--Please help!

Cant you just do a ```
sudo apt-get dist-upgrade
```? That would update your system without having to wipe all of your data

---

### Post by Justin91 on 2009-12-28
...its not working...

---

### Post by s.fox on 2009-12-28
> **Justin91 said:**
> ...its not working...

What output is terminal giving you from that command?

-Silver Fox

---

### Post by Justin91 on 2009-12-28
its "bash"ing every command i try for the md5sum command.
example:

root@xxx:-# cd download_directory  [press enter]
[result of command is below]
bash: cd: download_directory: No such file or directory

---

### Post by ugm6hr on 2009-12-28
> **tom.swartz07 said:**
> Cant you just do a ```
sudo apt-get dist-upgrade
```? That would update your system without having to wipe all of your data

No you can't.

7.10 is no longer supported.

---

### Post by Justin91 on 2009-12-28
so what do i do then?

---

### Post by ugm6hr on 2009-12-28
> **Justin91 said:**
> so what do i do then?

Your original plan to download the iso, burn to CD (or write to USB), reboot and do a fresh install.

Not sure why your iso won't write properly.

Check md5sum, if OK, describe the exact procedure you're using to write the iso.

From memory, the default Brasero didn't work in 7.10; try GnomeBaker or K3b.

Have you changed your repositories to reflect the fact that they have been moved for 7.10?  If not, you'll have to google what the repository address is - it hasn't been discussed on the forum for a while.

Again, from memory, it's something like old-releases.ubuntu.something

Edit: Found it [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
[http://ubuntuforums.org/showthread.php?p=6787824#post6787824](http://ubuntuforums.org/showthread.php?p=6787824#post6787824)

---

### Post by Slim Odds on 2009-12-28
Just for future reference, you should make sure you upgrade to the new version before the old one expires. That will save you a ton of trouble. Also, you might want to stick to the LTS releases if you don't want to upgrade every 12-18 months.

---

### Post by Justin91 on 2009-12-28
well i tried to md5sum but my terminal wont recognize the command.

[COLOR=SeaGreen][This]("https://help.ubuntu.com/community/BurningIsoHowto")[/COLOR] is the procedure I used to do the iso thing.
But for some reason 4-5 work differently for me...  


From my other posts, here's a description of my iso problem...
> **Justin91 said:**
> [--]("https://help.ubuntu.com/community/BurningIsoHowto%5B/URL")[ _[COLOR=Blue]4 and 5[/COLOR]_ ]("https://help.ubuntu.com/community/BurningIsoHowto")[--]("https://help.ubuntu.com/community/BurningIsoHowto%5B/URL") Dont work for me?

It brings up a screen and asks me for the same things but i cant select a speed or anything.
All I can do is Help, Cancel, or Write.  
When I click write it burns too fast?  or it just doesnt burn?  idk, but it doesnt work right

The other way I tried instead of 1-3, I dragged the file from my desktop into the CD/DVD Creator, 
then the "Write to Disk" button became clickable.  ....no, its not a word but oh well lol.
So I do that and I get a different menu....
Brings up a "Write to Disk" menu, but it also instantly pops up a window in front saying:
>                               ----Create disc containing a single disc image file?----
-It appears that the disk, when created, will contain a
single disc image file.  Do you want to create a disk
from the contents of the image or the image file
inside?
-create from image-     ....  -cancel-   ...... -create with file-----------------------------------------------------------------------------------------
ok, so i wrote the disc as an image, and it did the same thing that it did before, 
it didnt work.
So then I wrote it as a File.  It seemed to work, it actually took the time to write it?

But then I tried to boot my system from the CD and it didnt work.
My system like, idk, didnt recognize the content on the disc?

And now its reacting as though nothing was written to the disc...?

So...  yeah...  i'm not sure...

---

### Post by Slim Odds on 2009-12-28
> **Justin91 said:**
> its "bash"ing every command i try for the md5sum command.
example:

root@xxx:-# cd download_directory  [press enter]
[result of command is below]
bash: cd: download_directory: No such file or directory

Where did you put the file that you downloaded?

You clearly do not have a directory called download_directory

Where is your ISO file?

---

### Post by ugm6hr on 2009-12-28
> **Justin91 said:**
> its "bash"ing every command i try for the md5sum command.
example:

root@xxx:-# cd download_directory  [press enter]
[result of command is below]
bash: cd: download_directory: No such file or directory

I think you have misunderstood this.

You need to substitute ***download_directory*** with the location of the iso file.

e.g.

```
cd ~/Desktop/
```

A useful tip: to find out how to use a command:
```
man md5sum
```

Also - I don't think those instructions for iso burning work on 7.10.  You're better off installing GnomeBaker.

---

