---
title: "I need help in ubuntu 9.04"
date: 2009-07-08
forum: General Help
---

### Post by dbowler on 2009-07-08
How do you install directx 9 in wine. I tried it before, but it didnt work. I found a video on [www.youtube.com/watch?v=mlbVN26JaG8]("http://www.youtube.com/watch?v=mlbVN26JaG8") how to do it, but i dont know what to do please help me!

---

### Post by t4thfavor on 2009-07-08
Download it, Launch the redistributable from the command line with 

```

wine dewhateveritscalled.exe

```

Then extract the files somewhere you can find them.

Then run the dxsetup.exe

```

wine dxsetup.exe

```

If you need more help feel free to ask.

---

### Post by CatKiller on 2009-07-09
Installing DirectX in Wine seems like a really bad plan to me. Wine already has its own implementation of DirectX built-in. Installing DirectX over the top seems like it will just lead to severe breakage.

---

### Post by s.fox on 2009-07-09
Hi,

What application are you trying to run?   You could also search through the [WINE subsection]("http://ubuntuforums.org/forumdisplay.php?f=313") of this forum :)

-Silver Fox

---

