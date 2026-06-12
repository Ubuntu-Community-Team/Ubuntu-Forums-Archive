---
title: "Brasero used to rip CD/DVD's as ISO's."
date: 2012-06-08
forum: General Help
---

### Post by Stray Wolf on 2012-06-08
So, once upon a time I could use Brasero to make an image of a CD to be burnt later, or just mount it and play it like a CD from an ISO. Now, it saves as a .toc and .bin, which neither play like the ISO's would. I want to keep master copies of all my CD's and DVD's as ISO's. How do I do that now?

---

### Post by dino99 on 2012-06-08
it seems that only "k3b" can be trusted (unlike its a kde app)

---

### Post by Stray Wolf on 2012-06-08
> **dino99 said:**
> it seems that only "k3b" can be trusted (unlike its a kde app)
  Thanks, I'm off to give it a go! I'll be right back to let you know if I got it working.

Well, I have it installed. I can't find the option to create an image or save a CD/DVD as an ISO. Do you know how to navigate through this K3B to rip a disk to my HD as an ISO.

---

### Post by IWantFroyo on 2012-06-08
If you want a GTK alternative, xfburn works.
I'm pretty sure that it's GTK2, though.

---

### Post by Stray Wolf on 2012-06-08
> **IWantFroyo said:**
> If you want a GTK alternative, xfburn works.
I'm pretty sure that it's GTK2, though.
I'll try that too. I just have some CD's and a few DVD's. I made iso's of them a year ago using Brasero with no problem. But, forgot to back them up.

Well, like K3B it will let me burn an iso to a disk, but I haven't found where to rip a CD as an ISO onto my hard drive.

---

### Post by arubislander on 2012-06-08
In Brasero, if you click on the Properties button next to where you can select the filename of the disc image, at the bottom of the dialogue you can choose the Disc image type. It is set to Cdrdao image as default, but you can select ISO9660 image for a .iso file.

---

### Post by Stray Wolf on 2012-06-08
> **arubislander said:**
> In Brasero, if you click on the Properties button next to where you can select the filename of the disc image, at the bottom of the dialogue you can choose the Disc image type. It is set to Cdrdao image as default, but you can select ISO9660 image for a .iso file.

ISO9660 isn't an option. It has: Readcd/Readom image, Cue image, and Cdrdao. I did type ".iso" as the the extension in the file name. This is under 1:1 copy in Brasero. But it saved a filename.iso and filename.iso.bin. Which had two differences from when I previously ripped a disc as an ISO. One: it also made a filename.iso.bin and two: the .iso wasn't mountable and didn't play.

When did this .toc and .toc.bin stuff start happening. I know it may have been close to a year since I've tried to back up my CD's/DVD's as an ISO but I figured people would have made more noise when this capability was cut.

---

### Post by Cheesemill on 2012-06-08
I usually just use dd for creating images:
```
dd if=/dev/cdrom of=filename.iso
```

---

### Post by Stray Wolf on 2012-06-08
> **Cheesemill said:**
> I usually just use dd for creating images:
```
dd if=/dev/cdrom of=filename.iso
```

Well, that will copy an ISO to disk...but how do I go about saving a CD as an ISO on my HD?

---

### Post by Stray Wolf on 2012-06-08
AcetoneISO can supposedly rip it to a .toc then convert into an .iso. We'll see.

So, if I where to save CD's to be able to play on my system, but to also burn the CD to play in my car, what format should I copy the CD as? It seems a little silly to store a CD as flac files to play in a media player, and then save the same CD as toc.bin to burn but...is that what I'd have to do?

Last edit:
Problem solved. Doesn't matter what you rip a CD as so long as it's **not** an image. So, just use the music player of your choice and the format of your choice. Then in brasero, just select "Create Audio CD" and add the music files of your choice. It will convert while burning.

---

### Post by arubislander on 2012-06-15
You were trying to rip an **audio CD** to an ISO! This is indeed not possible with Brasero. Don't know that it's possible with any CD burning software.

All the suggestions given would work for data CD's / DVD's (movies counting as data too)

Maybe you could have specified that in the original post. And maybe we should have asked...

---

### Post by arubislander on 2012-06-15
> **Stray Wolf said:**
> ... or just *mount it and _play_ it* like a CD from an ISO. .. [SIZE="1"]Emphasis mine[/SIZE]

Turns out the OP *did* mention it was an audio CD. We just didn't pick up on it.

---

