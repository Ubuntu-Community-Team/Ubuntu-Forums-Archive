---
title: "Where do downloads go? - Newbie needs help!"
date: 2009-12-31
forum: General Help
---

### Post by MikeinVA on 2009-12-31
When I am downloading my bank statements I get a popup stating "Download of xxx.xx complete. It doesn't say where it was downloaded to. I also downloaded Adobe Reader and Chrome and don't know where they went either. Any help would be much appreciated.

Mike

---

### Post by drs305 on 2009-12-31
> **MikeinVA said:**
> When I am downloading my bank statements I get a popup stating "Download of xxx.xx complete. It doesn't say where it was downloaded to. I also downloaded Adobe Reader and Chrome and don't know where they went either. Any help would be much appreciated.

Mike

Often downloads are sent to your Desktop (/home/yourusername/Desktop, or ~/Desktop for short), or your $HOME folder (/home/yourusername).

As for the apps, if you don't find them on your Desktop if you give us the link to the download site we can tell you where their default download location is.

Also, if you know the name of the downloaded file, you can do a search with the following command:
[code]
sudo find / -iname *filename*
[code]
It may take a while to run because it will look through your entire system. You could start by searching just your $HOME folder with "find ~/ -iname *filename*

---

### Post by tubbygweilo on 2009-12-31
If you are using Mozilla Firefox then 

Edit > Preferences > Main > Downloads 

Will allow you to set where downloads are stored on your computer.

By clicking the browse button you will be able to set your desired location.

---

### Post by MikeinVA on 2009-12-31
Thank you both for the help. I really want to try Chrome. Here are the locations:

[http://www.google.com/chrome/eula.html](http://www.google.com/chrome/eula.html) – Chrome

[http://get.adobe.com/reader/?promoid=BUIGO](http://get.adobe.com/reader/?promoid=BUIGO) – Adobe Reader

As far as Firefox goes, I crashed it a while back and have been using Epiphany.
Any suggestions for reloading Firefox? I tried it once but when I click on it the mouse pointer just spins for a while and stops. Thanks!

---

### Post by drs305 on 2009-12-31
It looks like the Chromium link actually is designed install the software, in which case you should be able to open it from the Main menu. I think Chromium puts an icon in Applications, Internet.

As for Adobe, did you select the .deb file? These are much easier to install than the .bin packages. Normally the .deb file will end up on your Desktop but the link might also offer to install it with Gdebi, which if offered, is also acceptable. The current file name is Adbe-Rdr9.2-1_i386linux_enu.deb

---

### Post by LuisGMarine on 2009-12-31
The easiest way to re-install mozilla-firefox is just to open up your Ubuntu Software Center, which you can find by going to Applications > Ubuntu Software Center.

In the search box just type in "firefox", with out quotations and download the web browser that way.

If it's already installed and it is still giving you problems when you launch it, then go ahead and open it from the terminal.  To do so, click on Applications > Accerssories > Terminal.  Once the terminal window pops up, type in:

```
firefox
```

If it doesn't open please post back the output of what ever showed up on Terminal.

---

### Post by Leppie on 2009-12-31
> **MikeinVA said:**
> Any suggestions for reloading Firefox? I tried it once but when I click on it the mouse pointer just spins for a while and stops. Thanks!

you could try renaming the firefox folder:
```
$mv ~/.mozilla/firefox ~/.mozilla/firefox.old
```

---

### Post by MikeinVA on 2010-01-01
I'd like to thank everyone for the help. I got Adobe reader and Chrome downloaded and installed. Chrome works great, even You Tube works fine. Only problem I have now is with Hulu.com, the movies are choppy in full screen on Chrome. Things just keep getting better with Ubuntu!!!

Mike

---

### Post by LuisGMarine on 2010-01-01
> **MikeinVA said:**
> I'd like to thank everyone for the help. I got Adobe reader and Chrome downloaded and installed. Chrome works great, even You Tube works fine. Only problem I have now is with Hulu.com, the movies are choppy in full screen on Chrome. Things just keep getting better with Ubuntu!!!

Mike

To be quite honest they where choppy for me even on my windows XP. :popcorn:

---

