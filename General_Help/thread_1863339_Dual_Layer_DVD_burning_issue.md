---
title: "Dual Layer DVD burning issue"
date: 2011-10-17
forum: General Help
---

### Post by what_indeed on 2011-10-17
Hi folks, I need a little help, please.  I've been doing some video editing/creation for a while and have had no problems.  Recently, I made a movie that was 2h 46min long which was 6.9Gb in size.  So, ok, I got a dual layer 8.5Gb blank DVD and did the usual.  Except I got an error when attempting to write to this disc.  I tried another blank disc and then another.  Then I tried a different brand.  Still no go.  I searched but could not find any posts that seemed to be able to help me.  If anyone has any ideas I would appreciate it. Here's the info:

Computer:
Ubuntu 10:10 / 2.6.35-30-generic-pae
Gnome 2.32.0
Acer Aspire 5742-Z
Pentium P6100 DualCore 2.0GHz
Optiarc DVD-RW AD-7580S Multirecorder

Error Log:
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs closing connection for BraseroGrowisofs
Session error : unknown (brasero_burn_record brasero-burn.c:2865)

Thanks in advance for any help you can provide!

---

### Post by fedoraboy on 2011-10-17
I am no help whatsoever... but listening quietly for any replies.  I've had issues burning dual layer DVDs on ubuntu since I can remember.  I had written it off as a problem with my old hardware.  Now I have new hardware and still see the same issue.

---

### Post by fedoraboy on 2011-10-17
it's been a while since I was looking at this... just came across this thread:  [http://ubuntuforums.org/showthread.php?p=5920783#post5920783]("http://ubuntuforums.org/showthread.php?p=5920783#post5920783")

I was testing mine remotely (with the wife putting dvds in the drive when I asked via IM).  I just asked and ... sure enough, mine are Memorex.   What about yours?  What brand?

---

### Post by what_indeed on 2011-10-18
The first few discs I tried were Memorex.  I had a Verbatim DL-DVD someone gave me (that is blank) but it's a no go on that as well.  When I pop either of those into the drive, it recognizes them but it won't write to them.  I read the thread you posted, thanks, I'll see about getting a different brand next time I'm out-n-about.  I hate to fork over some more cash to find out those won't work either.  We'll see.

incidentally, I find video editing to be a total pain using a linux machine.  I love linux, have worked with three distros, Ubuntu being my favorite/most stable.  As far as video editing I've used PiTiVi, LiVES, Kino, OpenShot, Open Movie Editor and Kdenlive.  The best one (relatively speaking), IMO, is Kdenlive, although it is quite glitchy.

Buring with brasero has always been a nightmare for me.  K3b is ok, although it has brain-farts too.  Usually when one doesn't work it leaves my drive unable to read new blank discs and I have to exit out of everything and restart my machine to reset everything.  This is usually after rendering a project and then trying to burn it.  Any other time, I can just burn an iso image or whatever other kind of data I want with no problems.

Now, don't get me wrong, I'm a Linux man, but geez, at least with (gulp) Windows Movie Maker everything worked the first time with no glitches.  Well, I just have to say it like it is.  But I'm willing to pain through these issues because I would still rather use Linux, which is why I'm here for help.  This forum has been a TREMENDOUS help to me over the last year.

I'll keep my eyes out for any solutions to this DL issue.  Thanks, and have a good one.:popcorn:

---

### Post by fedoraboy on 2011-10-22
Okay, it took me a few days to find a non-Memorex dual layer dvd.  No one had anything but Memorex DL in the stores and I had to order from Amazon.

I just successfully wrote a full sized dual layer Verbatim disk.  I am not using Brasero, but using command line tools (from a script) that uses growisofs.  But from your error logs, it looks like that's what Brasero might be using, too.

I bought the smallest pack of Verbatims I could find ... just for a test:
[http://www.amazon.com/Verbatim-95166-2-4x-6x-Recordable-10-Disc/dp/B000B018VO/ref=sr_1_4?ie=UTF8&qid=1319311254&sr=8-4](http://www.amazon.com/Verbatim-95166-2-4x-6x-Recordable-10-Disc/dp/B000B018VO/ref=sr_1_4?ie=UTF8&qid=1319311254&sr=8-4)

---

### Post by what_indeed on 2011-10-25
Thanks, fed, I still haven't bought any but now with that link to Amazon I'll just order from them.  I'll see what happens after that.  Take care.

Bob

---

### Post by Derek Karpinski on 2011-10-26
Memorex are well known for bad burns.  A lot of stores carry them, sadly.

I was pulling my hair out trying to make windows backup disks, and once you start, you can't 'restart'.  Went through 6 discs, bought another brand, and I got a perfect burn the first disc.

Also, my DVD drive needed a firmware upgrade to properly recognize DL discs.

---

### Post by mc4man on 2011-10-26
For dual-layer dvd I'd only use Verbatim, nothing else close
(the best Verbatims where/are? still the ones that are  "Made in Singapore", but anywhere it's made is superior

The individually cased 3pk.s are great if on sale , for pancake wouldn't go over the ten size. (the 25 - 50 or higher count pancakes may contain a couple of lower quality disks

---

