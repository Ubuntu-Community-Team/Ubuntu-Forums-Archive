---
title: "Unusual Nautilus USB Transfer Error..."
date: 2010-03-28
forum: General Help
---

### Post by Ghost|BTFH on 2010-03-28
System:  Ubuntu 9.10 Karmic Koala, 64-bit.  AMD x2 dual core, 2gb ram on ASUS motherboard.

This is a first for me.  I'm used to slow speeds on USB 2.0 in Linux, I've seldom if ever seen anything beyond 13mb/s transfer rates and I don't expect that to change anytime in the near future...

That being said, I've recently been doing some massive backups of my 500gb hard drive to clean it up and prepare for a move - physical - and wanted to minimize my risk of a hard drive failure from shock, etc.

Anyhow, I go to transfer my /Music folder, which is filled with all .flac files I've ripped from my not-so-small CD collection.  Long story short, that's almost 70gb of data, in 25mb file clumps.  Shouldn't be too big of an issue for Nautilus to handle, right?

Wrong!  It "completed" the job, transferring about 10% of the entire file collection...taking a little over 1.5 hours.  So, perplexed, I gave it another go, only to get a generic error from Nautilus "Input/Output error"

Okay, now at this point I'm worried there's an issue with my USB drive.  So I fire up a terminal, whip out trusty cp and give the /Music folder a quick and decisive cp -dvr ~/Music/ /media/USBdrive/

Bam.  It's off and running, little over an hour later, 100% files transferred.  So, not 7gb in 1.5 hours, but 70gb in about an hour.  Impressed, I launch cp on my /Video directory as well, with quick zippy results...well, around 19-20mb/s at least.

While this was going on, I noticed a few files I had missed, one of them being about 8gb in size (VirtualBox drive, figures) so I, without thinking, slap that through Nautilus while the rest is going on.

What I see I still cannot understand.  20-30mb/s transfer rate...which dies 1/3rd of the way through with the same vague generic I/O Error message.

Has anyone run into such a situation?  Are there known bugs for this that I'm missing?  I've done an extensive search via Google for any information about this, only to find ancient bugs from Hardy and back, so I'm presuming this is something completely different?

Cheers,
Ghost|BTFH

---

