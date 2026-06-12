---
title: "NTFS support"
date: 2006-04-04
forum: General Help
---

### Post by _linux_ on 2006-04-04
I have Windows XP installed on another hard drive, and want to access it sometimes. Does anyone know how to install NTFS support?

---

### Post by yager on 2006-04-04
Go here for the official answer.

[https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

You will only have Read Only permission as NTFS writing is not officially supported.

---

### Post by FryerFox on 2006-04-04
Here are the directions for enabling NTFS write support on your drive:

[http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

But it is *experimental*, or so they say every time I have read about it.

---

### Post by webhed on 2006-04-05
[QUOTE=_linux_]I have Windows XP installed on another hard drive, and want to access it sometimes. Does anyone know how to install NTFS support?[/QUOTE]

Reading NTFS is no problem. Writing to NTFS is risky at best. You will want to do some searches on the mount command both in google and the man pages, as well as read up on the /etc/fstab file. Theres some cool stuff you can do.
:D

---

### Post by _linux_ on 2006-04-05
It's okay. I already found out how to mount and read NTFS disks from the Ubuntu Starter Guide.

---

### Post by OneBuntu on 2006-04-05
[QUOTE=_linux_]It's okay. I already found out how to mount and read NTFS disks from the Ubuntu Starter Guide.[/QUOTE]
So what?!?!?

Linux has been able to read NTFS for almost 10 years.

The question is,... can you write to NTFS from Linux.

Yes you can, and you don't know how to,... oh well,... why did you ask a question everyone knows the answer to anyway.

---

### Post by joshrobinson on 2006-04-05
[QUOTE=OneBuntu]So what?!?!?

Linux has been able to read NTFS for almost 10 years.

The question is,... can you write to NTFS from Linux.

Yes you can, and you don't know how to,... oh well,... why did you ask a question everyone knows the answer to anyway.[/QUOTE]

ive used linux ntfs writing in the past and it gave me problems, what you mentioned above, is that safe? i guess i can just make a spare ntfs to mess around on to make sure it works and i dont lose anything

before the ntfs writing i used was horribly slow..

also i can edit my fstab and make the ones i dont want them to write to read only and they wont get affected right?

---

### Post by OneBuntu on 2006-04-05
[QUOTE=joshrobinson]is it safe?[/QUOTE]

NTFS-FUSE is safe. 

The other method Captive-FUSE has some question marks when copying large files.

[QUOTE=joshrobinson]is it horribly slow..[/QUOTE]

NTFS-FUSE is fast.

Captive-FUSE is slow (for large files).

[QUOTE=joshrobinson]also i can edit my fstab and make the ones i dont want them to write to read only and they wont get affected right?[/QUOTE]

Yes.

NTFS-FUSE has one very strange feature. It can only write 12 files into any directory it creates. So copying lots of files in nested directories is a problem.

Otherwise it works fine.

---

### Post by joshrobinson on 2006-04-05
but i wont lose any data? thats my only problem

---

### Post by OneBuntu on 2006-04-05
[QUOTE=joshrobinson]but i wont lose any data? thats my only problem[/QUOTE]
NTFS-FUSE is totally safe.

---

### Post by OneBuntu on 2006-04-06
[QUOTE=OneBuntu]NTFS-FUSE is totally safe.[/QUOTE]

Well: [color=red]"Actually it's close to full write support and reliability shouldn't be a problem either"[/color]

Szakacsits Szabolcs <szaka@sienet.hu> -- Linux NTFS developer (4 days old).

---

### Post by mcwtlg on 2006-04-06
I have been using NTFS-FUSE for a few weeks now and have had no problems.  The how to in Tricks and Tweaks section of the forum is very well written.

I do not know about the 12 file limit, since I normally am only copying/deleting  a few files at a time.

With this addtion, I am a very happy camper with regards to Ubuntu Linux.  I think back to all my failed attempts (starting with Red Hat 6, Suse 8, XandroS 3, Linspire 5, Mandrake, Debian, et al) with Linux, Ubuntu is a gift from heaven.  It detected ALL my hardware (including my SATA drive, scanner, BOTH printers, my card reader, web cam) and if I have to complain at all it is the fact that I still cannot get my Tungsten E to synch properly (it does most of it, but hangs when trying to synch the photos) and the two apps I need in Windows either do not work or work erraticly in WINE (not that this is a big deal, mty wife still uses Windows, and I still have to log on to do any updates for her).

The only problems I have ever had with my install was when I compiled the most current Nvidia drivers and then installed XFCE ... somehow X got botched, but the forums gave me the clue I needed to fix it.  10 minutes later I was back in.

Ubuntu rules.

Thank you God!

---

### Post by OneBuntu on 2006-04-06
I have had absolutely no problems with NTFS-FUSE either.

---

### Post by yager on 2006-04-07
[QUOTE=OneBuntu],... why did you ask a question everyone knows the answer to anyway.[/QUOTE]

I guess his being new to Linux is not a good enough reason for you?  

I am new, most of the people here are new to Ubuntu and Linux.  If everyone attacks the new people, there won't be more new people....  Your response is not going to help promote the growth of Ubuntu or Linux if you answer all new user questions as if they should check the 23rd chromosone of their personal DNA for the answer to any Linux question.  

As humans, we talk to communicate ideas and knowledge.  Some people like to ask questions and others like to dig up answers.  I personally like to dig up answers to other people's questions because that is how I learn a new operating system, program, system, facts, a city, a country, etc.  Could they have used Google, Yahoo, or even the forum search tool to answer their own question?  Sure...  Would I have had the opportunity to present a welcoming presence to a new user and also learn a few things about this new hobby I have adopted? NO.

Linux is not something that was built as a natural response to the drive to replicate our personal DNA and put right next to "nest building instructions".  If it were, it would be much more appealing to women. (Check out my tail feather baby)

Be helpful.  Not everyone is as smart as you are.  Share your knowledge and make the whole community bigger and better.  If you answer the same question from 1,000 new people, that would be great because there are 1,000 new people in our community.  If you chew out the new people, they will be less likely to ask questions, become frustrated with all of the small issues that they are dealing with and not join our community.

---

### Post by OneBuntu on 2006-04-07
"I am new, most of the people here are new to Ubuntu and Linux."

I don't believe that you are new. You just pretend to be.

Your response is not going to help promote the growth of Ubuntu or Linux,.... that's 4 sure.

Why didn't you put all that effort into helping?

---

### Post by kerry165 on 2006-04-28
Only just started looking at Linux (Ubuntu is my first and only view of it) and wanted to look at connecting to my WIn2K server.

The first search I found got me to connect using "smbfs" as the file type with the smb service. This does seem slow.

This thread mentions "ntfs" and "ntfs-fuse".

What are the comparisons like? Is one faster/more stable than the other?

The phrase 

> Warning! Ntfs writing support is still experimental! You should not enable it on production machines and/or volumes you don't have backups of. Proceed at your own risk!

is a worry. I am investigating if (and there are reasons behind this) multiple remote logins, each running a Wine to execute a current Win app that will access some data from a Windows machine. No this is not the end goal, but an investigation into pushing the limits in the use of the environments. And I am curious.

Kerry:-k

---

### Post by erikwithak on 2006-06-15
If its only set to read will i still be able to copy items out of the harddrive?

---

