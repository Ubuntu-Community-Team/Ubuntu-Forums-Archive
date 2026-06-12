---
title: "How can ubuntu so utterly fail?"
date: 2009-10-13
forum: General Help
---

### Post by Aeolun on 2009-10-13
I'm not quite sure how I do it, but I manage to crash my ubuntu installation within a few minutes of using it.

I installed Ubuntu 9.04 64-bit on my GX700 MSI laptop but it simply won't work.

It isn't that I can't install it. That process works fine, and I get to login and all. The problem is after that. I first get the screen telling me my battery is old and has low capacity. Thanks for telling me something I have never noticed before... The disable in the future button doesn't seem to work either. Very good for the very first thing the user sees. :confused: 

That isn't really a problem though. The problem is that the update manager kicks in after that. I thought, great! New updates! And promptly continued by clicking the update button, enter my root password and install the whole ********, this takes almost no time at all with my internet connection (even though it's 140 mb).

The moment I do really get frustrated is when the update manager tells me something went wrong and I get the really helpful messages in the command line.  I don't know that it was, and I didn't really care. I thought it would be ok if I just clicked continue.

Turns out that wasn't right. I can't access aptitude at all anymore. Not from the gui or from the command line. WTF?! I have only installed Ubuntu for a few minutes and it becomes quite unusable for any nontechnical user :S

Now I am a quite technical user though, and I'm still willing ot give it a try, but I have no clue how to solve this problem. I found a solution on the internet, but it didn't work, it seems my filesystem has turned read only while updating... I don't know how.

Please help me... In the meantime I'll just install MS windows,

Yes, I'm somewhat frustrated, please bear with me. Such a thing always seems to happen when I install Ubuntu once in a while. I always have to conclude that it just isn't user friendly yet. Mainly because I always encounter some obscure error within a few minutes of using it that no nontechnical user can EVER fix. Much less understand.

Read only filesystem FTW...:(

---

### Post by Aeolun on 2009-10-13
As an addition note. I can't even boot my computer anymore now. It just shows a black screen with a blinking cursor the first time. The second time it went into shell mode to tell me I had to manually run fsck. I tried, but it told me my filesystem wasn't ext2. Sure enough, it was ext4, but I couldn't find any easy way to change it... (an option for fsck, not the filesystem).

EDIT: I'm reinstalling now, trying ext3 with a full automatically configured hard drive setup (use the complete disk).

---

