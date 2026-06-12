---
title: "md5sum: I/O Error when used to verify CD-R"
date: 2012-06-26
forum: General Help
---

### Post by stlu on 2012-06-26
It's possible that I'm the only idiot who tried this, but in case anyone else is pulling their hair out trying to get this to work, I am providing this warning.

I have wasted about 30 CDRs because the md5sum utility did not work how I expected it to.  Now I understand why.

First, I had the concept (mostly) understood that Linux treats devices as files.  Therefore, md5sum should be able to run on a burned CD in the same way it is used on an .ISO image.

I tested this on a Ubuntu CD which canonical had mailed to me:
```

$ sudo md5sum /dev/sr0

```And the correct md5sum was produced, exactly the same as the ISO Image md5sum.

So, I recently got some CD-Rs, as I wanted to install the latest version of Ubuntu.  I had some selection of various CD-R Drives which I had never used for burning, and so I would test the drives, and see if the CD was burned correctly using md5sum.

And the first CD I burned, I tested it:
```

$ sudo md5sum /dev/sr0
md5sum: I/O Error ...

```Long story short, I tried CDR after CDR on each of my uncertain drives, until I was convinced that the CDRs must have been defective, because how could all these drives not work?  I never thought that it was the test I used which was the cause of the trouble.

After meeting with a friend who burns a LOT of stuff, I had him burn onto one of my CDRs with his hardware/software which he knew worked, to see if they really were defective.  While his software confirmed a successful write, my md5sum still produced an I/O error on the same CDR.  So I ran md5sum under TTY1 to see any further errors were printed to the screen, and I found that the errors were occurring trying to read sectors that ran beyond the actual burned image!

So I thought up a modified test, where I used "dd" to read only the sectors that were actually written:

The ubuntu 12.04 desktop i386 ISO is 735358976 bytes.  Divide that by the sector count of 2048, and you have 359062 sectors to check. (The I/O error messages were errors reading 359063 and up - sectors which do not contain anything)

This time, I used dd to take only the sectors that were written to, and it would ignore anything past that point:
```

$ sudo dd if=/dev/sr0 bs=2048 count=359062 | md5sum
d791352694374f1c478779f7f4447a3f  -

```And finally I got the right output.  Only now I have about 30 duplicate CDRs of the same ISO and that was such a stupid waste...  I am so embarrassed.

So I learned that the kernel was reading the device like a file, and though it somehow worked fine on the professionally created ubuntu CD, it tries to read a CD-R from front to back without respecting where the data actually stopped.  It's doing what I told it to, but I expected it to stop reading the data where the writing stopped, in a similar manner to how it will not read past a partition boundary when called to pull raw data from a hard drive.

So the moral of the story is don't use md5sum on a CDR.  It won't work.  Oh, and dont run media tests when you aren't certain of both drive and media, cuz it leaves you still guessing which is the problem...](*,)

Aaargh!

---

