---
title: "Easiest way to share documents between OS"
date: 2009-08-08
forum: General Help
---

### Post by Joey-DK on 2009-08-08
Hello all!

I've slowly gotten tired of learning everything the hard way, so I decided to ask you guys and follow your advice!

I've a MSI Wind and is about to install the Ubuntu Remix. I used Ubuntu before (a long time ago) and know my way around it. But I want to dualboot WinXp and Ubuntu (netbook remix) which leads me to my problem.

I would like to have Ubuntu and WinXp share documents, so that when I click "Documents" in Start in Windows, I get to the same folder as the one I would go to if I clicked "documents" in Ubuntu.

What is the best way around this? I would hate to have 2 different document folders.

Hope any of you can help me a bit! :)

---

### Post by There Was A Time on 2009-08-08
> **Joey-DK said:**
> Hello all!

I've slowly gotten tired of learning everything the hard way, so I decided to ask you guys and follow your advice!

I've a MSI Wind and is about to install the Ubuntu Remix. I used Ubuntu before (a long time ago) and know my way around it. But I want to dualboot WinXp and Ubuntu (netbook remix) which leads me to my problem.

I would like to have Ubuntu and WinXp share documents, so that when I click "Documents" in Start in Windows, I get to the same folder as the one I would go to if I clicked "documents" in Ubuntu.

What is the best way around this? I would hate to have 2 different document folders.

Hope any of you can help me a bit! :)
I had Links (right click > Make Link) set up, pointing to the mount locations for each folder and that worked fine. Although be careful, as during Windows' boot, dskchk has a habit of deleting files created by Ubuntu, for no apparent reason. Any ideas why this is happening?

---

### Post by credobyte on 2009-08-08
How about creating a new FAT32 or NTFS partition, let's say, 1-2Gb in size ? You could use it in both OS's ( some kind of sharing ) :)

---

### Post by Joey-DK on 2009-08-13
but Ubuntu requires a drive for it's documents?

It couldnt just use my Windows documents on D:?

---

### Post by lisati on 2009-08-13
> **Joey-DK said:**
> but Ubuntu requires a drive for it's documents?

It couldnt just use my Windows documents on D:?

You can access your Windows drive with Ubuntu through Ubuntu's "places" menu item, but Ubuntu will have a name for it different to "D:". Depending on how it's set up you might have to navigate through a few folders, and/or install a tool such as NTFS-3G.

---

### Post by nikhilk on 2009-08-13
> **Joey-DK said:**
> but Ubuntu requires a drive for it's documents?

It couldnt just use my Windows documents on D:?

You can easily share a NTFS/FAT32 formatted partition (hence, any folder on that partition) between Windows and Ubuntu. You might just have to use a different name in Ubuntu for the Windows's document folder. That is only a minor inconvenience, don't you think?
All files created/updated from Ubuntu in that folder will be visible to Windows and vice-versa which is your ultimate objective right?

---

### Post by Joey-DK on 2009-08-13
Well, yeah.

But I had hoped for a solution without creating too many new partitions? :)

Not possible?

What is NTFS-3G?

---

### Post by P4man on 2009-08-13
ntfs-3G is the driver that lets ubuntu read/write windows ntfs volumes.

The other way around is also possible btw, you can install an Ext3 driver for windows so you can read ubuntu drives:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Though Id be very careful using it to write to an Ex3 partition.

I dont think it supports Ext4 yet, so if you install ubuntu, stay on Ext3 if you want to go that route.

---

### Post by nikhilk on 2009-08-13
> **Joey-DK said:**
> Well, yeah.

But I had hoped for a solution without creating too many new partitions? :)

Not possible?
Possible, you won't have to create any new partitions. Just mount the windows partition corresponding to drive D: in Ubuntu and you are all set.

> **Joey-DK said:**
> What is NTFS-3G?
It is a FUSE module which enables the read-write support for NTFS formatted partitions. Take a look at [this]("https://wiki.ubuntu.com/ntfs-3g").

---

### Post by Joey-DK on 2009-08-15
Thanks for being so slow with me ;)

But it's not possible to make Ubuntu go to my documents on D: when I click on the "home" and "pictures" link (I think they are called that, eh?)?

Because then I'll probably make a new partition to use as my documents!

---

### Post by P4man on 2009-08-15
You could do that for pictures and documents and video's. Not for your home folder as such (both windows and linux write a lot of stuff in there and you don't want to mix that).

But you can make your own "shortcuts" in ubuntu so that when you open places > pictures or places > documents it opens some folder that is shared between windows and ubuntu.Can even be the windows "my pictures" folder on the windows drive. Or on a separate shared partition, why not. In windows you can change those locations too.

---

### Post by Joey-DK on 2009-08-17
Ah.. so.. I would.. fake the document links, but still need a partition for some linux "home" files?

---

### Post by P4man on 2009-08-17
Doesnt have to be a partition. You can just do a regular install, which will create an ubuntu partition and a homefolder in it. Then you change the nautilus "shortcuts" to documents, pictures, movies from the subfolders inside the home folder (which you then remove), to somewhere else. like your windows userdata folder.

Creating a seperate partition for home is often recommended (makes it easier to do a clean install of ubuntu or any other linux without losing your stuff), but really not needed here.

---

### Post by Joey-DK on 2009-08-17
Sounds just great guys!

Thank you very much for your help!

---

### Post by Strongman332 on 2009-08-17
just create links pointing to those destinations.

---

