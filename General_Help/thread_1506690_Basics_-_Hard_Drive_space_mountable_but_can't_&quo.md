---
title: "Basics - Hard Drive space mountable but can't &quot;use&quot; it."
date: 2010-06-10
forum: General Help
---

### Post by David Steele on 2010-06-10
First the starter facts - I'm running 9.10 karmic.  I have two Hard Drives, The one which used to hold my Windows OS has just been formatted. (By me) using GParted.

I have created the following partition in /dev/sda1 : a 186 GB space of file system ext2

So - no more Windows.  Which is good.

All my old Windows files are on sda2, along with my Linux OS

When I click on "places", I can see my new drive space listed as "stl" which is the label I gave it.

I can mount (click and open) it, and there is a label there showing "lost and found"

When I try to save anything to this drive, or drag anything from the sda2 into it, I get the message that I don't have permission to do so.

So...  I gather it's something to do with being root, or such like.  (spot the newbie)

I've installed PYSDM but I think I was doing more harm than good when I tried to use it. Likewise the changes I made with Disk Utility simply resulted in me having to re-format the partition again.

So... Baby steps. All I need to do is be able to write and read from this device. Being simple I thought it would just plug and play. Anyone out there want to help out using very small words and speaking s-l-o-w-l-y? :)

---

### Post by Woody1987 on 2010-06-10
First of all, dont use ext2, its terrible, use ext4 for speed or ext3 for stability. To get the correct permissions run:

```

sudo chown username:username /mount/path/
chmod 775 /mount/path

```

---

### Post by colorlessprism on 2010-06-10
chown? i had to do that when i formatted an extra "Media" partition. root owned it so even though it mounted i could do nothing. find out where it is mounted (for me its /mnt/documents).

example:
sudo chown <your-username> /mnt/documents

---

### Post by David Steele on 2010-06-10
okay...  First of all - thanks for your quick reply.

Now, let's talk terminal - 

I assume in my case, since the partition I'm trying to beat into submission is dev/sda1, I would do this -

sudo chown myusername:myusername /dev/sda1/
chmod 775 /dev/sda1

I only ask because I've tried that and so far can't see a difference.

Secondly - I'm a bit baffled about what makes ext2 terrible? Is it terrible as in "you may as well go back to using a ZX Spectrum"?

---

### Post by Woody1987 on 2010-06-11
No, you run chown and chmod on the mount path, so this will usually be something like /media/stl in your case.

ext2 is old and not very stable. It has a tendancy to crash and lose data.

---

### Post by David Steele on 2010-06-11
Brilliant!

Thanks to you both for helping out.

So - chown would be "CHange OWNer" 
Does that make chmod "CHange MODification"? And why 775?  Off to google....

[http://www.sofer.com/research/unix.html](http://www.sofer.com/research/unix.html)

Right!  So it's a series of commands - 7 being the "most free". Read, Execute and Write.

Question - Why not 777?

---

