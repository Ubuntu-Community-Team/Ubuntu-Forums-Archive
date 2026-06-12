---
title: "What Filesystem should I install in a SSD ?"
date: 2009-10-09
forum: General Help
---

### Post by pmalvr on 2009-10-09
Hi,

I would like to know what's the appropriate filesystem for an ssd and why?  

Thanks in advance

---

### Post by zvacet on 2009-10-09
Ubuntu by default use ext3 but I think starting with Karmic will be ext4.

---

### Post by t0p on 2009-10-09
An SSD has a limited lifespan, as each location can be written to only a certain number of times.  Therefore, it is (at least in theory) better to use a non-journalling filesystem, as it will write to the disk less.  For this reason, I use ext2 on my EeePC.

Unsurprisingly, SSD endurance is improving.  And it's already reached the stage where it's comparable to that of magnetic media.  The report quoted in the Guardian newspaper [here]("http://www.guardian.co.uk/technology/blog/2008/jan/16/sohowlongmighttheflashdr") states  that it would probably break down because of other mechanical reasons before it "wore out" dues to rewrites (one projected lifespan of a specific SSD is 12.9 years.  Another is 51 years!).  Therefore, Ubuntu's default ext3, or the newer ext4 may be fine for SSDs.  Next time I reinstall to my EeePC, I intend to use ext3.

---

### Post by amitabhishek on 2009-10-09
> **t0p said:**
> An SSD has a limited lifespan, as each location can be written to only a certain number of times.

I didn't knew that!!!:confused:

---

### Post by Lars Noodén on 2009-10-09
Look at the mount options.  To increase speed, you can turn off atime, for example.  Whether you turn off journalling is up to you, but journalling helps recover from unexpected power outage (battery runs down, cable tripped over etc)

Here is a comparison of some specific characteristics:

[http://ldn.linuxfoundation.org/blog-entry/ssd%E2%80%99s-journaling-and-noatimerelatime](http://ldn.linuxfoundation.org/blog-entry/ssd%E2%80%99s-journaling-and-noatimerelatime)

---

### Post by Mighty_Joe on 2009-10-09
> **amitabhishek said:**
> I didn't knew that!!!:confused:

Don't sweat it.  As t0p points out, an SSD's life span will more than likely [outlast the hardware]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html") it is installed in.  
[Smarter people than I]("http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/") have considered the question and determined that the extra safety with ext3 is worth the wear.  Personally, I installed Ubuntu on a flash drive using ext3 and followed [this advice]("http://en.opensuse.org/Speeding_up_Ext3") to maximize performance.  It's more stable than ext2 (which would get "unclean unmount" errors every boot) and it *feels *faster (I did not benchmark to test this claim).

---

### Post by HermanAB on 2009-10-09
You can use any file system you want.  The limited lifespan argument is an Old Wives Tale nowadays and the wear leveling is done in hardware so you need not worry about it.

However, since a SSD is expensive, I prefer to use a file system with greater storage efficiency than ext3, for example IBM JFS. One can easily store 25% more data on JFS than on Ext3 on the same media.

---

### Post by Elfo33 on 2009-10-09
Ubuntu NBR talks about transferring the .img file onto a FAT32 formatted drive.  So, I guess I would go with that until they change that recommendation.

---

### Post by Mighty_Joe on 2009-10-09
> **HermanAB said:**
> One can easily store 25% more data on JFS than on Ext3 on the same media.

That's impressive, and I'm wondering if ext3 uses huge metadata or what so I hopped over to Wiki and see JFS uses compression and:
> Because of high CPU usage and increased free space fragmentation, compression is not recommended for use other than on a single user workstation or off-line backup areas
[Wikipedia: JFS]("http://en.wikipedia.org/wiki/JFS_%28file_system%29#Compression")

Doesn't sound like a good tradeoff for some extra storage, at least for a personal computer.

[QUOTE=Elfo33]Ubuntu NBR talks about transferring the .img file onto a FAT32 formatted drive. So, I guess I would go with that until they change that recommendation.[/QUOTE]
That's just to run the installer as a "live cd".  you still have to format and install UNR on a disk/SSD

---

### Post by Elfo33 on 2009-10-09
I understand that, I was just suggesting that if the Ubuntu team is targeting FAT32 for SSDs, maybe we should as well :)

---

### Post by Mighty_Joe on 2009-10-09
> **Elfo33 said:**
> I understand that, I was just suggesting that if the Ubuntu team is targeting FAT32 for SSDs, maybe we should as well :)

But they're not.  Live USB installs, like those created with the [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") or the image the UNR is distributed in have to be put on a FAT32 file system.  If you are going to install Ubuntu, you *cannot *install it to FAT32.

---

