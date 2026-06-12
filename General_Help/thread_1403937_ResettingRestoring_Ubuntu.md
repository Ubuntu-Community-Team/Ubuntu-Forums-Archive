---
title: "Resetting/Restoring Ubuntu?"
date: 2010-02-10
forum: General Help
---

### Post by rwt911 on 2010-02-10
I am duel booting windows and ubuntu and got tired of all the stuff I did to my ubuntu instalation. I was wondering If I could just reset/restore ubuntu it to how it was when I first installed it, without messing with my windows installation, so I can have a clean start.

Thanks 

rwt911

---

### Post by Megafag on 2010-02-10
> **rwt911 said:**
> I am duel booting windows and ubuntu and got tired of all the stuff I did to my ubuntu instalation. I was wondering If I could just reset/restore ubuntu it to how it was when I first installed it, without messing with my windows installation, so I can have a clean start.

Thanks 

rwt911

You could do a fresh re-install, if you dont mind losing all the programs you downloaded since.

that wont affect your windows partition so long as you do it right.

---

### Post by rwt911 on 2010-02-10
> **Megafag said:**
> You could do a fresh re-install, if you dont mind losing all the programs you downloaded since.

that wont affect your windows partition so long as you do it right.

Could you infer on what the right way is. I have done a lot of clean installs of Ubuntu, would I do it a different way in this situation.

---

### Post by Bright_View on 2010-02-10
In the step where you create the partitions where Ubuntu will be installed, just make sure NOT to format the partition with Windows.  Other than that, installation is the same.

---

### Post by serpentracer on 2010-02-10
I think  you guys are missing what he's asking.

I think he wants to do a "system restore" like you can in windows...
yet another thing windows does better in my opinion.

hopefully ubuntu will in the future....it's really annoying getting an update to a kernel and it screws up your computer..and the only fix is to reinstall the whole thing again...PITA!

---

### Post by Bright_View on 2010-02-10
I don't know if it's because I had hardware problems and had to re-install Ubuntu about 20 times in a row over a period of a few weeks, but I don't find that installing Ubuntu from scratch takes that much time.  Maybe if you have it customized exactly to your liking and want it back to the same configuration it would, but it sounds like he wants a fresh start so this is not an issue.

Not sure if there is a "system restore" - anybody know?  Could be handy I guess, but I've never needed it.

---

### Post by Miljet on 2010-02-10
> .it's really annoying getting an update to a kernel and it screws up your computer..and the only fix is to reinstall the whole thing again

No, the real fix is to simply boot into the old kernel, which is still there.

---

### Post by Megafag on 2010-02-10
> **serpentracer said:**
> I think  you guys are missing what he's asking.

I think he wants to do a "system restore" like you can in windows...
yet another thing windows does better in my opinion.

hopefully ubuntu will in the future....it's really annoying getting an update to a kernel and it screws up your computer..and the only fix is to reinstall the whole thing again...PITA!

This is not a "Windows is better than Ubuntu forum" my friend this is an ubuntu support forum. the OP is asking for support, not opinions.

and the OP is asking for a way to set ubuntu back how it is when he started. what better way than to do a fresh re-install?

---

### Post by john newbuntu on 2010-02-10
liveCD, remastersys and clonezilla can help you here.  The last two keep your data too!

---

### Post by Miljet on 2010-02-11
> This is not a "Windows is better than Ubuntu forum" my friend this is an ubuntu support forum

Thank You! That is exactly what I wanted to say.

---

### Post by philinux on 2010-02-11
> **rwt911 said:**
> Could you infer on what the right way is. I have done a lot of clean installs of Ubuntu, would I do it a different way in this situation.

Have you got your home on it's own partition?

---

### Post by serpentracer on 2010-02-11
> **Megafag said:**
> This is not a "Windows is better than Ubuntu forum" my friend this is an ubuntu support forum. the OP is asking for support, not opinions.
 
and the OP is asking for a way to set ubuntu back how it is when he started. what better way than to do a fresh re-install?
 
 
why do you guys all get so upset when someone mentions the short comings of ubuntu?
there are some things windows does way way better and the option to undo changes without losing all of your files is one of them.
 
re installing a os just for one little problem is a crazy idea..that shouldn't have to even be the answer. it shouldn't even have to be an option.
how is reinstalling the answer if you have a bunch of important files that you cannot lose?  and don't say just burn them to a disc...what if you can't get that kind of thing to work?
 
how do you improve things???? how about listening to some constructive criticism...just saying.

---

### Post by Bright_View on 2010-02-11
Serpentracer - if you create a separate partition for your home directory, then when you re-install the OS you won't lose any files that are saved in there because you'll only have to re-format the root partition.  No need to burn anything to disk (although this is a good idea anyways).

Also, I'm not sure where it was stated that you must reinstall the os for "one little problem".  We're saying that if the OP wants their system back to the original state, a fresh re-install is an easy way to accomplish this.

One last thing to keep in mind - I'm pretty sure I've read that few of the actual developers of Ubuntu read this forum much, so any of your constructive criticism is wasted on the majority of people who are here to help.  Most of us cannot change the rules, we can only play by them, so if a feature doesn't exist we can only offer alternative ways to do things.  You personally may not like some of these alternatives, but there you have it.

---

### Post by l-x-l on 2010-02-12
> **rwt911 said:**
> Could you infer on what the right way is. I have done a lot of clean installs of Ubuntu, would I do it a different way in this situation.

What I would do is a clean install of Ubuntu again except this time put your home folder on a seperate partition. This way, if you ever need to subsequently reinstall ubuntu again all of your data, documents, downloads, music, etc won't get lost with a reinstall.

Also, if you want to backup a list of programs you've downloaded, go to Synaptic & select File -> Save Markings somewhere safe. When it's time to reinstall, File -> Read Markings. Of course you will have to reinstall any/all repos you had before.

---

### Post by rwt911 on 2010-02-14
I have decided to reinstall, keeping my windows partition intact, but during installation when I pick which partition, It is only giving me the option to install it on my whole hard drive.

any suggestion?

---

### Post by Jpenguin on 2010-02-14
I think you want 'advanced/custom partitioning'

---

### Post by rwt911 on 2010-02-14
> **Jpenguin said:**
> I think you want 'advanced/custom partitioning'

Oh, ok, thanks

---

