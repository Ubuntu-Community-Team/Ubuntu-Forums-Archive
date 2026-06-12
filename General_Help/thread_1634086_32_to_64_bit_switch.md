---
title: "32 to 64 bit switch"
date: 2010-11-30
forum: General Help
---

### Post by jquis8411 on 2010-11-30
Back story is I'm changing a mobo and cpu in an older Ubuntu box and switching from 32 to 64 bit both 10.04. My question is is there a way to move my 32 bit  thunderbird, firefox profiles to 64 bit. Some ideas preserving all my samba, ssh, sane etc, *sigh* Would be great too. In my head I was thinking backup ,then restore haha oops TY

---

### Post by pbpersson on 2010-11-30
Is your home partition separate?  If so, you can get a snapshot of your current packages, preserve your home partition, then do a fresh install of 64-bit Ubuntu, then use the snapshot to re-install all the packages, then because you have the same home partition you will have all the same configuration settings.

The beauty of Ubuntu is that all the configuration files are plain text so it should not matter...in theory

---

### Post by jquis8411 on 2010-11-30
No its not a separate partition (unfortunately) but I like what you are saying. Couldn't I just backup my home folder, then manually put all the config files back?

---

### Post by iponeverything on 2010-11-30
> **jquis8411 said:**
> Back story is I'm changing a mobo and cpu in an older Ubuntu box and switching from 32 to 64 bit both 10.04. My question is is there a way to move my 32 bit  thunderbird, firefox profiles to 64 bit. Some ideas preserving all my samba, ssh, sane etc, *sigh* Would be great too. In my head I was thinking backup ,then restore haha oops TY

I have never seen anything 32/64 bit specific in an application profile or application configuration file.

---

### Post by pbpersson on 2010-11-30
> **jquis8411 said:**
> No its not a separate partition (unfortunately) but I like what you are saying. Couldn't I just backup my home folder, then manually put all the config files back?

Yes, I would think so - backup your home directory, save a snapshot of all your applications - then blow away your entire machine - re-partition your drive so your home partition is separate (so you never have to go through this again).  Then do a fresh install of the new 64-bit system, use the application snapshot to easily install all the same packages, then restore your home directory.

Now.....I am not quite sure how that will all work but it certainly sounds like an adventure.  :)

---

### Post by dcstar on 2010-11-30
> **jquis8411 said:**
> No its not a separate partition (unfortunately) but I like what you are saying. Couldn't I just backup my home folder, then manually put all the config files back?

If you want to waste time doing something like that rather than creating a separate /home partition so you never have to this again, yes.

Search out the instructions for a separate /home, you will thank yourself in the future once you do this.

---

### Post by jquis8411 on 2010-12-01
Thanks for the advice guys, It certainly will be an adventure. I'm trying to find a few hours to get this started and Ill report back. A seperate /home partition is a definate must. My other Ubuntu comps have them this is just an old "before I knew better" install.

---

### Post by jquis8411 on 2011-02-19
I forgot about this thread. I wound up making copies of my mozilla profiles and the config files of the important programs, wiped out the old installation and then copied the old config files into the fresh 64 bit install. It worked like a charm. Thanks for the help guys.

---

