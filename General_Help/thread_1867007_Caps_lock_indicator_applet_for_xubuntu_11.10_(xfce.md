---
title: "Caps lock indicator applet for xubuntu 11.10 (xfce 4.8)?"
date: 2011-10-22
forum: General Help
---

### Post by aspidistra on 2011-10-22
There isn't one

pretty essential

can't find out how to get one 

"lock-keys-applet" (gnome) I can't get

---

### Post by raja.genupula on 2011-10-22
hi go with this 

[http://askubuntu.com/questions/66181/how-do-i-enable-the-globalmenu-appmenu-on-xfce-or-lxde](http://askubuntu.com/questions/66181/how-do-i-enable-the-globalmenu-appmenu-on-xfce-or-lxde)

[http://www.omgubuntu.co.uk/2010/09/indicator-keylock-ubuntu/](http://www.omgubuntu.co.uk/2010/09/indicator-keylock-ubuntu/)

All The best .

---

### Post by aspidistra on 2011-10-22
> **raja.genupula said:**
> hi go with this 

[http://askubuntu.com/questions/66181/how-do-i-enable-the-globalmenu-appmenu-on-xfce-or-lxde](http://askubuntu.com/questions/66181/how-do-i-enable-the-globalmenu-appmenu-on-xfce-or-lxde)

[http://www.omgubuntu.co.uk/2010/09/indicator-keylock-ubuntu/](http://www.omgubuntu.co.uk/2010/09/indicator-keylock-ubuntu/)

All The best .

#1 doesn't work because i'm running 64 bit 

> 

[LIST=1]
[*]**Install the missing dependencies**. In a terminal : sudo apt-get install indicator-appmenu appmenu-gtk appmenu-qt
[*]**Install the app menu** : download [this deb]("http://ubuntuone.com/0TaQXo8rXjqcYhZrZv49wy") and open it with the software center
[*]**Enable app menu for firefox and thunderbird**. In a terminal : sudo apt-get install appmenu-gtk3 firefox-globalmenu thunderbird-globalmenu
[*]Right-click on an empty part of the top XFCE panel and choose **Panel** > **Add New Items** > **App Menu plugin**
[/LIST]
  *[Source]("http://www.omgubuntu.co.uk/2011/10/how-to-enable-ubuntus-global-menu-in-xubuntu-11-10/")*
 1. already installed
2. doesn't install (only for i386)
3. already installed
4. because 2 doesn't install -- not available

the "omgubuntu"

have tried this before

that doesn't work either this is xubuntu 11.10

> W: Failed to fetch [ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/dists/oneiric/main/source/Sources]("http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/dists/oneiric/main/source/Sources")  404  Not Found

W: Failed to fetch [ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/dists/oneiric/main/binary-amd64/Packages]("http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/dists/oneiric/main/binary-amd64/Packages")  404  Not Found

W: Failed to fetch_ _[ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/dists/oneiric/main/binary-i386/Packages]("http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu/dists/oneiric/main/binary-i386/Packages")  404  Not Found

**HTTP:// redacted in the above to show url (indicator keylock not found)**

E: Some index files failed to download. They have been ignored, or old ones used instead.
dan@brick:~$ sudo apt-get install indicator-keylock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package indicator-keylock
dan@brick:~$ sudo apt-get install indicator-keylock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package indicator-keylock
If I could get gnome panel applets to install I could install "lock-keys-applet"

this is extremely basic ... a large percentage of machines don't come with a caps lock light

---

### Post by aspidistra on 2011-10-22
impossible ...

there is an indicator

doesn't work for 4.8 xfce

there is a python hack to get round this

I sense that people will be ditching xubuntu xfce as we speak because of such a basic omission

---

### Post by aspidistra on 2011-10-22
the python code for a custom applet to run once a second look for caps lock and display
doesn't work right away

I changed it a bit

person who wrote it has put in the path name but hasn't got the png workign (picture, traffic light) for the applet 
no idea also - no time to bother

could be changed to get the png working -- I have just put two asterisks up to alert caps lock on
further addition would be for num lock symbol

ugly - called every second (genmon applet) which is "custom python applet"

but at least I have a caps lock indicator

from [http://blog.treellama.org/2011/01/genmon-numlockpy.html](http://blog.treellama.org/2011/01/genmon-numlockpy.html)

> 
#!/usr/bin/python

indicator="Caps Lock"
text = ""
on_icon="**"
off_icon=""

#on_icon = "/usr/share/pixmaps/pidgin/status/16/available.png"
#off_icon = "/usr/share/pixmaps/pidgin/status/16/invisible.png"

from ctypes import *

def GetIndicatorState(name):
    state = c_bool(False)

    libX11 = CDLL("libX11.so")
    display = libX11.XOpenDisplay(0)
    atom = libX11.XInternAtom(display, name, c_bool(False))
    libX11.XkbGetNamedIndicator(display, atom, 0, byref(state), 0, 0)
    libX11.XCloseDisplay(display)
        
    return state.value

if GetIndicatorState(indicator):
    print("" + on_icon + "")
else:
    print("" + off_icon + "")


---

### Post by gsmanners on 2011-10-22
I would suggest using LXPanel, myself (if I had that problem). Meanwhile, this problem has made the [wishlist]("http://wiki.xfce.org/plugins_wish_list").

---

### Post by gridcube on 2011-10-22
Another way of doing it is installing:
[http://git.xfce.org/panel-plugins/xfce4-kbdleds-plugin/](http://git.xfce.org/panel-plugins/xfce4-kbdleds-plugin/)

You need to compile it, the dependencies i lacked on a default xubunu oneiric ocelot 11.10, where intltool, libxfce4ui-1, xfce4-panel-dev, and xorg-dev

they all install whit:
```

sudo apt-get install intltool libxfce4ui-1-dev xfce4-panel-dev xorg-dev

```

uncompress the plugin to some folder, and on a terminal execute 
```

./config --prefix=/usr

```
you need to change the prefix by hand, this is a bug from xfce4-panel. If you get some error its probably some other dependency its not fulfilled, ask around.


then you run in the same folder:
```

 make && sudo make install

```

this will install the plugin and then you can add it to your panel :****)

---

### Post by gsmanners on 2011-10-22
> **gridcube said:**
> You need to compile it, the dependencies i lacked on a default xubunu oneiric ocelot 11.10, where intltool, libxfce4ui-1, xfce4-panel-dev, and xorg-dev

Cool. See, already hard at work on it. :)

You really need all of xorg-dev? I think I'd try xserver-xorg-dev if I could and avoid the monster pile you get from the other.

---

### Post by aspidistra on 2011-10-22
Doesn't work GridCube

> Another way of doing it is installing:
[http://git.xfce.org/panel-plugins/xfce4-kbdleds-plugin/](http://git.xfce.org/panel-plugins/xfce4-kbdleds-plugin/)

You need to compile it, the dependencies i lacked on a default xubunu oneiric ocelot 11.10, where intltool, libxfce4ui-1, xfce4-panel-dev, and xorg-dev

they all install whit:```

sudo apt-get install intltool libxfce4ui-1 xfce4-panel-dev xorg-dev

```
libxfce4ui-1 is not available though apt

"E: Unable to locate package libxfce4ui-1"

I have canonical enabled (software source)
Is this the one you said you got through synaptic (because I can't see it there either ... the compile requires that specific package) ... rhin0 from freenode here

> uncompress the plugin to some folder, and on a terminal execute```

./config --prefix=/usr

```
./configure --prefix=/usr                       works (not ./config)

---

### Post by gridcube on 2011-10-22
> **aspidistra said:**
> Doesn't work GridCube


libxfce4ui-1 is not available though apt

"E: Unable to locate package libxfce4ui-1"

I have canonical enabled (software source)
Is this the one you said you got through synaptic (because I can't see it there either ... the compile requires that specific package) ... rhin0 from freenode here


./configure --prefix=/usr                       works (not ./config)

Yes, sorry, my mistake, its:


libxfce4ui-1-dev

---

### Post by aspidistra on 2011-10-22
Right -- this all works --

to get keyboard status indicator panel plugin

> 

Download and extract (decompress) this package to a directory

[http://git.xfce.org/panel-plugins/xfce4-kbdleds-plugin/](http://git.xfce.org/panel-plugins/xfce4-kbdleds-plugin/)

load these packages:

```
sudo apt-get install intltool libxfce4ui-1-dev xfce4-panel-dev xorg-dev
```(someone on this thread said xserver-xorg-dev will be smaller than xorg-dev and still work)

change to the directory and configure with this command:

```
./configure --prefix=/usr
```then compile it:

```
make && sudo make install
``` gives you a "Kbleds" plugin. Add it to your panel.



---

### Post by muppet317 on 2012-03-06
This worked perfectly for me:
[http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html](http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html)

---

### Post by kurt18947 on 2012-03-06
> **muppet317 said:**
> This worked perfectly for me:
[http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html](http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html)

+1  This or something like it is critical with wireless keyboards without LED indicators.  Entering passwords without knowing the state of the capslock can be tricky.  Here's a link to the various .debs.

[http://ppa.launchpad.net/tsbarnes/indicator-keylock-daily/ubuntu/pool/main/i/indicator-keylock/](http://ppa.launchpad.net/tsbarnes/indicator-keylock-daily/ubuntu/pool/main/i/indicator-keylock/)

The amd64 deb for oneiric seems to work in precise as well.  In fact, precise gnome-shell seems to come with this or something very similar already included. I haven't tried 12.04 Xfce4-desktop yet but it worked fine in 11.10 Xfce-desktop.

---

### Post by aspidistra on 2012-12-11
delete

---

