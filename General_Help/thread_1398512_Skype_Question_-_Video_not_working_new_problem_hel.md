---
title: "Skype Question - Video not working new problem help!"
date: 2010-02-04
forum: General Help
---

### Post by x C0MMAND0 x on 2010-02-04
Main problem : I can not see incoming video on Skype.

Okay, so I have Skype installed, and it has worked fine in the past.  I have been able to chat with my girlfriend on it.  We can see each other and both talk.  I haven't used it in probably 3 or 4 months.  I tried to use it last night and for some reason, I could not see her on the video.  It would just show up as a white box where the video should be.  She could see me, and we could hear each other.  I already had her test with somebody else to check if her video output was okay, and it worked just fine.

I read something that Cairo Dock could somehow be affecting it, but I haven't tested this theory.  I can't see how the two could be related.  Does anybody have any ideas?

---

### Post by x C0MMAND0 x on 2010-02-05
Any ideas?

---

### Post by tviviano on 2010-11-13
I'm having the same issue.  Any ideas?

---

### Post by tviviano on 2010-11-13
Oh yeah, I'm using Ubuntu 10.10 with the latest skype from the repository.

---

### Post by sohlinux on 2010-11-14
sounds like a missing or corrupt lib or user directory, usually a reinstall will fix it

close skype

sudo apt-get remove skype

rename your skype directory , you will find it in /home/username/.Skype/

cd /home/username/

sudo mv .Skype .Skype_bk 

sudo apt-get install skype

---

