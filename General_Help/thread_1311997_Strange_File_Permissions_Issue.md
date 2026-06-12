---
title: "Strange File Permissions Issue"
date: 2009-11-02
forum: General Help
---

### Post by panicy on 2009-11-02
Hello everybody!

I wrote a simple shell script today, and for some reason decided to check and see if it was able to run from another account (dummy user account, and under different group).  When I ran it, it gives permission denied.  Ok, so I check the permissions and everyone had "x" permission.  Wierd.  After some guessing and checking I've found that the only time it ran  is if it had r AND x perms (or all three).  Only under these circumstances will a file execute.  x is not enough for ANYONE to run the file even the creator of it... I dont understand.  Granted, the code for the shell script is beyond easy, but its the point.  You should have to give r permission to just let anyone run it right?  If it was complex code you wouldn't necessarily want them to see the source code.  I guess what im saying is that I want to have rwx--x--x so I can rwx but everyone else can only x.  Im frustrated...  Someone please enlighten me...

btw on 9.10 if that makes a difference (maybe known bug that I dont know about...idk)

---

