---
title: "livecd problems"
date: 2010-02-24
forum: General Help
---

### Post by willedoit on 2010-02-24
looking for some help. Iam interested in installing unbuntu, but wanted to run the livecd to make sure the system could handle it. but the live cd stalls and gives:

scsi_id[2580]: can't open /etc/scsi_id.config i/o error
scsi_id[2606]: can't open /etc/scsi_id.config i/o error
init: rc-default main process (2685) terminated with status 127

as if it is apparent I'm new to Unbuntu. What gives?

Itried dropping back from Ubuntu 9.10 to 9.04 still no luck

---

### Post by mörgæs on 2010-02-25
Welcome!

Good to see that you are trying various releases. It is usually the quickest solution to a given problem.

You could also try 10.04:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is still in alpha, but it behaves well on all machines where I have tried it.

---

### Post by willedoit on 2010-03-05
Well folks I must say the help response has been overwhelming!!!! Thanks

---

### Post by mörgæs on 2010-03-05
Without more information from you it is not easy to provide any help.

How did 10.04 work? 
Have you tried other distros, like Puppy Linux? 
On which hardware are you running? Especially, which drives are there? SCSI, it seems, but let's have some details.
Are you trying to set up a RAID?
Anything else of relevance...

---

### Post by willedoit on 2010-03-05
well at least someone responded.
sys specs:
   pentium 4 cpu
   1 gig mem
   80 gig scsi drive
  ati graphic card

[I]Its a Box I aquired on the cheap with Vista- just wanting to try out Linux

No As I write this I am burning 10.04 livecd to try out---Just figured If 9.10 8.04 couldn't handle the sys why push my luck.
[/I] 
Both livecd work on newer hardware so I think the cds are good

Thanks for responding

---

### Post by willedoit on 2010-03-07
Well I've now tried 10.04 and it hangs at the ubuntu title screen so i'm still in search of a installable version of linux. I did tryout the 10.04 version on a newer laptop and liked the experience. but I fear the bloat factor is fast overrunning Mr. Torvalds ideals. 

P.S. can someone clue me into what user Id and password is needed  to logon to Ubuntu - i was trying to see how it would react on an older laptop (xp, celeron, 512 meg mem---yeah yeah paper weight but she severed me well for many years) and couldn't get by the logon screen b4 the install screen . I tried no user ID and ubuntu for the password - tried blanks in both etc no luck. I thought I read somewhere that the default was ubuntu/unbuntu or blank/ubuntu but it didn't work for me. for what its worth i didn't get prompted for the log on the newer system. So I'm definitely cornfoosed.

hp desktop
1 gb mem
pentium 4
onboard ethernet
older ati video card

hep me hep me please

---

### Post by mörgæs on 2010-03-07
If you still can't get Ubuntu working on your new machine try opening a new thread with 'SCSI' in the title, explaining your findings. I have no experience with SCSI, sorry. Absolute Beginners Talk has the most activity.

Have your tried username = ubuntu and a blank passwork?

I agree on the bloating :-( To aviod a lot of unnecessary stuff I mostly install minimal Ubuntus:
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
There is some bitching in this thread, but it is still worth reading. Just remember to use a network cable while installing.

512 MB memory is a great machine with a minimal 9.04. It works fine on my Compaq with 192 MB.

---

