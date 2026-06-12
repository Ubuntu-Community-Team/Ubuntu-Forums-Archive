---
title: "Picasa doesn't read ini files copied from XP?"
date: 2010-09-09
forum: General Help
---

### Post by 2CV67 on 2010-09-09
I have about 20 000 photos in XP which have mostly been tagged, cropped, etc using Picasa.
That Picasa is working OK.

I am shifting my activities from XP to Ubuntu & am just getting to the Photo part.

In Ubuntu, I have the current Picasa (3.0.5744-02) & that is working OK with any new photos I download to Ubuntu & modify in Picasa there.

So far - so good.

My next step was to copy a folder of photos from XP to Ubuntu & look at them in Picasa.
They copy perfectly & Picasa finds them OK.
All the tags are there OK.

But the cropping & other editing from Picasa XP is not seen in Picasa Ubuntu.

The ini file is there & looks the same as ini files generated in Ubuntu.

Should I expect my XP edits to be visible in Ubuntu?

How can I get that to work, without re-editing 20 000 photos?

Thanks for any advice!

---

### Post by 2CV67 on 2010-09-13
I found my problem was due to different names for the ini files.

Most of these files are called "Picasa.ini" but from 12 May 2009, when I upgraded to Picasa 3.1.0 in XP, then the files, looked at from Nautilus, are called ".picasa.ini".

I needed to rename all the .picasa.ini files to Picasa.ini then use Folder Manager to Remove & then Scan these folders.

Now they are all OK.

But I could have done without that!

---

