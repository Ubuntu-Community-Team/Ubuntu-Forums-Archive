---
title: "Total noob backup question - only read if you have patience - not urgent."
date: 2011-03-17
forum: General Help
---

### Post by atomicben on 2011-03-17
I consider myself a M$ expert and I'm very familiar with all sorts of disaster recovery on that platform but when it comes to ubuntu/linux I'm lost.

I've read all these different ways to preform backups but none of them give me the confidence that I'm really getting what I need.  eg.  It seems like SBackup (and many other solutions) only backup my home folder.  This seems crazy to me.  IMO that is like me backing up 'my documents' in Windoze and telling my CEO our butts are covered.  

There's also a TAR option.  Well, under M$ backing up your C drive doesn't cut it either because in a restore situation that's not going to restore the MBR and NTloader...basically make the drive bootable....Even under DOS you just can't copy command.com to the c drive and boot.  What am I missing?  Oh, and dd sounds dangerous and on it's own doesn't have compression (as far as I know).  I also can't have a nice scheduler or restore disk (besides live cd).  If partimage is my only option, fine, that that so-called gui looks like a wicker old version of GHOST...Nasty DOS stuff.  

I want/need a solution that I know will image my whole drive (all partitions) and compress it daily (or at least weekly on my personal system) so that when I need to recover I can restore the whole damn system... grub... programs... all home dir's... the whole system drive and still be bootable!  A nice GUI and scheduler along with a great rescue disk would be the tops.

Something like GHOST or ACRONIS (I loved acronis under M$)...  if the above mentioned solutions will do this, then just tell me to shut up.  Otherwise, I need advice on a disaster recovery solution that I can count on.

I mean, from what I've seen and know, there's no way a good IT manager would use sbackup on an enterprise server... or am I wrong?  hell, I don't even know what have of these directories contain, so please, be gentle.

Thanks!

---

### Post by JKyleOKC on 2011-03-17
Have a look at "clonezilla" which is equivalent to Ghost or Acronis; it can do a full disk image, or less, as you prefer.

I've not used it myself but it's often recommended. I do have a copy of the clonezilla live cd for use if I think I need it, but for the moment I'm just sending my critical documents to a cloud-based free service as a stopgap. I did use a package called BackupPC, which is in the repositories, but found it a bit complicated to configure. Specifically, it would fail to copy certain subdirectory content from Windows boxes on my LAN. Attempting to solve that problem led to my opening my entire LAN to an invasion, resulting in having to reformat and reinstall every box. Fortunately no critical data was lost, but I've never reinstalled the package. Once burnt, twice shy...

Copying the home directory is a bit more than just backing up "My Documents" since it also includes the equivalent of the user-specific portions of the Windows registry, as hidden files within the home directory. Also copying the /etc directory will get most of the rest of the system configuration. There are other areas that hold the packages you've downloaded for installation, and there's really no need to backup the main system programs that are on your installation media. However, for your needs a full-disk imaging system is probably the optimum solution!

---

### Post by varunendra on 2011-03-18
+1 to clonezilla.

I have personally tested clonezilla-live. It presents you with the option to image partitions or entire disk including MBR / boot sectors (default choice for disk image).

It can save to, or read from an image stored on a local disk (including USB drives) or a location over network, with (or without - if so needed) a variety of compression levels.

So with a disk image (created with default options), you can make even a new, blank, unformatted drive up and running just by restoring the image on that drive.

Its interface is not much attractive as Acronis or even ghost, but is more capable and user-friendly in my opinion. Presents with a lot of custom backup/restore options if "advanced mode" is chosen. If all those options seem confusing, it is perfectly okay to go with default options.

Last but not least, right before executing a backup/restore operation, it presents you the commandline for the execution of same operation with the same choices you have made. So that you can use that command-line at command prompt or in a shell-script to automate or quick-perform the same operation later.

I hope that should be sufficient for your needs. However, if you need incremental and scheduled backups, then let's hope someone could throw some more light on how to do it easily, else you may have to dig it a little bit yourself.

And please don't shut up, instead go ahead & tell us what option you chose and how it is working for you.

---

### Post by atomicben on 2011-03-18
Wow, two great answers and a concensus on a solution.  Thanks a lot varunendra & JKyleOKC for taking the time to look at this and provide verbose answers.  I think I will give this clonezilla a try.

Have a nice weekend.

Ben

---

### Post by Rasa1111 on 2011-03-18
Hi Ben,

 I honestly don't think that this tool will be too useful for what you're looking for.. (but i don't know)...

Anyway,
 It is called "Remastersys" , and I just used it for the first time the other day, and it worked soo well!

 I was skeptical of using it for awhile, just because I thought it'd be too hard or that id break something,  lol

But it was very simple, and I was able to create a clone of me entire setup, as a LiveCD that I can use/install again. 

It kept all my programs, all my settings, my AWN dock/panel, everything!
Even files i'd placed in my home folder, pics/folders, etc. 
So when i boot the CD, it's exactly like when I boot up my laptop,
can't even tell the difference.  lol

 So, maybe not useful for you here/now..
but maybe it could be useful to you sometime in the future? I dont know.

I have checked out clonezilla a few times, 
(maybe thats the one I was thinking was hard?) :lol:
gotta be, cuz remastersys is super easy. lol

I read tons of great stuff about clonezilla though. 

Good luck! have fun. :)

---

### Post by varunendra on 2011-03-18
> **Rasa1111 said:**
> Hi Ben,

 I honestly don't think that this tool will be too useful for what you're looking for.. (but i don't know)...

Anyway,
 It is called "Remastersys" , and I just used it for the first time the other day, and it worked soo well!

Hi Rasa1111,

First, I'd personally thank you and truly appreciate  your encouraging words on that 'heart-breaking' thread of mine which I don't want to bump anymore. :)

Now on topic here. I'm a huge fan of Remastersys and have been using it not only for personal, but sometimes for my official needs too. I've distributed a few times a bunch of DVDs among my friends customized/created with this great tool just to impress them with the magic of linux + compiz effects + all those great applications in the surprisingly small size that only linux offers.

BUT,

The bottleneck comes when the size of the customized image exceeds the limit of 1 single-layer DVD (that is 4.2 GB). It simply refuses to create iso in this case. Besides, its restoration process involves the complete installation steps (even though some of them are not required at all) and thus takes unnecessary time. That's why I suggested clonezilla. It of-course creates only an offline backup image, not a live one, but has no size-limits and can be used over network.

If size or incremental backup is not an issue for ben, then I'd agree that Remastersys can be the easiest solution for him. (well for the 'incremental-backup' part, I'm not sure about the capability of clonezilla either. Maybe someone else could confirm....)

[However, as a side-note, since Remastersys has its own advantages (at least in the personal use scenario), I'd recommend ben to get familiar with it. Even if not for his current requirements, for personal use it's definitely going to astonish him with what it does especially because he has been a Window user so far.]

---

