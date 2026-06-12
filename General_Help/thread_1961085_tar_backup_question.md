---
title: "tar backup question"
date: 2012-04-18
forum: General Help
---

### Post by teeleef on 2012-04-18
Hi,  I have a HP Proliant box running Freenas to store all my important media, however I am using Deja Dup periodically to backup stuff from my laptop to a small Qnap NAS box.  Deja Dup uses tar to compress the data, if I delete something on my laptop, Deja Dup restores from the NAS as it should.

My question is.... if the laptop hard drive failed, and I installed  Ubuntu onto the new drive along with Deja Dup, would all the tar files be copied back to the laptop automatically or is there a danger that the files on the NAS would be wiped instead?


Thanks


Teeleef

---

### Post by Roasted on 2012-04-18
I'm not sure I understand entirely, however if your hard drive fails I would think you would lose the automatic Deja Dup backup settings anyway, so I don't see how any additional backups would be made until you set them up again.

On top of that, Deja Dup isn't like rsync --delete where if the data is missing on source, it deletes it on the destination... At least, from what I understand.

---

### Post by ratcheer on 2012-04-18
In DejaDup, all the real work is done by rsync. DejaDup is just a front-end application. Actually, DejaDup is a front end to Duplicity, which is a front end to rsync.

Tim

---

### Post by teeleef on 2012-04-18
Thanks Gents....  

Yeah the danger is losing stuff off the NAS.  I didn't want a scenario of load of backup tarballs on the new laptop drive either. 

I wonder then if one can find backup software that backs up data in its pure form without tarring the data?


Teeleef

---

### Post by ratcheer on 2012-04-18
I am not sure I understand your problem with this, teeleef. What are you trying to back up? Normally, just your user data is specified. If you lose your system, first you reinstall your system, then you restore your user data from backups. When you restore your system, you will get back your tar utility, so your backups will be usable.

If you want full system recovery from backups, you probably need some kind of disk imaging software, such as Clonezilla. IMHO, this is overkill. But it depends on what you need and want.

Here is an unasked for tip. Before running any backups, clear your web browser's cache. This can reduce the size of data backed up by hundreds of MB.

Tim

---

### Post by teeleef on 2012-04-18
ratcheer, thanks for your reply.  

I wanted to backup periodically my Documents folder for example.  Any changes would be altered also in the backup tarball.  

My concern is that if my laptop drive failed dramatically and a new install was done...my new /home/Documents folder would be empty therefore installing Deja Dup may not result in the tar files being copied back to my new empty Documents folder!  That is why I wondered if a uncompressed backup solution would be better, although I do like the simplicity of Deja Dup.

Thanks again.

Teeleef

---

### Post by ratcheer on 2012-04-18
I am pretty sure DejaDup will do what you need, then.

It is always best to test your backups. Why don't you pretend like you had such a disaster. Just install a fresh copy of Ubuntu into a testing partition. Then run a DejaDup restore to this test installation. Find out for yourself exactly what it does.

I should do that myself, heh heh.

Tim

---

### Post by Roasted on 2012-04-19
Deja Dup sounds like it'd be an easy painless way for you to get your Documents backed up. For fun, do what ratcheer said. When I first set up Deja Dup, I didn't just set it and "okay let's just assume it works" and walk away... no, I tested it. Around that time my mother had gotten a new computer, so I decided she'd be a good test. I Deja Dup'd her /home to my external, then restored it to the new install. Her stuff was still on her old computer, of course, but I knew I could restore it to the blank fresh install on the new system and it be a decent test. Sure enough, it worked great.

I suggest you Deja Dup your Documents folder, and then restore it to another location, such as /home/Desktop/Test or something. Just make sure it dumps your Documents back in the new location effortlessly.

Enjoy!

---

### Post by teeleef on 2012-04-19
Thanks Roasted....

I tried your restore option to another folder and that worked fine.  In many ways it eased the fear that most people have should the backup data get either corrupted or fail due to human error.

I think Deja Dup will suit me fine and for extra peace of mine a second backup of important data would seem to be sensible.

Thanks again.


Teeleef

---

