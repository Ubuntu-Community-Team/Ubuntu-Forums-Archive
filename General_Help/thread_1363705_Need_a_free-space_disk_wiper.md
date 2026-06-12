---
title: "Need a free-space disk wiper"
date: 2009-12-24
forum: General Help
---

### Post by JackRock on 2009-12-24
I'm looking for a good free-space wiper that can do simple wipes, as well as DoD-level wipes.  A component of [url=http://www.auslogics.com/en/]Auslogics' BoostSpeed had this, but they don't have a linux-compatible version.  I suppose I could try with Wine, but I prefer not to.

The trick is to wipe the free space, but not the current data.

Any suggestions?

---

### Post by falconindy on 2009-12-24
Write zeroes to a file on the disk until it fills up, then delete that file:
```
dd if=/dev/zero of=/path/to/file.of.zeroes bs=1m
```

Note that most methods of "wiping" are mostly ineffective on journaling file systems.

---

### Post by steve161 on 2009-12-24
secure-delete.  It is in the repos.

---

### Post by JackRock on 2009-12-25
> **steve161 said:**
> secure-delete.  It is in the repos.

We have a winner!  That worked beautifully.  It created a file called "oooooooo.ooo" in the /root/ directory, which suddenly was over 300+ gb.  But I restarted, and it went away.  I imagine that's how it did the wipe - create a large worthless and unreadable file.

---

### Post by sliketymo on 2009-12-25
Dosn't BleachBit clean free space ?

---

### Post by JackRock on 2009-12-25
> **sliketymo said:**
> Dosn't BleachBit clean free space ?

Not that the description notes.  It seems specifically to delete existing files more "securely".  What I wanted was a way to wipe out free space that's not being taken care of by "current" files.

BleachBit seems to take a "current" file and make it into free space.

---

### Post by falconindy on 2009-12-25
> **JackRock said:**
> We have a winner!  That worked beautifully.  It created a file called "oooooooo.ooo" in the /root/ directory, which suddenly was over 300+ gb.  But I restarted, and it went away.  I imagine that's how it did the wipe - create a large worthless and unreadable file.
I suggest you read the following before you assume that any type of "secure delete" utility will provide the results you're looking for:

[http://www.slac.stanford.edu/comp/unix/secure-erase.html](http://www.slac.stanford.edu/comp/unix/secure-erase.html)

In particular, the following snippet:
> One major problem with all of these utilities is that most modern file systems use techniques called "journaling" or "logging" to help prevent file system corruption. Unfortunately, these techniques can also make it nearly impossible to ensure that all traces of a file's data get overwritten unless you are willing to completely wipe out all data on the disk. Operating system buffers, hardware caches, "bad block" lists and file system corruption (e.g., orphaned inodes which are neither in a file nor in the disk's free space) can also interfere with the proper operation of these utilities.
Bottom line: if you want to be able to use a secure delete utility, you'll need a filesystem like ext2 which doesn't use a journal.

---

### Post by JackRock on 2009-12-25
Frankly, I'm okay with that.  I'm not trying to hide top secret data or anything.  So as long as it makes it a bit more of a pain for any thieves to retrieve stolen data, I'm good.

Eventually, I'll get another SATA HDD to replace the IDE secondary I have, and then I'll do a complete clean install on the next Ubuntu release, and then swap/format/swap.

---

### Post by steve161 on 2009-12-25
Bleachbit does have an option to wipe free space with a one pass zero wipe.  I think it is under 'system'.

---

### Post by sliketymo on 2009-12-25
Right.Run it 3 times.

---

### Post by Andrew.Z on 2009-12-31
> **sliketymo said:**
> Right.Run it 3 times.

The increased effectiveness of multiple passes is an urban legend, but it may be necessary to wipe the free disk space (once) in case the file has moved around.

---

### Post by Andrew.Z on 2009-12-31
(Sorry, I didn't see this post the first time.)


> **JackRock said:**
> Not that the description notes.  It seems specifically to delete existing files more "securely".  What I wanted was a way to wipe out free space that's not being taken care of by "current" files.

BleachBit seems to take a "current" file and make it into free space.

BleachBit has three independent (but related) operations which should be not be confused:

1. Wiping free disk space
2. Shredding arbitrary files (such as a spreadsheet on your desktop)
3. Shredding files it cleans (such as cookies and cache)

---

### Post by JackRock on 2009-12-31
> **Andrew.Z said:**
> The increased effectiveness of multiple passes is an urban legend, but it may be necessary to wipe the free disk space (once) in case the file has moved around.

Curious.  That's the first I've heard of it not being true.  This "urban legend" has both the entire IT industry (I'm taking the Security+ course, now, and it says to do it multiple times) and the DoD convinced.

Either way, secure-delete did well enough for me.  I may check out BleachBit later when I do it again.  I usually do a free space wipe once a month.

---

### Post by Andrew.Z on 2009-12-31
> **JackRock said:**
> Curious.  That's the first I've heard of it not being true.  This "urban legend" has both the entire IT industry (I'm taking the Security+ course, now, and it says to do it multiple times) and the DoD convinced.

Quote from Wikipedia on page "Data remanence" regarding the DoD:

"As of the Nov 2007 edition of the DSS C&SM, overwriting is no longer acceptable for sanitization of magnetic media. Only degaussing  (with an NSA approved degausser) or physical destruction is acceptable."

The reason degaussing and physical destruction are more effective is they erase remapped bad sectors which are generally inaccessible to the operating system (and therefore all applications such as BleachBit and secure-delete).  The number of bad sectors is generally pretty small on new hardware, but the NSA and DoD don't take chances.

There is a lot more discussion here (especially on the difference between 1 and 35 passes): [[BleachBit] How many passes for the "free disk space" option?](http://bleachbit.sourceforge.net/forum/how-many-passes-free-disk-space-option), and if it not mentioned there, there is a big difference between 
1. wiping a file in a file system
2. wiping the free space
3. wiping the entire drive accessible to the OS
4. wiping the entire drive including the remapped sectors hidden to the OS


> Either way, secure-delete did well enough for me.  I may check out BleachBit later when I do it again.  I usually do a free space wipe once a month.

Don't forget to wipe your swap file (which BleachBit does since 0.7.0, IIRC).  In case you are really paranoid, another area you may be missing is slack space (which BleachBit doesn't wipe, at least not as of 0.7.2).

---

### Post by dcstar on 2009-12-31
> **JackRock said:**
> Curious.  That's the first I've heard of it not being true.  This "urban legend" has both the entire IT industry (**I'm taking the Security+ course, now**, and it says to do it multiple times) and the DoD convinced.
.......

Let me guess, lots of quotes related to technologies years (if not decades) out of date presented to you by people who have little (or no) idea about how data is actually encoded and stored on modern storage media?

It's strange that if you do your own research that you find so many revisions to the self-serving rubbish often presented in these things, isn't it?

I still see people quoting Gutmann when the hardware they are using has no relevance to his original work:

[http://en.wikipedia.org/wiki/Gutmann_method](http://en.wikipedia.org/wiki/Gutmann_method)

---

### Post by JackRock on 2009-12-31
> **dcstar said:**
> Let me guess, lots of quotes related to technologies years (if not decades) out of date presented to you by people who have little (or no) idea about how data is actually encoded and stored on modern storage media?

Not true.  Current working instructors, with a course less than 2 years old.  Almost all of the technology they reference is still in use today's commercial world.  (I say "almost" because this thread is the first that I've seen anything different than my course)

> **Andrew.Z said:**
> Don't forget to wipe your swap file (which BleachBit does since 0.7.0, IIRC). In case you are really paranoid, another area you may be missing is slack space (which BleachBit doesn't wipe, at least not as of 0.7.2).

Thanks.  I had forgot about that.  Does Secure-delete work on the swap file?  Any recommendations on slack space?

---

### Post by dcstar on 2009-12-31
> **JackRock said:**
> Not true.  Current working instructors, with a course less than 2 years old.  Almost all of the technology they reference is still in use today's commercial world.  (I say "almost" because this thread is the first that I've seen anything different than my course)


Great, have they told you that most commercial "disk wipe" products are less effective than the free NIST tool that actually uses the ATA-standard secure wipe feature built into most modern drives?

Have the explained how modern disk encoding techniques makes it almost impossible to guarantee an actual write to a specific bit area on a disk platter no matter how many "random" passes you do?

Do they also tell you how they cope with SSDs that dynamically remap physical write areas (to spread the finite write cycles across the whole chip and increase the effective life of the device)?

If all of these things now happen, then things have (finally) improved and people may get some real value and knowledge of the realities of this area, otherwise more myths may just be getting repeated.

---

### Post by Cheesemill on 2009-12-31
> **JackRock said:**
> Curious.  That's the first I've heard of it not being true.  This "urban legend" has both the entire IT industry (I'm taking the Security+ course, now, and it says to do it multiple times) and the DoD convinced.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

---

### Post by dcstar on 2010-01-01
> **Cheesemill said:**
> [http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

Shush!, if you point out that this particular piece of paranoia has little basis in reality then people might start to question other aspects of the "Security" industry.......   ;-)

Belief is a strong thing (even unsubstantiated belief), people can build whole careers on it (thank you very much.........)

---

