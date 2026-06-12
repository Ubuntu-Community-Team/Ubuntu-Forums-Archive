---
title: "emulator to play old school"
date: 2010-05-25
forum: General Help
---

### Post by Ready2DropWin on 2010-05-25
I was wonder what the best emulator is for play station one for unbuntu.

---

### Post by WorMzy on 2010-05-25
I use ePSXe.

---

### Post by Ready2DropWin on 2010-05-25
I tried to use wine to stat the .exe and i got this error

```

err:module:import_dll Library zlib1.dll (which is needed by L"Z:\\home\\darkness\\Desktop\\epsxe170\\ePSXe.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\darkness\\Desktop\\epsxe170\\ePSXe.exe" failed, status c0000135

```

---

### Post by Drizzt611 on 2010-05-25
ePSXe is slow (at least for Final Fantasy VII it is).
pSX is excellent and you do not need to download any plugins for it, but last I checked it was no longer compatible with ubuntu after the wonderful 10.04 changes...

---

### Post by Ready2DropWin on 2010-05-25
Thats funny, thats the game that I wanted to play, and I am using 10.04, so what am I to do? Is the another emu out there that I can use?

On another note, does this mean that I don't have mean that I don't zlib1 installed? If so how do I install it.

---

### Post by WorMzy on 2010-05-25
I've never had much luck with v1.7.0 on either Linux or Windows. Try 1.6.0 instead. Or try the emulator Drizzt suggested, pSX.

---

### Post by Ready2DropWin on 2010-05-25
I tried 1.6.0 with wine and got this

```

err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\darkness\\Desktop\\ePSXe\\ePSXeCutor.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\darkness\\Desktop\\ePSXe\\ePSXeCutor.exe" failed, status c0000135

```

---

### Post by Ready2DropWin on 2010-05-25
I am trying pSX right now, it looks like it might work with wine.

---

### Post by tatsuyame on 2010-05-25
> **Ready2DropWin said:**
> I am trying pSX right now, it looks like it might work with wine.
You shouldn't have to use wine for ePSXe, there is a linux executable for version 1.6.0.  Also, you don't need to use the executor frontend, ePSXe already has a GUI.

---

### Post by WorMzy on 2010-05-25
Weird. I don't get that error. I've uploaded my version [which I know to work fine]("http://www.ubuntu-pics.de/bild/70488/desk_1_028_pb5mLO.png"). I've left out the bios file since sharing that is illegal, but there's a bunch of plugins in there that I've collected over the years.

[http://www.megaupload.com/?d=9A52GTA8]("http://www.megaupload.com/?d=9A52GTA8").

For the record, I use wine to run ePSXe because the Linux version depends on an obsolete version of libgtk. The windows version works fine under wine anyway, I've never noticed any performance issues.

---

### Post by tatsuyame on 2010-05-25
> **WorMzy said:**
> For the record, I use wine to run ePSXe because the Linux version depends on an obsolete version of libgtk. The windows version works fine under wine anyway, I've never noticed any performance issues.
Oh, thanks for the clarification.  I was wondering why it wouldn't start up in my test vm.

---

### Post by Ready2DropWin on 2010-05-25
Thank you for that upload, the version that you gave me run fine. Not sure why the one that I download didn't work maybe it was a bad download.

---

### Post by Ready2DropWin on 2010-05-25
Now I just wish I could get my logitech controller to work, and figure how to load a game now that I have the bios.

---

### Post by Ready2DropWin on 2010-05-29
When I try to set up my controller in epsxe, its fighting with my desktop environment, like when I try to set up the sticks, it won't read in the epsxe setup because the courser is moving on my screen. Any ideas?

Thanks

---

