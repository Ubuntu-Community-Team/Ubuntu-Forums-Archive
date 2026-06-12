---
title: "Thunar(?) forgets file type."
date: 2012-05-16
forum: General Help
---

### Post by bryncoles on 2012-05-16
Greetings fellows.  

I have an odd problem.  I'm running Xubuntu 12.04, and I have a Western Digital 1TB external hard drive for backups.  

Now, every now and then Xubuntu (perhaps Thunar) forgets what the file type is.  It also did this in 11:10 -- but only about three times.  It mostly happens to folders.  They lost the folder icon, and become blank squares.  If I double-click them, Thunar asks what program I want to open them with.  If I rename them, they remember they are folders, and I can open them normally.  There doesn't seem to be any data loss -- the contents of the folders is still there as far as I can tell.  

I have run the tests through Palimpsest, and it says the drive is healthy, not about to fail.  I have searched the forums, and found [this](http://ubuntuforums.org/showthread.php?t=874446) post which seems to describe the same problem, but alas attracted no commentary from the good people here.  

Anyone got any ideas?

*** edit ***

Oh yes, I also got a crash report from 'tumblerd', whatever that is when I was busy renaming the files this time around.  Don't know if that's significant...

---

### Post by rai4shu2 on 2012-05-16
Maybe you could help these guys out:

[https://bugzilla.xfce.org/show_bug.cgi?id=8004](https://bugzilla.xfce.org/show_bug.cgi?id=8004)

---

### Post by bryncoles on 2012-05-16
I'll keep an eye, and if the crash happens again I'll let them know.  It's a little hard to gather relevant bug-fixing information though, cause the crashes are so random!

---

### Post by bryncoles on 2012-05-21
Well, looking at the report [ulr=https://bugzilla.xfce.org/show_bug.cgi?id=8004]here[/ulr], I disabled thumbnailing in Thunar.  So far, no repeat of this behaviour.  Doesn't help me provide info to get the problem fixed, but does seem to have helped me out.  

I shall tentatively say the problem is 'solved'... Cheers rai4shu2 for the lead!

---

