---
title: "fsck apparently finished but no command prompt"
date: 2011-09-28
forum: General Help
---

### Post by OriTheEep on 2011-09-28
Hopefully this will just be a quickie.

One of the drives in a RAID 1 array, which I profoundly regret having set up but haven't got around to changing, overheated to the extent that the array stopped working. When all had cooled down and seemed operational, I ran diff to compare with a copy on a USB drive that I started keeping after I lost faith in the original array.

This seized up at the same point twice in succession so I unmounted the array drive and fscked it (see attached). The terminal window is currently flashing its cursor at me at the start of the next line and has been doing so for more than an hour.

Can anybody tell me what is going on?

Thanks!

---

### Post by OriTheEep on 2011-09-28
Whoops! Forgot to attach...

---

### Post by blueridgedog on 2011-09-28
Nothing attached.  Is there drive activity during the long period?

---

### Post by OriTheEep on 2011-09-28
> **blueridgedog said:**
> Nothing attached. 
 
You just beat me to it! Thanks for being so quick. :) 
 
> **blueridgedog said:**
> Is there drive activity during the long period? 
 
Drives are SATA so I can only say that there is the odd bit of disk activity in the system but not where it is taking place. 
 
Sorry :(

---

### Post by blueridgedog on 2011-09-28
Have you tried verbose mode with -V?

---

### Post by OriTheEep on 2011-09-28
> **blueridgedog said:**
> Have you tried verbose mode with -V?

With the benefit of hindsight...

I haven't yet aborted fsck - while it is laying claim to the disk I don't suppose anything else can wade in and make things worse.

I am a little concerned that some alteration to the disk may have been interrupted. Admittedly, the completeness of the summary message from fsck probably indicates that all changes intended by the main programme were effected but how rigorously does it check its subprocesses? I've come a cropper before where a programme has blithely continued after a disk write only to find that the information written only got as far as the cache* and disappeared following a reboot.

I have no idea if any harm that might have been done can be undone. If definitely not, then I will follow your suggestion and hope!

Thanks for sticking with me.

*Does fsck switch disk caching off?

---

### Post by blueridgedog on 2011-09-29
> **OriTheEep said:**
> *Does fsck switch disk caching off?

Given that the volume is unmounted when fsck is run, I think caching is not in play.  The umount operation should sync the disk identical to the sync command ([http://linux.die.net/man/2/sync](http://linux.die.net/man/2/sync)).

---

### Post by OriTheEep on 2011-09-29
> **blueridgedog said:**
> Given that the volume is unmounted when fsck is run, I think caching is not in play.  The umount operation should sync the disk identical to the sync command ([http://linux.die.net/man/2/sync](http://linux.die.net/man/2/sync)).

I note with amusement their assertion: "Errors[:] This function is always successful." but I was referring to the hardware cache that most HDDs seem to have these days. Presumably, a call to the driver can switch this on and off?

Anyway, I have now aborted fsck and will have to reboot (so it doesn't think it's locked out of using the disk as it clearly didn't get as far as releasing it before seizing up) and run it again.

Will report back as soon as I have anything - perhaps even the report of a successful operation?

Cheers!

---

### Post by OriTheEep on 2011-09-30
> **OriTheEep said:**
> 
Will report back as soon as I have anything - perhaps even the report of a successful operation?
Cheers!


Well, this is what I appear to now have :)

Thousands of files have gone missing but, this time (!), I have a backup from which to replace them.

Curiously, fsck didn't have anything more to say with -V than it did without (?).

Thanks for sticking with me and keeping me going. That was more help than perhaps you realise.

---

