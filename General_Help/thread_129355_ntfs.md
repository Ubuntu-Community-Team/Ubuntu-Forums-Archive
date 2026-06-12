---
title: "ntfs"
date: 2006-02-13
forum: General Help
---

### Post by HokeyFry on 2006-02-13
is there ANY way to edit files on an NTFS partition using linux? and if there isn't, is there a way to convert it to an FAT partition so I can edit it?

---

### Post by hegenious on 2006-02-13
you can't.
well yes there is captive-ntfs. check Jan Kratochvil's webpage.
I must stress though that this program is somewhat dodgy and that it is easy to destroy your ntfs filesystem with it.
so it matters if the data on the ntfs drive is important to you. If it is, don't use captive.
I played with it on my ubuntu box but just to learn about this program and I didn't care for the data on the ntfs partition. Nothing desastrous has happened yet but when I mount the ntfs partition with the options rw user,umask=0
and I start accessing the ntfs partition I create a memory leak.

As for your second question, I copied this from ntfs.com:

Q: How can one revert a disk with NTFS to FAT 32?

A: What you asked is actually installation the new Operating System over the existing one.

There is no standard procedure of doing this.

Just copy all your important files (My Documents, etc.) to another logical (or physical) drive. Then format partition in FAT32, or delete and re-create new partition and perform standard procedures of installation Operating System to the newly formatted drive. As long as you successfully installed OS, copy your files back to the drive.

---

### Post by RaptorRaider on 2006-02-13
Linux really needs good NTFS writing support.

FAT32 isn't an option for most dualbooters because FAT32 doesn't allow individual files to be larger than 4GB.
Thus today they must choose to either loose those 4GB files or remove the possibility to edit files. :neutral:

---

### Post by cono on 2006-02-13
But then is it true that captive is unreliable, since it uses the native windows ntfs driver?

Or is it pretty safe exactly because it uses this?

---

### Post by aysiu on 2006-02-13
[QUOTE=RaptorRaider]
FAT32 isn't an option for most dualbooters because FAT32 doesn't allow individual files to be larger than 4GB.
Thus today they must choose to either loose those 4GB files or remove the possibility to edit files. :neutral:[/QUOTE] **Most** dual booters? What about those of us who don't have DVD burners? Or those who just plain don't have files that large? I think the largest file I have is 13 MB.

---

### Post by hegenious on 2006-02-13
> But then is it true that captive is unreliable, since it uses the native windows ntfs driver?

Or is it pretty safe exactly because it uses this?

captive is unreliable. It wraps around the native ntfs driver in a similar way as ndiswrapper does. that is a workaround since the exact specification is a trade secret of Microsoft.

The only alternative is third party ntfs drivers that you have to pay big bucks for. (paragon) but even these are known to leave errors on an ntfs drive.

---

### Post by Magneto on 2006-02-13
Dual Booters who need large file support (greater than 4gb) and read/write access to a (non system) partition in Windows,  use ext2 and mount the drive using ext2fs in windows

---

### Post by Mr Frosti on 2006-02-13
[QUOTE=RaptorRaider]Linux really needs good NTFS writing support.[/QUOTE]

If Microsoft would disclose the specifications of how their NTFS driver worked, it would be an invaluable resource to the computing world. Data recovery, integration, interoperability and stability would all benefit as a result. As long as no one regulates Microsoft and no one is forcing them to open up these specifications, this type of issue will continue. 

NTFS writing support for Linux will probably move into early beta as WinFS rolls out, with the same issues all over again.

---

### Post by DarkED on 2006-02-13
[QUOTE=Mr Frosti]If Microsoft would disclose the specifications of how their NTFS driver worked, it would be an invaluable resource to the computing world. Data recovery, integration, interoperability and stability would all benefit as a result. As long as no one regulates Microsoft and no one is forcing them to open up these specifications, this type of issue will continue. 

NTFS writing support for Linux will probably move into early beta as WinFS rolls out, with the same issues all over again.[/QUOTE]

I agree, Microsoft keeps way too much to themselves. If they would give details on their filesystems, the world of computing would be a much better place. Vista is gonna use WinFS isn't it? What will people do then? The same they are doing now, they have to grin and bear it. My life would be so much easier if I could write to my NTFS partition, but instead, I have to think about whether I want to use something in Windows or not BEFORE I download it...

---

### Post by RaptorRaider on 2006-02-15
> As long as no one regulates Microsoft and no one is forcing them to open up these specifications, this type of issue will continue.
Though perhaps unlikely, let's hope the EU will force Microsoft to release the specifications of NTFS and more. :D 
> Vista is gonna use WinFS isn't it?
Probably not.
More info about that [here]("http://news.com.com/2100-1016_3-5212077.html?tag=nefd.lede").

---

### Post by cotcot on 2006-02-15
I agree with magneto. 

By doing too much effort to be able to deal with ntfs you meanwhile accept a proprietary sysem as a standard. It is better to defend an open source platform that can meet the demand for file sharing above 4 GB per file. The ext2 (see [www.fs-driver.com](www.fs-driver.com)) is an acceptable alternative for having shared files of more than 4 GB per file.

---

### Post by HokeyFry on 2006-02-15
i already use ext2fs when I am logged into windows. Since I am a poor 17 yr old SOB who can't afford his own computer, I am forced to use windows when the rest of the family is at home. I just thought that if you could use ext2fs to access a linux partition in windows, there might be a reliable free way to do this with ntfs in linux.

---

