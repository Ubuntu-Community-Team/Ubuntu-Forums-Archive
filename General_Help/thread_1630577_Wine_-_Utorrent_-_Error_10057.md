---
title: "Wine - Utorrent - Error 10057"
date: 2010-11-25
forum: General Help
---

### Post by balaji31d on 2010-11-25
I have a cable connection in home with two computers. One running Ubuntu (Home PC) and one Windows (Office PC) connected to same switch.

Both have Utorrent 2.0.4 version (In Ubuntu, using wine) with exactly the same settings. Windows downloads at more than 1MB/s with Utorrent Setup Guide runs clean speed test.

But, Ubuntu downloads Max Speed of 100 Kb/s and utorrent setup guide test results in below message

"Results: Speed test failed. Connection failed error: Error 10057 (10057)"

Any help is very much appreciated.

Regards
Balaji M

---

### Post by carl4926 on 2010-11-25
What's up with Transmission?

---

### Post by WorMzy on 2010-11-25
Utorrent is a Windows application. It may not work as well in a Linux environment. Use a native client for the best results.

---

### Post by balaji31d on 2010-11-25
@ Carl and WorMzy- Honestly I remember trying Transmission first few weeks before and it was very slow compared to the later installation utorrent. I will try once again.

Is it a known compatibility issue. Or is it a permission error/issue - Because the Wireshark program I have works with the capture only if i sudo it. If i just open the program it will open but the interface capture buttons will be grayed out and you cannot capture the packet.

Any ideas..

---

### Post by James78 on 2010-11-25
What happens if you do "winetricks utorrent"? It may not fix it, or it may, I don't know. Utorrent has always worked flawlessly for me in WINE.

> **balaji31d said:**
> @ Carl and WorMzy- Honestly I remember trying Transmission first few weeks before and it was very slow compared to the later installation utorrent. I will try once again.

Is it a known compatibility issue. Or is it a permission error/issue - **Because the Wireshark program I have works with the capture only if i sudo it. If i just open the program it will open but the interface capture buttons will be grayed out and you cannot capture the packet.**
That's normal for Wireshark to need root privileges. But for a regular app that uses an internet connection, like Utorrent, KTorrent, etc, they don't need root privileges to work correctly.

---

### Post by balaji31d on 2010-11-25
@ James - I will do the winetricks option when i go home today and will let know the finding.

The normal way i start utorrent is, I go to the downloaded utorrent.exe file and open with wine loader and then add the torrent by clicking on file - add torrent. Am i doing it correctly. Is there any way to fully install it without having to open the executable file via wine loader.

---

### Post by James78 on 2010-11-25
The winetricks option I said earlier will install Utorrent, however you will always have to use WINE to load it, as there's no other way to run exe's natively on Linux. Although, the winetricks option should add an entry to your menu for Utorrent, so you can just go there and open it. Let us know if it still refuses to work afterward!

---

### Post by balaji31d on 2010-11-25
Got it! I will try it tonight and will update the progress immediately.

---

### Post by d3v1150m471c on 2010-11-25
> **carl4926 said:**
> What's up with Transmission?
was wondering that myself. I use transmission-daemon and run all my torrents in a timely manner with cronjob ;). You can set download and upload times with transmission as well.

---

### Post by balaji31d on 2010-11-25
I Guess i got addicted to Utorrent.. lol.. 

Guys - Really do you think transmission is better compared to utorrent (apart from being open source)

---

### Post by carl4926 on 2010-11-26
> **balaji31d said:**
> I Guess i got addicted to Utorrent.. lol.. 

Guys - Really do you think transmission is better compared to utorrent (apart from being open source)

It stands to reason mate.

But I can confirm uTorrent does work in Linux generally.

However, I suggest that you may have to work on your settings. I can't give you such a fair answer because unlike you I suspect, I disable DHT.
But for me Transmission will max out no problem.

Make absolutely sure your port settings are **properly** forwarded in your router.

---

### Post by balaji31d on 2010-11-26
@ Carl - Thanks Man.

I strongly believe my settings and version are the same as in the windows machine. Nevertheless I will double check the settings to make sure we are on the same page.

Other than that, I am pretty positive above the port because, the same port number is used by windows machine to go Max speeds and If you suggest, I can keep my Ubuntu PC in DMZ and test.

Regards
Balaji M

---

### Post by carl4926 on 2010-11-26
If you are still getting the original error
"Connection failed error: Error 10057"

I Google that and just get a load of stuff about Windows.
Sorry but I don't understand it. Although I have Windows installed, I never use it, it's just there for my bootloader testing.

---

### Post by James78 on 2010-11-26
From [here]("http://msdn.microsoft.com/en-us/library/ms740668%28VS.85%29.aspx"),
```
Socket is not connected.

    A request to send or receive data was disallowed because the socket is not connected and (when sending on a datagram socket using sendto) no address was supplied. Any other type of operation might also return this error&#8212;for example, setsockopt setting SO_KEEPALIVE if the connection has been reset.

```

So, that most likely goes to say that WINE may not be able to connect to the internet through your computer (you should have no problems with that!). What happens if you delete ~/.wine, create a new one, and reinstall Utorrent?

Lots of little issues and problems can happen if your WINE prefix is messed up too much. For example, Photoshop CS5 just stopped working for me in WINE, so I had to delete it and redo everything, but it works like it should again.

---

### Post by balaji31d on 2010-11-26
@James and Carl - I will have to go home tonight to try this. Will post back the results as soon as i Test it.

---

### Post by balaji31d on 2010-11-27
Okay.. Lemme update on the progress (progress ??)

1. Removed Wine and Utorrent 2.0.4
2. Installed Wine 1.3 with winestrick (comctrl32 library) and downloaded utorrent latest version 2.2
3. Opened Utorrent 2.2 by wine. It was running in the background but no gui. Opening again will say "it seems that utorrent is already running" - new utorrent does not work with ubuntu

refer: [http://forum.utorrent.com/viewtopic.php?id=88292](http://forum.utorrent.com/viewtopic.php?id=88292) 

4. Downloaded utorrent 2.0.4 - opened by wine - successfully launched, but crashed when adding torrent "utorrent has crashed. A crash dump has been saved as filename.dmp, how would you like to proceed"  and gives me only "ok" button to click hehe (wats the point asking me "how woyld you like to proceed"

5. There is Utorrent for Linux released as a tar version very recently. i am going to try that and will let you know the result.

Regards
Balaji M

---

### Post by carl4926 on 2010-11-27
More versions here
[http://www.filehippo.com/download_utorrent/](http://www.filehippo.com/download_utorrent/)

But often it doesn't go well if you use very old versions, you tend to get kicked

---

### Post by balaji31d on 2010-11-27
Yee Haw.. Wow :)
UTORRENT SERVER (Meant for Linux) Downloaded from Utorrent Website worked perfectly fine... I got back my 1.2 MB/Sec speed!!!!

NO WINE.. NO WINETRICKS.. Just the native utorrent server started  and you can add the torrent either from terminal or open browser and type "http://localhost:8080/gui" and key in a username "admin" and leave the password blank.

Just perform some regular tweaks and wah..lah.. It works perfectly fine! for 64bit users, I guess you have to still wait.

All guys who helped me with this issue, Thanks a Lot.. I am a Happy Ubuntu user :)

---

### Post by nmr on 2011-01-18
> **balaji31d said:**
> Yee Haw.. Wow :)
UTORRENT SERVER (Meant for Linux) Downloaded from Utorrent Website worked perfectly fine... I got back my 1.2 MB/Sec speed!!!!

NO WINE.. NO WINETRICKS.. Just the native utorrent server started  and you can add the torrent either from terminal or open browser and type "http://localhost:8080/gui" and key in a username "admin" and leave the password blank.

Just perform some regular tweaks and wah..lah.. It works perfectly fine! for 64bit users, I guess you have to still wait.

All guys who helped me with this issue, Thanks a Lot.. I am a Happy Ubuntu user :)

balaji31d,

Any chance those tweaks helped you Max your downloads speed?
I was using uTorrent under Wine (always below 100KBs/s) and now i am using uTorrent Server, but the speed is even lower: below 20KBs/s.

Is there any tweak you can advise to make it more efficient?
Thank you for your time,
nuno.

---

### Post by balaji31d on 2011-01-18
> **nmr said:**
> balaji31d,

Any chance those tweaks helped you Max your downloads speed?
I was using uTorrent under Wine (always below 100KBs/s) and now i am using uTorrent Server, but the speed is even lower: below 20KBs/s.

Is there any tweak you can advise to make it more efficient?
Thank you for your time,
nuno.

Hi, after running the utorrent server i followed the youtube video explaining to tweak utorrent. below is the link.

watch?v=u9w8Wet5np0

---

### Post by nmr on 2011-01-21
Thank you so much for the link.
I'll look into it.

> **balaji31d said:**
> Hi, after running the utorrent server i followed the youtube video explaining to tweak utorrent. below is the link.

watch?v=u9w8Wet5np0

---

