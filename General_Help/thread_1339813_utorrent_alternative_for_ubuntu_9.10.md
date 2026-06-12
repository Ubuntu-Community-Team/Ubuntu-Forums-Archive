---
title: "utorrent alternative for ubuntu 9.10"
date: 2009-11-27
forum: General Help
---

### Post by manuleka on 2009-11-27
with utorrent on my windows machine i can do downloads fine... when i run transmission on ubuntu it freezes my adsl modem/router :(

i have set the settings on transmission similar to utorrent and it still freezes my modem :( weird

can anyone recommend me a bittorrent client that is as simple and yet won't freeze my adsl modem/router like utorrent?

i have tried wine to install utorrent on ubuntu but no luck :(

---

### Post by shaggy999 on 2009-11-28
Here's a webpage comparing all bittorrent clients:
[http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients](http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients)

You might want to look into Vuze or Deluge. Personally, I use rtorrent, which runs at the command line and is super powerful.

---

### Post by raktarok on 2009-11-28
Try deluge, its a fine client.

---

### Post by claracc on 2009-11-28
Ktorrent or qbittorrent, both of them work  well in ubuntu 9.10, consuming low resources.

---

### Post by jono2009 on 2009-11-28
I also use Deluge, best downloader for me

---

### Post by RedSingularity on 2009-11-28
+ 1 for deluge.

---

### Post by anonSam on 2009-11-28
Utorrent 1.8.4 and 1.8.5 have some bugs that cause it not to finish installing for a lot of Wine users.  I got utorrent 1.8.4 to work by installing 1.8.2 and then used utorrent's automatic update (but isn't offering me 1.8.5 for some reason) and it works well now.

Alternatively there is the less popular official Bittorrent client which looks and feels (and works?) exactly the same as utorrent but actually installs correctly and easily for me compared to utorrents last few releases. I've been using it since v6.2 and except for it saying Bittorrent instead of uTorrent on the title bar, I can't tell a difference between the two at all. If you really don't want to give up utorrent (I understand...) and can't get it to work I would recommend Bittorrent.

I also agree with everyone else, Deluge is a fine bittorrent client! Ktorrent is also very nice, and in my opinion is the closest uTorrent alternative other then Bittorrent. I never tried rTorrent (but heard a lot of good things).

You cold also try turning off your firewall for a little while to see if thats the problem rather then the client. Also, some of us are having problems downloading large files via bittorrent to Ubuntu's encrypted home directory (clients crash or modem speeds drop).


Test results for uTorrent 1.8 at winehq:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11113](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11113)

Large Files - BitTorrent Crash:
[http://ubuntuforums.org/showthread.php?t=1216636&highlight=bittorrent+download+large+files](http://ubuntuforums.org/showthread.php?t=1216636&highlight=bittorrent+download+large+files)

---

### Post by scouser73 on 2009-11-28
+1 for Deluge, it's just the best torrent client that I've used.

---

### Post by manuleka on 2009-11-28
thanks guys... i think i'll try deluge... hopefully it will not freeze my modem/router

---

### Post by manuleka on 2009-11-28
> **anonSam said:**
> Utorrent 1.8.4 and 1.8.5 have some bugs that cause it not to finish installing for a lot of Wine users.  I got utorrent 1.8.4 to work by installing 1.8.2 and then used utorrent's automatic update (but isn't offering me 1.8.5 for some reason) and it works well now.


i downloaded 1.7.7 installed it... using utorrents autoupdate i've got 1.8.4 running :)

thanks guys

---

### Post by trytenn on 2009-11-30
rtorrent rocks! I installed it yesterday and it's not a commandline client. It has sort of a graphical interface. But it runs in the terminal and u can't use the mouse to click around, only keyboard. Anyway, I used it one day now and I'm able to do everything i want. So it's not that hard to learn. The good things about it is that it's fast, easy to tweak and very low on cpu.

And another thing, if you want the magnet links to work you need to install the latest version no matter what program u use. At least with deluge, vuze and rtorrent (build from trunk and install patch) and if u want to download from thepiratebay. So don't install from ubuntus usual repos. Search for your program in [launchpad.net]("http://launchpad.net/"). U need to check out the change log and maybe some bug reports/forum threads.

//Simon

---

### Post by bgbnbigben on 2009-12-01
Whilst this thread has been solved:

you *can* install wine under 9.10.

Simply install it like normal.
From there, open up a terminal window and make sure you killall any appearences of 'utorrent.exe' or 'uTorrent.exe'
of course, just issue ```
 killall utorrent.exe uTorrent.exe 
``` inside your terminal.

From here, modify the shortcut that wine has placed on your desktop. You should see something like this:
```
env WINEPREFIX="/home/ben/.wine" wine "C:\Program Files\uTorrent\uTorrent.exe"
```Append it with a space and a /NOINSTALL

In other words, it will now look like so:
```
env WINEPREFIX="/home/ben/.wine" wine "C:\Program Files\uTorrent\uTorrent.exe" /NOINSTALL
```From here, it works perfectly :)
good luck with whichever client you chose.

---

### Post by shaggy999 on 2009-12-06
> **trytenn said:**
> rtorrent rocks! I installed it yesterday and it's not a commandline client. It has sort of a graphical interface. But it runs in the terminal and u can't use the mouse to click around, only keyboard. Anyway, I used it one day now and I'm able to do everything i want. So it's not that hard to learn. The good things about it is that it's fast, easy to tweak and very low on cpu.

And another thing, if you want the magnet links to work you need to install the latest version no matter what program u use. At least with deluge, vuze and rtorrent (build from trunk and install patch) and if u want to download from thepiratebay. So don't install from ubuntus usual repos. Search for your program in [launchpad.net]("http://launchpad.net/"). U need to check out the change log and maybe some bug reports/forum threads.

//Simon

rtorrent IS a commandline client. It runs on a terminal using a curses interface. It obviously doesn't work with a mouse because it's not a graphical application.

---

### Post by manuleka on 2009-12-10
> **bgbnbigben said:**
> Whilst this thread has been solved:

you *can* install wine under 9.10.

Simply install it like normal.
From there, open up a terminal window and make sure you killall any appearences of 'utorrent.exe' or 'uTorrent.exe'
of course, just issue ```
 killall utorrent.exe uTorrent.exe 
``` inside your terminal.

From here, modify the shortcut that wine has placed on your desktop. You should see something like this:
```
env WINEPREFIX="/home/ben/.wine" wine "C:\Program Files\uTorrent\uTorrent.exe"
```Append it with a space and a /NOINSTALL

In other words, it will now look like so:
```
env WINEPREFIX="/home/ben/.wine" wine "C:\Program Files\uTorrent\uTorrent.exe" /NOINSTALL
```From here, it works perfectly :)
good luck with whichever client you chose.

cheers :)

---

