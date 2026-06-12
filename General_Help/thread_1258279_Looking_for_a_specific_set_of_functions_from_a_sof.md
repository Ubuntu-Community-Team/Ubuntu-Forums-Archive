---
title: "Looking for a specific set of functions from a software..."
date: 2009-09-04
forum: General Help
---

### Post by Nugar on 2009-09-04
Hi all,

I hope this is the right forum to ask for this. I'm an Ubuntu user, photographer among other things and I'm looking for a certain set of functionalities from a software I used to use when in Windows.

While I've searched this forum, Google and the Linux alternative databases, this is the kind of things that can only be answered by the experience of the collective mind.

The thing is, it is an obscure Windows program that isn't even developed or sold anymore and it's called Archive Creator. 

But before telling me there are a lot of these kind of programs, let me tell you what it does:

[LIST]
[*]It backs up your photos to CD/DVD, DVD DL, etc.
[*]It backs it up as normal images, not encrypted, just the images files
[*]It spans the backup, so if your images are more than can fit on the media, it spreads them among several discs. But as it back up as normal images, it doesn't matter if one of the media gets lost, since the other will have complete images, readable by any computer and you would only miss the lost media.
[/LIST]
It does a couple of things more, like producing an html index with all the images on every media, but those are the most important things.

Is there any Linux program that can do this? It would make my life incredibly easier.

If there isn't, where can I post this so maybe someone gets interested and codes it?

Also is there any software that does this: [http://no-nonsense-software.com/supercat/](http://no-nonsense-software.com/supercat/)

Thanks in advance for your time and answers,

---

### Post by Paqman on 2009-09-04
You could just open up Brasero or K3B and burn a data disk, surely? You wouldn't get the nice html index file, but you'd get disks full of images.

---

### Post by Nugar on 2009-09-05
Yes, that is an option. But the good thing about this particular software is that it calculates itself how many images fit on each media and then ask for a new disk.

The point is making your life easier than doing it "by hand".

I'm talking about thousands of images here and the need to locate them fast and to back them up easily.

---

### Post by StuartN on 2009-09-05
I think both Bacula and Mondo Rescue can do an indexed backup to removeable media like floppy / CD / DVD.

Given the value in a photograph collection I would invest in an external hard drive and copy the complete collection exactly as is, using ext3 / ext4 if you only need Linux compatibility or FAT / NTFS if you want Linux and Windows compatibility. You could simply copy with Nautilus, backup with rsync (or Meld) or use something like Krusader to create and maintain the copy. I use this method and it has an additional advantage that I can see any additions, deletions and changes to the collection when I run a synchronization on the copy.

---

### Post by Nugar on 2009-09-05
Thanks Stuart, 

I'll start my investigation in that direction. How do I go and try to interest coders into doing something like this?

Cheers,

---

### Post by Efwis on 2009-09-05
I found a program that does exactly what you want it to. and it's in the repos.

```
sudo apt-get install albumshaper
```
from the program info file
> Photo album creator and photo manipulator
Album Shaper strives to be the most friendly, easy to use, open source
application for organizing, annotating, framing, enhancing, stylizing,
and sharing your digital photos. Album Shaper embraces open formats like XML,
JPEG, and XSLT, while supporting Windows, Mac OS X, and Unix users who speak
a multitude of languages around the world!

Two-layer albums can be created in a drag-n-drop interface which allows
quick and easy arrangement and categorization of photos.

A few simple image manipulations such as rotation and flipping are provided
to help you get your photos presentable as quick as possible.

Photos, collections, and albums themselves can be labeled as needed and
modified at a later time by saving and loading from a simple XML format.
Albums are exported as HTML which can then be posted directly on the web
or viewed straight from your hard drive.

Album Shaper supports themes which means you can completely customize the
look of the Albums you produce. Album Shaper is designed to help you share
your photos with your friends and family as easily as possible, as well as
update and maintain these Albums in the most efficient and easy way possible.

good luck

---

### Post by Nugar on 2009-09-05
Almost there!

Sadly, it doesn't support PSDs or even TIFFs, which I frequently use as Masterfiles, since they can provide multi-page saving of files, with layers, adjustments, etc.

---

