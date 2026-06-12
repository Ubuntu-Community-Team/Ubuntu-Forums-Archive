---
title: "Extracting .PKG file"
date: 2010-07-31
forum: General Help
---

### Post by root-x on 2010-07-31
Does anyone know how to extract the files and contents out of a .pkg, A sony package file to be precise.

---

### Post by WorMzy on 2010-07-31
Try using fileroller (right-click -> extract here). You may need to install an xz package from Synaptic before you're able to. (Assuming that it's in xz format)

---

### Post by root-x on 2010-07-31
> **WorMzy said:**
> Try using fileroller (right-click -> extract here). You may need to install an xz package from Synaptic before you're able to. (Assuming that it's in xz format)

thanks ill try it out..

---

### Post by root-x on 2010-07-31
I cant get it to install or do i say i dont know how to is there a terminal command.

---

### Post by WorMzy on 2010-07-31
File roller should be installed by default.

Can you tell us where you downloaded this file from, then we can check it out and advise you on how to proceed.

---

### Post by root-x on 2010-07-31
> **WorMzy said:**
> File roller should be installed by default.

Can you tell us where you downloaded this file from, then we can check it out and advise you on how to proceed.

Its a playstation package file. Contains the modern warfare 2 patch, you see i want to mod it. Unfortunatly i cant see any release that can extract the files please.

---

### Post by root-x on 2010-07-31
When you download a file from the pc playstation store it saves a .XPD file to your computer. This file is used by the playstation network  downloader to download your content (game, demo, etc). I was messing around and noticed that if you open the xpd with a text editor it reveals that it downloads a pkg and extracts it. My theory is by changing the pkg url in the xpd and also some other info that we could use this tool to extract ps3 pkgs.

Example XPD:
Quote:



[Info]
EID=pngc
Desc=ã€Žã¾ã„ã«ã¡ã„ã£ã—ã‚‡ã€PSPÂ®ç”¨ã‚«ã‚¹ã ‚¿ãƒ ãƒ†ãƒ¼ãƒž
Size=247824

[File]
C=http://zeus.dl.playstation.net/cdn/JP9002/NPJA90054_00/awNJC8v74OLOMoR3FpL4YO3cq7MY1YXVfY1OyXM6e6Dp91UjH5 uAhPKyfsFFMla9T9WWhGJe6xfWfQTnDnIHkWxL7bXdwc1rt9yF G.pkg

[DrmPNPD]
AID=d6ff6e5107839a30
CID=JP9002-NPJA90054_00-MAINICHICT000001
LID=asksin@gmail.com
EPW=B196215E8EFE978DC16F51E0A5EB5A0D23515D705070C3 AE7A2750BDA5D7AE9BBE8CD1D753D60A27C8958D43E35AB5DA
KD=https://store.playstation.com/kdp.m
CA=https://store.playstation.com/cap.m

[DrmMGN]
T2=http://sclock.ww.np.community.playstation.net/mgntt/get

Got this information from a site.

---

### Post by WorMzy on 2010-07-31
In that case, I don't know what you can do with it. Run "file" on it*, and post the output here, and maybe we can suggest a package that will allow you to extract it's contents, but if it's packaged using an obscure algorithm, then there's not much hope. If there's a Windows application that can be used to extract it's contents, then you can try using that through wine.


*Open a terminal and run
```
file /path/to/the/file.pkg
```

---

### Post by root-x on 2010-07-31
Look whether you like it or not if you can help me get through this you will get money in your paypal lol.

---

### Post by root-x on 2010-07-31
> **WorMzy said:**
> In that case, I don't know what you can do with it. Run "file" on it*, and post the output here, and maybe we can suggest a package that will allow you to extract it's contents, but if it's packaged using an obscure algorithm, then there's not much hope. If there's a Windows application that can be used to extract it's contents, then you can try using that through wine.


*Open a terminal and run
```
file /path/to/the/file.pkg
```

Ok i greatly appreciate your help.

---

### Post by root-x on 2010-07-31
administrator@administrator-laptop:~$ file /home/administrator/Desktop/EP0002-BLES00683_00-MW2P000000000010-A0110-V0100-PE.pkg
/home/administrator/Desktop/EP0002-BLES00683_00-MW2P000000000010-A0110-V0100-PE.pkg: data
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$

---

### Post by root-x on 2010-07-31
This is the pkg file [http://rapidshare.com/files/410273191/EP0002-BLES00683_00-MW2P000000000010-A0110-V0100-PE.pkg.html](http://rapidshare.com/files/410273191/EP0002-BLES00683_00-MW2P000000000010-A0110-V0100-PE.pkg.html)

---

### Post by WorMzy on 2010-07-31
I've taken a look at it, and there doesn't seem to be anything you can do with it. It must rely on a specific algorith encoded into the Playstation Network Downloader, or maybe the algorithm's built into the file, and the PND can read it; either way, I think you're going to have to use wine to run the PND to extract the file, there doesn't seem to be any way of extracting it's contents otherwise.

---

### Post by Quackers on 2010-07-31
I don't know if it will help but this subject was discussed on the Vaio Link Forum some time ago. I haven't been there in a while and the last time I was there the search function didn't work. It'd be mean a lot of trawling through threads to find an answer. If you fancy that here's a link

[http://club.vaio.sony.ru/clubvaio/gb/en/forum/listthreads?forum=6](http://club.vaio.sony.ru/clubvaio/gb/en/forum/listthreads?forum=6)

---

### Post by root-x on 2010-07-31
> **Quackers said:**
> I don't know if it will help but this subject was discussed on the Vaio Link Forum some time ago. I haven't been there in a while and the last time I was there the search function didn't work. It'd be mean a lot of trawling through threads to find an answer. If you fancy that here's a link

[http://club.vaio.sony.ru/clubvaio/gb/en/forum/listthreads?forum=6](http://club.vaio.sony.ru/clubvaio/gb/en/forum/listthreads?forum=6)

Yeah thanks for the link do you know the username of the person discussing it ?

---

### Post by root-x on 2010-07-31
Cant find anything regarding my issue, thanks anyway.

---

### Post by Quackers on 2010-07-31
No, I'm afraid I don't. It could have been 18 months ago to be honest. I see the forum has changed looks and possibly staff as well since I was a regular. I'll have a look through some old threads. 
On a side note Sony issue EP files as Vaio Updates and they are executable on a Vaio by double-clicking in Windows. I've never tried to get into one though.

---

