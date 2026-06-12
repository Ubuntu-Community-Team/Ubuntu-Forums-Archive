---
title: "Google Chrome won't open; Chromium crashes"
date: 2012-07-09
forum: General Help
---

### Post by pottzie on 2012-07-09
I have just installed Ubuntu 12.04, having to first install Ubuntu 11.10 and then upgrading from that, as the live cd wouldn't work on my computer for some reason. It's an older Compaq with a gig of ram, and I'm using a 32 bit system.

 I have flash installed, and when I tried using it in Youtube, it worked, but the video froze part way through the video, although the sound kept going. I then installed Chromium, using the Unity package manager. When I tried to get youtube to work in Chromium, it said that a plugin was missing. I had no results trying to get that to work, so I tried ti install Google Chrome stable. The icon for Google Chrome is in the "Internet" section, but Google Chrome never opens.

 Sound like anything someone could help me clear up? I've changed my set up to Gnome, and it defaults to Gnome fall back.

Edit: Trying whatever I find on Google, this from a guide. I installed Opera, to see how well opera worked. No video on Opera, so I found a guide:[http://*********************.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://*********************.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

 And I ran sudo apt-get install flashplugin-installer gsfonts-x11 in the terminal. When I did, I got a warning from bash saying that I have two sources listed for Google.

W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

When I ran apt-get update, the warning shows up again.

---

### Post by haresear on 2012-07-09
Some have had problems with the latest version of Chrome due to a problem with the included new Pepper/Flash. If this is your problem, the immediate solution is to downgrade flash to an earlier version, e.g. 11.1. If you search the Ubuntu Forums for "chrome flash pepper" you will find quite a few recent threads.

---

### Post by pottzie on 2012-07-09
Thanks haresear for the tips, but I'm stuffed. When I tried to follow the tips to downgrade Adobe flash in either Chromium or Google Chrome, Chromium crashes as soon as it opens-and Google Chrome won't even get that far(!); it doesn't open at all.

  I need to get past the crash/not opening problem before I can wrench on flash. And as I said, I installed Opera to see if that worked, and so far I have flash/video on Firefox, and that's all.

I might as well have a message saying "All your browser are belong to us."

---

### Post by haresear on 2012-07-09
Did you try starting Google Chrome with flash disabled as described in post #3 of the following thread?
[http://ubuntuforums.org/showthread.php?t=2015563]("http://ubuntuforums.org/showthread.php?t=2015563")


```
google-chrome --disable-bundled-ppapi-flash
```

---

### Post by pottzie on 2012-07-10
haresear, that  "kind of" worked. Google Chrome did "attempt" to open. Made it farther than it has so far, I was able to register to my Google account and sync. Then when I tried to search, it crashed without getting as far  as me hitting "enter." Never saw anything in the search bar, and the Google logo never showed up.

Still, better than I've managed to get so far.

Edit: Just retried it, this time I made it as far as getting to Youtube to see if video worked. It doesn't, but the terminal logged several "Core dump...Couldn't initialize plug-in." messages.

---

### Post by haresear on 2012-07-10
If you start Chrome with the disable-flash option, then flash won't be available unless you install an older version of flash, as noted in this thread:
[http://ubuntuforums.org/showthread.php?t=2011882&page=4]("http://ubuntuforums.org/showthread.php?t=2011882&page=4")

The flash problem should not cause Chromium to crash, just that flash will not work, so your Chromium crashes may be caused by some other problem.

Earlier there was a problem in Chrome, and maybe Chromium, having to do with syncing passwords. You might try turning off sync, or just deselect the password sync. There was a command line option that would workaround this problem, but I can't remember the exact syntax.

---

### Post by pottzie on 2012-07-10
haresear, following through the links I came upon this:[https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)

It suggested 
sudo mv /opt/google/chrome/PepperFlash /opt/google/chrome/PepperFlash.bak google-chrome

Still got the same results, Google Chrome opens, no Google logo, no video on Youtube.

Here's the terminal log, if anyone is curious.
```

larry@larry-DA236A-ABA-6420NX-NA910:~$ sudo mv /opt/google/chrome/PepperFlash /opt/google/chrome/PepperFlash.bak
[sudo] password for larry: 
larry@larry-DA236A-ABA-6420NX-NA910:~$ google-chrome
--2012-07-10 10:55:05--  https://clients2.google.com/cr/report
Resolving clients2.google.com (clients2.google.com)... 173.194.33.4, 173.194.33.5, 173.194.33.6, ...
Connecting to clients2.google.com (clients2.google.com)|173.194.33.4|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                    ] 0           --.-K/s              
Crash dump id: 5806a5471b3b1848
[12:12:62437726931:ERROR:ppapi_thread.cc(188)] Failed to load Pepper module from /opt/google/chrome/PepperFlash/libpepflashplayer.so (error: /opt/google/chrome/PepperFlash/libpepflashplayer.so: cannot open shared object file: Permission denied)
larry@larry-DA236A-ABA-6420NX-NA910:~$ 


```

---

### Post by haresear on 2012-07-10
I'm afraid I've reached the end of my experience with this issue. Maybe someone else more knowledgeable will chime in.

---

### Post by pottzie on 2012-07-10
FWIW, apparently
 sudo mv /opt/google/chrome/PepperFlash /opt/google/chrome/PepperFlash.bak 
google-chrome  

Is supposed to allow Google Chrome to open and run, but without video. So it actually works, I just expected it to include working video. Hope someone fixes both Chrome and Google Chrome,as I use them and like them a lot.

---

### Post by haresear on 2012-07-10
If you want flash videos to work, you would have to install an older version of flash for the time being, such as version 11.1.
Here is a thread that describes how to do that:
[http://ubuntuforums.org/showthread.php?t=1953796]("http://ubuntuforums.org/showthread.php?t=1953796")
See post #1, Solution 2-Downgrade Flash

---

### Post by Pilot6 on 2012-07-11
On older CPUs like AthlonXP Chrome crashes on keyring password store. It happens when you go to sites, which require password.
You have to start it with --password-store=basic 
to avoid it. Also disable pepper flash as was mentioned above.

On older comps I start Chrome this way
```

google-chrome --password-store=basic --disable-bundled-ppapi-flash

```
All works OK. If you do not know how to get these keys to be stored in a launcher shortcat, you are welcome to ask.
And you do not need older flash. 11.2 from repos works quite well.

---

