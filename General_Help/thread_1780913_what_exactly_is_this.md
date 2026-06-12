---
title: "what exactly is this ?"
date: 2011-06-12
forum: General Help
---

### Post by richa5300 on 2011-06-12
I searched for canon i250 drivers in forums.
I got this script from any site made by a unkown person.
HE has mentioned it weired that dont trust me ..this is his site address 
Is this some thing wrong script to install drivers .please anyone help me and tell me what exactly is this 
As I tried to run up without checking it.

[http://gkn.me.uk/i250ubuntu/](http://gkn.me.uk/i250ubuntu/) 

gksudo "aptitude -y install libpng3 libtiff4 cupsys alien" cd /tmp wget [http://download.canon.com.au/bj/i250linux/bjfilteri250-2.3-0.i386.rpm](http://download.canon.com.au/bj/i250linux/bjfilteri250-2.3-0.i386.rpm) wget [http://download.canon.com.au/bj/i250linux/bjfiltercups-2.3-0.i386.rpm](http://download.canon.com.au/bj/i250linux/bjfiltercups-2.3-0.i386.rpm) gksudo "alien --scripts bjfilteri250-2.3-0.i386.rpm" gksudo "alien --scripts bjfiltercups-2.3-0.i386.rpm" gksudo "dpkg -i bjfiltercups_2.3-1_i386.deb bjfilteri250_2.3-1_i386.deb" gksudo "ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3" gksudo "ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2" gksudo "/etc/init.d/cups restart"

---

### Post by Autodave on 2011-06-12
> **richa5300 said:**
> I searched for canon i250 drivers in forums.
I got this script from any site made by a unkown person.
HE has mentioned it weired that dont trust me ..this is his site address 
Is this some thing wrong script to install drivers .please anyone help me and tell me what exactly is this 
As I tried to run up without checking it.

[http://gkn.me.uk/i250ubuntu/](http://gkn.me.uk/i250ubuntu/) 

gksudo "aptitude -y install libpng3 libtiff4 cupsys alien" cd /tmp wget [http://download.canon.com.au/bj/i250linux/bjfilteri250-2.3-0.i386.rpm](http://download.canon.com.au/bj/i250linux/bjfilteri250-2.3-0.i386.rpm) wget [http://download.canon.com.au/bj/i250linux/bjfiltercups-2.3-0.i386.rpm](http://download.canon.com.au/bj/i250linux/bjfiltercups-2.3-0.i386.rpm) gksudo "alien --scripts bjfilteri250-2.3-0.i386.rpm" gksudo "alien --scripts bjfiltercups-2.3-0.i386.rpm" gksudo "dpkg -i bjfiltercups_2.3-1_i386.deb bjfilteri250_2.3-1_i386.deb" gksudo "ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3" gksudo "ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2" gksudo "/etc/init.d/cups restart"

Here is a thread that I found.  I would install the repository like advised.

---

### Post by richa5300 on 2011-06-18
What does that means? I didnt get it. Sorry but plz specify it. 
Why he mentioned dont trust me , to get access. 
Whether it is safe to install?

---

### Post by lisati on 2011-06-18
Hmmm, the formatting is wonky..... here goes:
```
gksudo "aptitude -y install libpng3 libtiff4 cupsys alien"
cd /tmp
wget http://download.canon.com.au/bj/i250linux/bjfilteri250-2.3-0.i386.rpm
wget http://download.canon.com.au/bj/i250linux/bjfiltercups-2.3-0.i386.rpm
gksudo "alien --scripts bjfilteri250-2.3-0.i386.rpm"
gksudo "alien --scripts bjfiltercups-2.3-0.i386.rpm"
gksudo "dpkg -i bjfiltercups_2.3-1_i386.deb bjfilteri250_2.3-1_i386.deb"
gksudo "ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3"
gksudo "ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2"
gksudo "/etc/init.d/cups restart"

```
Here's my take on what it means:
The first line installs a bunch of stuff that could be useful for installing the drivers: "alien" is a tool that helps with using packages other than the ".deb" format used by ubuntu.
The "wget" lines download a couple of ".rpm" files containing the drivers.
The lines starting 'gksudo "alien...."' convert the files to a form that Ubuntu can use.
The "dpkg" line installs the converted files.
The "ln" lines set do a bit of cross-referencing type stuff with "symbolic links"

Last but not least: the printing system (cups) is restarted. If you're using a newer version of Ubuntu, you might need to change the last line to: ```
sudo service cups restart
```

(p.s. I'm not sure that "gksudo" is needed: sudo should suffice.)

---

### Post by richa5300 on 2011-06-18
ya u r right i guess. as i run it.  
my printer doesnt work so tht was wrong. 
may be its a new ubuntu version as u said.
i have to correct it.:D:D:D:D

---

