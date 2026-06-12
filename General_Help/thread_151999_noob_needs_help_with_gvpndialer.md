---
title: "noob needs help with gvpndialer"
date: 2006-03-29
forum: General Help
---

### Post by blx_286 on 2006-03-29
after searching through the threads and beating my head against the wall, i finally got the cisco vpn client installed and working.

i would like a gui connection manager for vpn, so i installed network-manager using synaptic. it didn't create any type of menu entry or launcher. i tried to launch it in terminal and nothing happens, it just returns to the prompt with no error messages. so i uninstalled it.

i thought i might use vpnc, but i think i read the gui is kde and i didn't want to install a bunch of kde stuff just to run one app in gnome.

so now i am trying the gvpndialer and i cannot get it to install. i read in another thread that i need expect, so i installed that, using synaptic. the readme says i need gnome2 libraries and pcre libraries. i installed libpcre3 thinking that was the pcre libraries it wants, but i'm not sure. i also don't know which packages, in synaptic, to select for gnome2.

on the gvpndialer forum at [https://sourceforge.net/forum/forum.php?thread_id=1228575&forum_id=391663](https://sourceforge.net/forum/forum.php?thread_id=1228575&forum_id=391663) i read that i need to do the following to install it:

./configure
make
su
make install

when i try ./configure i get the error below. is that because it's not in the directory? 

tclark@blackhole:~/Temp/gvpndialer-1.1$ ./configure
bash: ./configure: No such file or directory
tclark@blackhole:~/Temp/gvpndialer-1.1$ ls
acconfig.h  autom4te.cache  configure.in        NEWS     src
aclocal.m4  ChangeLog       gvpn_dialer.glade   pixmaps  stamp-h.in
AUTHORS     config.h        gvpn_dialer.gladep  po       Status-Dock.png
autogen.sh  config.h.in     Makefile.am         README   TODO
tclark@blackhole:~/Temp/gvpndialer-1.1$

can someone let me know what i am doing wrong? should i just ditch gvpndialer and the cisco client and try vpnc and the kde gui? ](*,) 

thanks,
tim

---

### Post by bernardfrancois on 2006-03-29
When you do **./configure**, make sure there is a file *configure* in your working directory. You can execute **find -name configure** in the topmost directory of the gvpndialer archive you unpacked, it will show you the path of the configure executable (if available).

---

### Post by blx_286 on 2006-03-29
thanks for the reply. i could see more files in the directory using the gui file manager than i could in terminal. using the gui, i changed the permissions and here is what shows in terminal.

.           autogen.sh      configure.in        pixmaps     Status-Dock.png
..          autom4te.cache  gvpn_dialer.glade   po          TODO
acconfig.h  ChangeLog       gvpn_dialer.gladep  README
aclocal.m4  config.h        Makefile.am         src
AUTHORS     config.h.in     NEWS                stamp-h.in

i've had to fight with the wireless card and fight to get the vpn working. i'm not going to fight this just for a gui. besides i went back and looked at the website and the files look like they are from october of 2005.

this is an old laptop that dual boots, so i'll just keep windows for work and ubuntu to play on the net. the only drag is that i have a six gig hard drive with 2 gig for ubuntu and 4 for windows. ubuntu has run out of drive space twice, but i now have 100 mb free.

thanks again.

---

### Post by den benne on 2006-04-05
hey, try this:

download the "i586.rpm" from [sourceforge](https://sourceforge.net/project/showfiles.php?group_id=114566)

and then use "alien" to convert it to a deb-file like this:
(assuming you have alien installed, if not just install it with synaptic)

```

fakeroot alien ****.rpm

```

then install it like this:
```

sudo dpkg -i ****.deb

```

now you should be able to use the program with the command
```
sudo gvpndialer
```

PS: I first installed the pcre library files using synaptic
and when I tried to execute gvpndialer it said he could'nt find "libpcre.so.0"
I did a search in my system and I found this file "libpcre.so", so this is what I did:
I went to the folder /usr/lib where this file is situated and made the missing file, using the existing one
```
sudo cp libpcre.so libpcre.so.0
```
and now it works

---

### Post by shadow07 on 2006-04-06
@den benne:

I completely forgot about alien.  converting it to a deb package worked.  I had the older version installed, which required libpcre (and I already made a sym link.)

---

