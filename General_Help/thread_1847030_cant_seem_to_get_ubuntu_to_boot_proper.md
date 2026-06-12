---
title: "cant seem to get ubuntu to boot proper"
date: 2011-09-20
forum: General Help
---

### Post by rollinsmoke on 2011-09-20
hi i was wondering if someone could help me get my ubuntu back up and going heres the deal i installed 6 gigs of ram 2 4 gig patriot 800mhz and 2 1 gig stcks of kingstons value ram 533mhz it was running fine with the 4 I installed the two more and it went haywire i take them out and still same thing it'll load but only the desktop icons in a really low bit color scheam show up and a error message that states 


GConf error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: GetIOR failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus))



im sure its something i set wrong within the bios or something hopefully not too devestating but i apprecieate anyones help on this hopefully i can have my system again i just got it setup to run netflix flawlessly thanks again

---

### Post by rollinsmoke on 2011-09-20
anyone have any insight its driving me nuts running off a live cd

---

### Post by rollinsmoke on 2011-09-20
welp hate to do it but it might do me some good on some other minor issuses i was having but i guess im going to back up and reinstall thankfuly i can still get to all my files and such man its gonna be a long night

---

### Post by rollinsmoke on 2011-09-20
the more and more i try to back up what ive got the more and more i realize i really dont want to go this route if anyone has anything that could help even if its just a point in the right direction id greatly apprentice the help

---

### Post by rollinsmoke on 2011-09-20
update:
all other users are fine i dont know why i didnt check that but they all work flawlessly anyone have any ideas they'd throw my way i know its late here but hopefully with 100 some odd viwes someone will know something towards my problem

---

### Post by rollinsmoke on 2011-09-20
going on day two and no replys still same problem

---

### Post by rollinsmoke on 2011-09-20
i looked into this all night i found plenty of bug reports about it but no fixes so is there any it'd sure be nice to know if there were or not

---

### Post by blueridgedog on 2011-09-20
> **rollinsmoke said:**
> i installed 6 gigs of ram 2 4 gig patriot 800mhz and 2 1 gig stcks of kingstons value ram 533mhz

I suspect the value RAM can not run at 800mhz.  Do you know what your system memory is clocked at?  I suspect that you will need to run only the patriot.  I do not get your math though, two four gig and two one gig is ten gig.  If you want to run the value ram, you will need to go into the bios of your system and down clock the RAM speed.

When you reply many times to your own post, other forum members only see the post count going up, so the assumption is that someone is helping you.

---

### Post by rollinsmoke on 2011-09-20
my bad not too forms savvy but yea i mistyped that i have 2x2gb of patriot and 2x1gig of kvm i have it under clocked to match the kvm at 400mhz and other users run fine no problems so im thinking its not the hardware

---

### Post by blueridgedog on 2011-09-20
Your system may have shared video memory and the underclocking of the RAM causes the performance issue you speak of, or the front side bus of the CPU is tied to the clock rate of the RAM, so underclocking the RAM caused the system to get very slow.  

I would boot the patriot RAM at 800 and then at 533 (no other RAM).  If the problem persists with the lower clock speed then that is the issue.

---

### Post by rollinsmoke on 2011-09-20
but how is it i can still load into other users with no problems it runs fine

---

### Post by rollinsmoke on 2011-09-20
running four gigs at 667mhz and proper timings with no change it has to be somethin else if someone could point me in the right direction to what may be causeing this i could probably figure the rest out through google

---

### Post by patryk77 on 2011-09-20
There is an EDIT button on your posts. Please click it sometimes, it feels unloved. (Smartass way of saying, please don't quintuple-post) ;)

---

### Post by blueridgedog on 2011-09-20
> **rollinsmoke said:**
> but how is it i can still load into other users with no problems it runs fine

So, you can boot and log in as a given user and it has an issue, then log in as another user and it works fine?  In that case I suggest you boot as the working user and delete your gnome configuration files:

sudo rm -rf /home/baduser/.gnome

Repeat for .gnome2 .gconf .gconfd where "baduser" is the user account that is not working. 

**Note:  Be Careful!  "sudo rm -rf" is a dangerous command...**but you will need to use sudo as you are trying to delete another user's files, so you will just need to be careful.

Note2:  You will lose your desktop settings and have a clean plain setup.  An alternative is to make a new user account and use that one as your account.

If your additional user account is not in the admin group and can't sudo, they you may need to do it as your broken user.  In that case you will not need sudo.

---

### Post by ewtrowbr on 2011-09-26
This post saved me. Thanks a lot!

Erich

---

