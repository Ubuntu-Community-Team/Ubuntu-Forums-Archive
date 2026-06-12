---
title: "wallpaper changer please?"
date: 2011-09-22
forum: General Help
---

### Post by liquidmonkey on 2011-09-22
i'm looking for a wallpaper changer, one that is SIMPLE and upon installation does NOT require any screwing around with the whitelist or anything else.

just a simple click and........... it runs :) with a local directory.

and i'm using 11.04.


so far i've tried...
desktop drapes - can't even get it to run
wally - requires whitelist BS
wallpaper gallery - 
desktop nova - nothing happens when i put in the settings
webilder - seems to only allow online flickr photos which i can't get to work anyway.



any ideas?

---

### Post by raja.genupula on 2011-09-22
[http://www.makeuseof.com/tag/5-wallpaper-changer-apps-for-linux/](http://www.makeuseof.com/tag/5-wallpaper-changer-apps-for-linux/)


go with this

---

### Post by hawthornso23 on 2011-09-22
I use desktop nova. It seems to be the best. However natty has managed to pretty thoroughly break tray applets. The desktop nova tray applet (which works fine in maverick) won't work at all in natty; even in a whitelist; even using the classic desktop!

However an indicator applet has now been written for desktop-nova which works just fine. It isn't in the repositaries yet though - you need to get it from the following ppa. 

[http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu](http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu)

---

### Post by stinkeye on 2011-09-22
Have a look at [**_[COLOR="DarkRed"]Wallch[/COLOR]_**]("http://www.omgubuntu.co.uk/2011/08/wallch-wallpaper-changer-adds-unity-features/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29").

---

### Post by liquidmonkey on 2011-09-22
> **stinkeye said:**
> Have a look at [**_[COLOR="DarkRed"]Wallch[/COLOR]_**]("http://www.omgubuntu.co.uk/2011/08/wallch-wallpaper-changer-adds-unity-features/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29").


u just made my week!
very painless and it works, THANK YOU and HAVE AN :popcorn: AWESOME DAY/NIGHT/WEEK/MONTH ):P

---

### Post by raja.genupula on 2011-09-22
hey man we are glad that you got solved with your issue , please mark your thread as solved from thread tools

---

### Post by varunendra on 2011-09-22
> **liquidmonkey said:**
> so far i've tried...
desktop drapes - can't even get it to run
....

I haven't tried others, but I regularly use Drapes and like it! It is in the official repo, gets installed very easily, starts easily, and its configuration too is very easy. However, it has that common problem of not starting at startup even when the option to do so is selected in preferences. The solution is very simple though. It goes as:

[LIST]
[*]Open Preferences > General tab and check the option to "Start Desktop Drapes at Start"
[/LIST]

[LIST]
[*]Open its startup configuration file **drapes.desktop**: ```
gedit ~/.config/autostart/drapes/drapes.desktop
```
[/LIST]

[LIST]
[*]Add this line at the bottom (or top - doesn't matter): ```
Type=Application
``` Save, close and reboot to see if it worked (it always works for me!)
[/LIST]


**_EDIT_:**
Just found it doesn't even run on Natty by default. Here's a bug report with solution (posts #2,3 for 64 bit & 32 bit resp.):
[https://bugs.launchpad.net/ubuntu/+source/drapes/+bug/756687](https://bugs.launchpad.net/ubuntu/+source/drapes/+bug/756687)

Solution is:
```
cd /usr/lib/x86_64-linux-gnu
sudo ln -s libX11.so.6 libX11.so
```(for 64bit)

```
cd /usr/lib/i386-linux-gnu
sudo ln -s libX11.so.6 libX11.so
```(for 32 bit: tested myself)

 
Also, the address of configuration file is **~/.config/autostart/drapes.desktop** in Natty.

---

### Post by liquidmonkey on 2011-09-23
> **varunendra said:**
> I haven't tried others, but I regularly use Drapes and like it! It is in the official repo, gets installed very easily, starts easily, and its configuration too is very easy. However, it has that common problem of not starting at startup even when the option to do so is selected in preferences. The solution is very simple though. It goes as:

[LIST]
[*]Open Preferences > General tab and check the option to "Start Desktop Drapes at Start"
[/LIST]

[LIST]
[*]Open its startup configuration file **drapes.desktop**: ```
gedit ~/.config/autostart/drapes/drapes.desktop
```
[/LIST]

[LIST]
[*]Add this line at the bottom (or top - doesn't matter): ```
Type=Application
``` Save, close and reboot to see if it worked (it always works for me!)
[/LIST]


**_EDIT_:**
Just found it doesn't even run on Natty by default. Here's a bug report with solution (posts #2,3 for 64 bit & 32 bit resp.):
[https://bugs.launchpad.net/ubuntu/+source/drapes/+bug/756687](https://bugs.launchpad.net/ubuntu/+source/drapes/+bug/756687)

Solution is:
```
cd /usr/lib/x86_64-linux-gnu
sudo ln -s libX11.so.6 libX11.so
```(for 64bit)

```
cd /usr/lib/i386-linux-gnu
sudo ln -s libX11.so.6 libX11.so
```(for 32 bit: tested myself)

 
Also, the address of configuration file is **~/.config/autostart/drapes.desktop** in Natty.




thanks for the info!

---

