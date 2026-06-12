---
title: "WineHQ 1.1.28 and DirectX Based Games!!"
date: 2009-09-19
forum: General Help
---

### Post by abhishekdey1985 on 2009-09-19
Hi, I have installed WineHQ and it executes almost all the applications of windows excluding Microsoft's Office, media players, etc.

WineHQ also claims to emulate DirectX based games on Ubuntu. I tried executing Crysis and Far Cry 2 but it failed. The runtime exception which it throws says that it cannot find MSVCR80.dll not found.

How can i include the Windows System32 folder into the winehq so that all the applications refer to the required DLLs?

Please Help!!

Thanx in Advance!!

---

### Post by NoaHall on 2009-09-19
Can I just ask, are you serious? Crysis, a high end game, on wine? Seriously? No. It doesn't work very well at all, it's not worth it. You'll have to stick to windows for that.

---

### Post by XCan on 2009-09-19
As NoaHall said, such advanced games as Crysis or FarCry 2 will have trouble getting to work properly, that of course doesn't mean that Wine can't run new advanced games, there are several which are fine. Anyway, as always you should check their appdb for tip on how to get your app working: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880) [http://appdb.winehq.org/objectManager.php?sClass=application&iId=8522](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8522)

---

### Post by solidblu on 2009-09-19
If you want you can try Cedega (*hides from the hisses of hard core wine users*)


They have added support for DirectX to wine and their support for games are usually a step ahead of wine.  It is not free, but it is not expensive.

[http://www.cedega.com/gamesdb/index.html?search=far+cry&join_operator=AND&submit_keyword_search=Search](http://www.cedega.com/gamesdb/index.html?search=far+cry&join_operator=AND&submit_keyword_search=Search)

---

### Post by shae on 2009-09-19
That error sounds like it is missing some dotnet dll file.  Check winetricks for ways to install that.

---

### Post by solidblu on 2009-09-19
I think shae is write.

try:
```

sh winetricks vcrun2005sp1 vcrun2005

```

I found it in the forums when someone else had a similar issue.


[http://ubuntuforums.org/showthread.php?t=845750](http://ubuntuforums.org/showthread.php?t=845750)

---

### Post by abhishekdey1985 on 2009-09-20
First of all, Thanx for helping me guys!. 

I didnt know about the performance issue that culd incur on WineHQ. How about cedega, will it also have the same performance issue as WineHQ?

---

