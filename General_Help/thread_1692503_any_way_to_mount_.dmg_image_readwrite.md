---
title: "any way to mount .dmg *image* read/write??"
date: 2011-02-21
forum: General Help
---

### Post by youWho on 2011-02-21
Howdy,

I've been trying everything I can think of/find searching the internet. I'm using ubuntu lucid (64 bit). I have a .dmg file that I managed to burn onto a CD just before my old iBook died (I now have no Mac access). I'm trying to mount that so I can access it under ubuntu. The problem I'm having is that though I can get it to mount with:

sudo mount -t hfsplus -o loop '/home/<me>/Desktop/those_documents.dmg' /mnt/dmg

it mounts "read only", so I can't chown anything on it to my username, which I would like to do because the UIDs in Mac use a different range of numbers than in Ubuntu, so everything on the "disk" is owned by some user that's definitely not "me".

I know that hfsplus disks can only be mounted read/write if journaling is turned off on them, but does that have any relevance in the case of disk images?

I thought I could just copy the contents to a directory, but I guess it'd be better to be able to mount it and then work with the files directly there, converting them each according to type and such (some have resource forks for example) because when I tried cp -R -t /new_directory /directories/on/the/dmg I got a *lot* of "IO" error messages, things like:

cp: reading `/mnt/dmg/TEMPORARY--TO_BE_SORTED/spirit voices from Guy': Input/output error

and though some things did seem to copy there are so many items in all that it'd be a hella hard task trying to figure out which had copied properly and which hadn't.

Any expert advice??? *Thanks*

[Edit:] indeed it's worse than I thought: even trying to open text files that are "on" that "disk" I get IO errors and no text (in gvim).

PS to forum administrators: I didn't know whether this was the proper place to post this or not; please move it if you think it was in the wrong place (sorry).

---

### Post by andrewc6l on 2011-02-22
You can avoid permssion problems with:

```
sudo sh
```

This will give you a root shell, which has permissions to do pretty much everything (including breaking your Ubuntu install, if you tell it to - so be careful!)

After that, getting Mac files is still tricky because of the [resource fork]("http://en.wikipedia.org/wiki/Resource_fork").

Here's a link that will give you some ideas of reading from Mac filesystems: [andrewmemory.wordpress.com/2010/08/06/reading-fonts-from-a-mac-cdrom-and-converting-them-to-truetype]("http://andrewmemory.wordpress.com/2010/08/06/reading-fonts-from-a-mac-cdrom-and-converting-them-to-truetype/")

---

### Post by WorMzy on 2011-02-22
Take a look at this:

[http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/hfsplus.txt)

The options listed here can be included in an fstab entry, or in a mount command. e.g.

sudo mount -t hfsplus -o loop_,gid=1000,uid=1000,umask=022_ '/home/<me>/Desktop/those_documents.dmg' /mnt/dmg

> You can avoid permssion problems with:

```
sudo sh
```


While this is acceptable, I would avoid it. Use the inbuilt function in sudo for a root shell if you really need one: 
```
sudo -i
```

---

### Post by youWho on 2011-02-23
Thanks for your comments andrewc6l and WorMzy. I installed hfsutils-tcltk, and I guess I need to investigate that further but it seems to be specifically for HFS, not HFS+. I wonder if that matters. Hmm.

Your tip WorMzy of using the uid, gid and umask option specifiers is something I'm going to try next. That looks promising indeed.

But I should say that the problem seems more obscure (to me) than I had at first thought: it looks like even files I had thought were copying were in fact not readable---basically when trying to access any of the files I get IO errors.

I have bought an enclosure for 2.5" drives and I'm planning on taking the drive out of the iBook; probably if I can access those files on the actual disk, instead of the .dmg file, it would be better. I'll let you know how that goes (this might take up to a couple of weeks because of work-time pressure, but I definitely want to do it, and I'll report back here what I learn, in case it helps anybody else).

And to andrewc6l: indeed the resource fork is the reason I'm trying so hard to get at the actual files directly. For example I have some SD2 audio files, and those used resource forks to save playlists and regions and such back in the days. I believe that libsndfile can convert those to more modern audio file formats, though I suppose with a lot of that information missing. Anyway even to use sndfile-convert (which I haven't tried yet) I suppose it'd be best to input the original file---a unix copied copy would in any case be without resource fork.

In the end it's  likely that I'll just admit that I'll never need to keep for posterity (??!) the resource forks of those files, but I haven't reached that stage yet. I'll try a few more times to "properly" convert them.

Thanks again.

-Sam

---

### Post by youWho on 2011-05-24
In case anybody is having similar difficulties I'll post a bit of an update:

I tried a *lot* of things, and unfortunately there were so many that didn't work that I've now totally lost track of exactly what I did do, but the upshot is that I did in fact manage to get at the .dmg file, accessing it as though it were a "disk" using other apps, including (I know I tried at least these, and sorry but I now don't remember exactly what worked for what step... long story) dmgextractor, hfsexplorer, peazip.  In the end I was able to get at the files. I did also buy an enclosure---actually 2 but the first didn't work; beware of enclosures from König---and with my HFS+ drive in that I was able to access the files. BUT never was I able to even copy the files from that drive to another HFS+ drive; I still haven't tried to convert the SD2 audio files to another format. But the main issue I kept stumbling over was that unix apps and utilities (including command line apps obviously)  are not designed to acknowledge the existence of the resource fork. I think at this point I'm either going to yield to the idea that I'll never have a need for those forks anyway, except that as I do try to sort through all those old files if I come across one that's especially important to keep I'll try to convert it somehow, if possible.

Not much useful info here in this post, sorry.The main thing I wanted to say was just that if you are trying to access files on an HFS+ formatted drive beware that just mounting the volume is not enough; if you need those resource forks somehow then it's not necessarily so easy to preserve them, and you might not actually know that as you even just copy, move, etc the files.

Very nice Java apps for accessing HFS+ files are dmgextractor and hfsexplorer, found at:
[http://www.catacombae.org/](http://www.catacombae.org/)

---

