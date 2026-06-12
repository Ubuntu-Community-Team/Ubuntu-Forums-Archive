---
title: "No space left after a backup using &quot;Backup-Manager&quot;"
date: 2012-09-19
forum: General Help
---

### Post by Mensik on 2012-09-19
Hi guys,

I'm forced to ask for your help, since I've tried anything I could to resolve my problem.  Here's the deal : yesterday evening, I decided to make a backup of my files using "backup-manager".  Since it took a while, I decided to go to bed and let it run during the night.  This morning, when I woke up, a message appeared on the screen, telling me that there were only about 700 Mo of free space left on the computer.  Everything was low and my backup wasn't even complete (it weights about 110 Go).  Since the .tar.gz file wasn't complete, I decided to put in the trash, but when I did so, it didn't appear in it.  I couldn't even empty the trash, since my backup file wasn't even appearing.

I thought it was strange and decided to reboot, to see if it could help.
Bad idea.

Here are screenshots of what it looked like, while booting.

[First]("http://antoinemalette.com/ubuntu/1.jpg"), a purple screen, which is normal.  Then comes [this]("http://antoinemalette.com/ubuntu/2.jpg") warning box.  Then [this]("http://antoinemalette.com/ubuntu/3.jpg") list, where four options are offered.  The first one (booting in low graphics mode) is set by default.  By choosing it, [this]("http://antoinemalette.com/ubuntu/4.jpg") last screen appears.  From there, nothing moves.  I'm stuck on this screen.  I can't even press "ok", since the cursor isn't even visible.  I try to hit the ok button by moving the mouse everywhere, and nothing works.  Not even by hiting "enter" or "tab".

I feel a bit angry because I did my backup precisely to avoid a crash like that...
I hope there's something I can do to get my computer back...

Thanks a lot for your help guys !
Antoine ;)

---

### Post by jerrrys on 2012-09-20
You have the option to go to console in one of your pics, try to delete your trash from there.

rm -rf ~/.Trash/*

---

### Post by Mensik on 2012-09-20
Hi jerrrys !

Thanks for your help.
I tried but nothing worked.  I went to the console (ctrl-alt-F1) and tried :

[HTML]df -h[/HTML]Here's the [result]("http://www.antoinemalette.com/ubuntu/5.jpg").
Sorry, it's French...

---

### Post by jerrrys on 2012-09-20
Yep your max out, try this in console:

apt-get clean

That should get you enough space for a normal boot.

---

### Post by Mensik on 2012-09-20
Hey jerrrys,

I tried it already.
Doesn't make anything.  I even tried the **sudo apt-get autoclean** and it didn't work either.

I'm making a complete back-up on my live session CD and will probably have to reinstall my whole Ubuntu... :s

I'll let you know if there's any changes.
Thanks again mate,

Mensik

---

### Post by Bashing-om on 2012-09-20
Mensik;  
If it has been a while since any house cleaning:
Delete the old log files in /var/log/
These old files can consume huge amounts of disk space.

That may get you some much needed space.

[INDENT][INDENT]hth <==BDQ

[/INDENT][/INDENT]

---

