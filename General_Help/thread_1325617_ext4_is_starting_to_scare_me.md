---
title: "ext4 is starting to scare me"
date: 2009-11-13
forum: General Help
---

### Post by nerdy_kid on 2009-11-13
i just made the mistake of reading this:  [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579)

does this effect me at all?  cause if it does i have a stupid reinstall to do... why the heck did they put ext4 as default filesystem if it has bugs like this?????

i will *freak* if my files get ruined....

and on a side note, once a fix gets released for this bug, will it just be a simple upgrade via apt-get or will it be a whole reinstall anyway?

---

### Post by arnab_das on 2009-11-13
> **nerdy_kid said:**
> i just made the mistake of reading this:  [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579)

does this effect me at all?  cause if it does i have a stupid reinstall to do... why the heck did they put ext4 as default filesystem if it has bugs like this?????

i will *freak* if my files get ruined....

and on a side note, once a fix gets released for this bug, will it just be a simple upgrade via apt-get or will it be a whole reinstall anyway?

running ext4 and i did get those errors. but dont worry. its really really stable and i mean it. i think i've as of now fallen in love with karmic more than i did with jaunty!

---

### Post by nerdy_kid on 2009-11-13
> 
running ext4 and i did get those errors
 

you did get the errors?  do you mean youve had file corruption?

i am seriously concerned about the preservation of my files....

I am kinda still deciding between jaunty and karmic...

---

### Post by arnab_das on 2009-11-13
> **nerdy_kid said:**
> you did get the errors?  do you mean youve had file corruption?

i am seriously concerned about the preservation of my files....

I am kinda still deciding between jaunty and karmic...

go for karmic and update it. there have been some bug fixes after the official release. also u'll find the errors progressively thin out in due time. i used to get LOADS of filesystem and kernel errors earlier with the new karmic release but now, no error notifications at all!

believe me i had messed up karmic big time! but to my utter surprise, it didnt let me down at all, i just reinstalled the default ubuntu-desktop package and everything worked perfectly again. i cant remember any crashes on my system in the past 2 weeks.

karmic's faster than jaunty and even if u install jaunty now, u'd probably have to install about 300-400MB of additional software update/bug fixes.

go for karmic.

---

### Post by jhb1608 on 2009-11-13
That's why you have to backup files. I always burn stuff in CD :).

---

### Post by ranch hand on 2009-11-13
I have been running ext4 since before Jaunty was released with no problems at all.

Have you looked at;

[https://launchpad.net/+search?field.text=ext3](https://launchpad.net/+search?field.text=ext3)

and seen how many of them were filed this year inspite of its being around for years?

Sorry, just getting tried of off beating this dead horse.

---

### Post by doas777 on 2009-11-13
I haven't had any problems thus far (as i knock on my wooden bookshelf) and have been using it since April with Jaunty.

I am a little disturbed with how quickly the diskcheck disappears in karmic when it shows up in usplash though. it'll blink 6%, then 8%, just before the GDM loads. no idea if it is finishing.

---

### Post by arnab_das on 2009-11-13
> **doas777 said:**
> I haven't had any problems thus far (as i knock on my wooden bookshelf) and have been using it since April with Jaunty.

I am a little disturbed with how quickly the diskcheck disappears in karmic when it shows up in usplash though. it'll blink 6%, then 8%, just before the GDM loads. no idea if it is finishing.

maybe u could try removing the splash screen (via the startupmanager software) and see whats going on behind the scenes, just to be sure.

---

### Post by slumbergod on 2009-11-13
EXT4 is working perfectly for me so far with no issues at all. Even converted an archive drive from EXT3 to EXT4 - no issues there either.

---

### Post by nerdy_kid on 2009-11-13
ok, thanks a bunch for all the replies!
guess im being parinoid (like usual) :D

---

### Post by mosaic2s on 2009-11-14
Friends,
I have ext3 file system 8.04 installed in one partition while I installed 9.10 in the next partition using ext4.

I would like to read ext4 partition from ext3 file system while booted in 8.04. Is that possible ?

---

### Post by ranch hand on 2009-11-14
Unfortunately not.  Make sure you have "backports" uncommented on your sources.list and hope that they come up with a fix.

I have the same problem and have to go the other way with data.  It is a bummer.  Hardy is a great OS.

Lenny (Debian stable) does not either even though it uses a newer kernel than 8.04.  I do have a Debian "respin that does though.  PhatDebian uses the 2.6.30 kernel and has no trouble reading my ext4 partitions.

---

### Post by arnab_das on 2009-11-14
> **mosaic2s said:**
> Friends,
I have ext3 file system 8.04 installed in one partition while I installed 9.10 in the next partition using ext4.

I would like to read ext4 partition from ext3 file system while booted in 8.04. Is that possible ?

i guess you could create a virtual os. then  u could have any filesystem running simultaneously with apparently incompatible ones.

---

