---
title: "Here I sit lonely hearted I paid ten cents and can't gparted."
date: 2009-09-12
forum: General Help
---

### Post by nix-idioteque on 2009-09-12
hey there, I'm currently on a new Ubuntu install, dual booted with Vista and would like that to change.   I've come to the decision that Vista is no longer the operating system for me, I do however know I can't get rid of it.  So, I sudo apt-get install gparted - good -  starts up - great!  Now to resize my ntfs partition by half freeing up space... 

There's my problem...

A little triangle with an exclamation point.  I know it's not mounted at all because the system tells me it is not, but I am having a real humdinger of a time googling this for the answer so I guess I'll send it your way.

How can I do this?  I really have no need for whatever is on there, it was defragged before I dual booted and all my files I cared about (legally purchased music, of course) was stored.  So, any suggestions?

---

### Post by mikewhatever on 2009-09-12
:lolflag:
You are funny.

---

### Post by P4man on 2009-09-12
safest and easiest way to resize is a vista partition is using vista's disk manager really.

---

### Post by twright on 2009-09-12
> **nix-idioteque said:**
> hey there, I'm currently on a new Ubuntu install, dual booted with Vista and would like that to change.   I've come to the decision that Vista is no longer the operating system for me, I do however know I can't get rid of it.  So, I sudo apt-get install gparted - good -  starts up - great!  Now to resize my ntfs partition by half freeing up space... 

There's my problem...

A little triangle with an exclamation point.  I know it's not mounted at all because the system tells me it is not, but I am having a real humdinger of a time googling this for the answer so I guess I'll send it your way.

How can I do this?  I really have no need for whatever is on there, it was defragged before I dual booted and all my files I cared about (legally purchased music, of course) was stored.  So, any suggestions?
Hi,
you will have the use the livecd to resize the partitions - doing it that way should work fine.

---

### Post by gadolinio on 2009-09-12
As far as I know, that little triangle with the exclamation mark appears when the partition cannot be read, because it needs to be formatted or mounted. Try mounting it to do the job, but as another user said use the liveCD (it comes with gparted included). If you still have that same problem, make sure your ntfs partition is acually seen as a "NTFS-3G" partition; ntfs-3g is some sort of driver that lets ubuntu read and write partitions in ntfs, which is a win...'s filesystem. Ntfs-3g comes with gparted, you don't need to download anything, just use it.
Hope you find this useful

---

### Post by P4man on 2009-09-12
> **gadolinio said:**
> As far as I know, that little triangle with the exclamation mark appears when the partition cannot be read, because it needs to be formatted or mounted. Try mounting it to do the job,

eeeh. NO! Never mount a partition you want to edit or resize. It should be unmounted.

---

### Post by StuartN on 2009-09-12
> **gadolinio said:**
> Ntfs-3g comes with gparted, you don't need to download anything, just use it.

I thought ntfstools was a separate package, and parted could only modify NTFS partitions once this was installed.

---

### Post by gadolinio on 2009-09-12
If you can't solve your problem with gparted only, DiskManager is an application that can help you too. Use it with the liveCD (you might need to download it with synaptic)

---

### Post by gadolinio on 2009-09-12
Maybe the liveCD has that package already installed. I use ntfs-3g in live sessions, without having installed anything.

---

### Post by P4man on 2009-09-12
> **StuartN said:**
> I thought ntfstools was a separate package, and parted could only modify NTFS partitions once this was installed.

Bingo. I think thats it. And indeed I think its installed in a livecd, but not when you install gparted manually after installing.

---

### Post by cak3 on 2009-09-12
Why you pay for it? Its free you know.

But anyway, you might not want to use gparted to resize ntfs partitions if they have windows installations on them. I have broken windows like that. If possible, I would recommend using the built in partitioned in vista or 7.

---

### Post by blackened on 2009-09-12
> **P4man said:**
> safest and easiest way to resize is a vista partition is using vista's disk manager really.

+1. Many have complained of borking their Vista install by shrinking the NTFS partition with something other than Vista's disk manager. Not wanting to spread FUD, but if you don't have a Vista install disk or recovery disk, then this is potentially a very bad situation waiting to happen.

---

### Post by louieb on 2009-09-12
Use Gparted on a live CD - latest version can be found on [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  and the System Rescue CD. 

Another thing about Gparted and Vista. With Vista - Microsoft changed the way it installs itself in a partition.   When you do the resize un-check the box that says round to cylinders. This is really only necessary if you move the start.

Thats why Vista did not resize nicely when done by other partitioners.  With th box unchecked its safer now.

---

### Post by nix-idioteque on 2009-09-12
Thanks, I'm running on battery power right now (on the road) - But from what I skimmed through I'll load up Winders, shrink my partition volume and add that volume to my ext 3...  

Oh and in regards to the 10 cents thing, I got the topic from an old saying from back when some out houses used to charge 10 cents to use...  Figure out the second half on your own.

---

### Post by lisati on 2009-09-12
**_Thought:_** could the yellow warning icon be a result of Vista not shutting down cleanly?

**+1 **to the previous suggestions of using Vista partition manager to shrink its partition if possible.

Edit: I like the thread title, a nice play on the "spent a penny" rhyme about public conveniences. You don't have to have a sense of humour but it can help......

---

### Post by nix-idioteque on 2009-09-12
> **lisati said:**
> **_Thought:_** could the yellow warning icon be a result of Vista not shutting down cleanly?

**+1 **to the previous suggestions of using Vista partition manager to shrink its partition if possible.

Edit: I like the thread title, a nice play on the "spent a penny" rhyme about public conveniences. You don't have to have a sense of humour but it can help......


+1, I've never been +1!  Anyways, kind of a addendum/errata to my previous post...   I'll shrink my windows volume via Vista, move back to linux and use that to extend my ext 3 partion or come to think of it...  If I made a large unallocated partion can I just use the ext 3 partition to goble that free space up?  

Sorry to sound noobish, I though partitioning was a wizz back when I was 14 using fdisk, but 8 years later I'm kind of polishing my glass eye and sweating profusely at this whole ordeal.  

Viva la resistance!

---

### Post by SlugSlug on 2009-09-12
install ntfs-config  then in system > admin > ntfs config -- -  tick both boxes.

---

### Post by nix-idioteque on 2009-09-12
> **SlugSlug said:**
> install ntfs-config  then in system > admin > ntfs config -- -  tick both boxes.


so when I use that app, I get to the check the boxes but it says that I have to set a mount point for /dev/sda1 - what am I throwing in there?

Also, I tried shrinking my partition via windows but only by 500mb...   Which is nonesthecool.  The only option would be to delete that partition which isn't that great of an Idea seeing as how I don't own a vista install disc.  So, another round of suggestions?

---

### Post by swerdna on 2009-09-12
I've just seen this -- read them all -- imho the valid ones are "shrink using vista (or 7)" and "do it from the live CD" (your Ubuntu install CD / live CD has Gparted). Since you just tried the first, that suggest now to try  the second using your Ubuntu CD.

---

### Post by nix-idioteque on 2009-09-12
> **swerdna said:**
> I've just seen this -- read them all -- imho the valid ones are "shrink using vista (or 7)" and "do it from the live CD" (your Ubuntu install CD / live CD has Gparted). Since you just tried the first, that suggest now to try  the second using your Ubuntu CD.


I can't even shrink my partition from windows at all so something is definately going on, kinda giving up on it for the time being....

---

### Post by jobst on 2009-09-12
> **nix-idioteque said:**
> hey there, I'm currently on a new Ubuntu install, dual booted with Vista and would like that to change.   I've come to the decision that Vista is no longer the operating system for me, I do however know I can't get rid of it.  So, I sudo apt-get install gparted - good -  starts up - great!  Now to resize my ntfs partition by half freeing up space... 

There's my problem...

So, any suggestions?

Go buy yourself 2 USB sticks (they only need to be 2GB), put clonezilla on one and gparted on the other. Then backup your stuff using clonezilla buy booting it, then start gparted and resize.

You then have a recue usb dongle as well ...

jobst

---

### Post by ubudog on 2009-09-12
> **twright said:**
> Hi,
you will have the use the livecd to resize the partitions - doing it that way should work fine.

Yes this should work.

---

### Post by SlugSlug on 2009-09-13
> **nix-idioteque said:**
> so when I use that app, I get to the check the boxes but it says that I have to set a mount point for /dev/sda1 - what am I throwing in there?

Also, I tried shrinking my partition via windows but only by 500mb...   Which is nonesthecool.  The only option would be to delete that partition which isn't that great of an Idea seeing as how I don't own a vista install disc.  So, another round of suggestions?


once you have ticked both boxes gparted should be able to resize that ntfs partition, if it cnt then I would be warry of other methods as you say you dnt own a disk if it goes wrong.

---

