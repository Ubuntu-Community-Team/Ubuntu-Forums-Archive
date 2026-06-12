---
title: "Good programs"
date: 2005-03-09
forum: General Help
---

### Post by JMY1983 on 2005-03-09
I just got Ubuntu to run properly so tell me all about the good software for linux I've been missing! Programs of any category are appreciated!

---

### Post by spartas on 2005-03-09
First of all, install and cofigure your computer before going spastic with linux software (like I did).  Go to [http://ubuntuguide.org](http://ubuntuguide.org) and read up on installing stuff like the flashplayer for mozilla, xmms, adobe acrobat reader, java and the like as well as configuring it to use the network with windows computers as well (optional).  

Afterward, or beforeward, run apt-get update then apt-get upgrade to upgrade all your packages to the latest version.

Finally, the good stuff comes into the picture.  A really good app is gnome-launch-box (via apt-get) so you can load up programs using the keyboard (faster than a mouse after you get it running.  Only way to run it is from the terminal though [yes, I run hoary]).

---

### Post by JMY1983 on 2005-03-09
Cool, I have updated all my packages already. What's next?

---

### Post by KLineD on 2005-03-09
Maybe it's best to say what you need/want to do.

For example maybe you want to share some files with another PC in your house/office that runs windows, theres Samba to do that.

You need graphics editing?? The Gimp. Maybe you just want to play mp3s ?? well you need to enable the propietary (non free) codecs, as spartas said, visit [the ubuntu guide](http://ubuntuguide.org) to do that and many more great things.

It all depends in what you need or want to do.

---

### Post by JMY1983 on 2005-03-09
I'm thinking as a windows user, of programs that make the OS easier and fun. Like a mail checker, volume hotkey program, zip tool, good music player, other stuff like that.

---

### Post by Kimm on 2005-03-10
> 
Like a mail checker


if you mean like Outlook then theres one allredy installed, Evolution, its cinda good.

> 
zip tool


that is also alredy installed... try running gzip, it should open archives automaticly however

> 
good music player


Run synaptic and look for a program called XMMS, when you find it mark it for installation and click apply. If you want something more powerfull however, have a look at beep-media-player, its based on XMMS and personaly I think its better...
make a search for beep-media-player on google. If you to, try compiling it from source (allways good to know how).

Just extract the archive and do this...

> 
cd <folder that contains files>
./configure
sudo make
sudo make install


it does take a while to compile, but well, you'll be facing one good looking media player when its done.

---

### Post by JMY1983 on 2005-03-10
[QUOTE=Kimm]if you mean like Outlook then theres one allredy installed, Evolution, its cinda good.



that is also alredy installed... try running gzip, it should open archives automaticly however



Run synaptic and look for a program called XMMS, when you find it mark it for installation and click apply. If you want something more powerfull however, have a look at beep-media-player, its based on XMMS and personaly I think its better...
make a search for beep-media-player on google. If you to, try compiling it from source (allways good to know how).

Just extract the archive and do this...



it does take a while to compile, but well, you'll be facing one good looking media player when its done.[/QUOTE]
 Here are the messages I get. "No acceptible C compiler in path"... "No targets specified and no makefile found. Stop."

---

### Post by burlap on 2005-03-10
General advice...

Check [Ubuntu wiki](http://www.ubuntulinux.org/wiki/FrontPage/) or [Ubuntu guide ](http://ubuntuguide.org/index.html) for information.

Before you start downloading: each distro (Ubuntu also) comes with a lot of software. First check Applications menu, where you can find basic music or movie player (you can find information on how to make it work with mp3 or divx on the above pages), email client, browser, office program, zip tools, graphics programs and many more. If you don't like them - look for something else. 

And before you compile anything (to do it you need a lot of packages - like gcc, autoconf and libraries - usually "dev" packages - as necessary for specific program) check the repositories (synaptic). If something is missing - on the above pages there are addresses of different repositories, where you can find a lot of nice software. And if you download a program, first check if there is a deb package (binary) available (sometimes they won't work, depends on a distro).

---

### Post by bored2k on 2005-03-10
*No compilation needed*

**Music**
beep-media-player
stream-tuner [Shoutcast]
**Video**
vlc
mozilla-mplayer [quicktime trailers ; web streams]
**Video Editing**
Avidemux
dvd:rip

**Word Processing**
Abiword [light]
Leafpad [even lighter]
**SpreadSheet**
Gnumeric

**File Sharing**
bittornado-gui
azures [azureus.sourceforge.net - java needed]
Limewire [limewire.org]
Nicotine [soulseek client]

**File Management**
rox-filer [light]
emelfm [even lighter]

**Net**
Amsn [msn wannabe]

**Desktop Environments**
Xfce4 [light, resembles gnome]
KDE [not light, but appeals to certain people -not me]

**Utilities**
Gnomebaker [gnome burning app]
K3B [kde burning app - resembles nero]

---

### Post by Kimm on 2005-03-10
> 
Here are the messages I get. "No acceptible C compiler in path"... "No targets specified and no makefile found. Stop."


well, thats means you havent installed a C compiler yet... run this in console...

> 
sudo apt-get -f install gcc


then I'd suggest installing g++ to...

> 
sudo apt-get -f install g++


then try running ./configure again :)

---

### Post by JMY1983 on 2005-03-10
[QUOTE=Kimm]well, thats means you havent installed a C compiler yet... run this in console...



then I'd suggest installing g++ to...



then try running ./configure again :)[/QUOTE]
 Just ran configure again but it still says I have no makefile.

---

### Post by Kimm on 2005-03-11
:-k well... as far as I know ./configure is supose to create the makefile...
try downloading the source again...

---

### Post by hashimoto on 2005-03-11
Did you unzip the source package?

---

### Post by ohman11 on 2005-03-11
[QUOTE=Kimm]if you mean like Outlook then theres one allredy installed, Evolution, its cinda good.



that is also alredy installed... try running gzip, it should open archives automaticly however



Run synaptic and look for a program called XMMS, when you find it mark it for installation and click apply. If you want something more powerfull however, have a look at beep-media-player, its based on XMMS and personaly I think its better...
make a search for beep-media-player on google. If you to, try compiling it from source (allways good to know how).

Just extract the archive and do this...



it does take a while to compile, but well, you'll be facing one good looking media player when its done.[/QUOTE]
 I tried to install this too and I got this message saying libglade 2.0 not found but I did check and it says it is installed.

1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for libglade-2.0 >= 2.3.1... Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
configure: error: Cannot find libglade

---

### Post by cutOff on 2005-03-14
Hi

I think what you need **libglade2-dev**.

Good Luck

---

### Post by ssam on 2005-03-14
vector graphics:
inkscape

video:
xine-ui

cd ripping (with lots of options)
grip

music players:
beep-media-player     (modern version of xmms)
amarok                     (some people like it (warning will install lots of kde stuff))
muine                      (nice and simple)

games:
freeciv              (you might need to find a how to on running it, you have to start a server and then the client)
pingus                (lemings clone)

---

