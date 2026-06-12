---
title: "no templates installed, Wrong file Path ?"
date: 2009-11-26
forum: General Help
---

### Post by Ronok on 2009-11-26
Hi

Right Click, Create Document, no templates installed


some background:
Searched for "Templates" folder, couldn't find it

so I made a "Templates" folder in:
/home/myname/afolder/a Folder With Space Number & Caps in Name/Templates

and put some files in it e.g: "OpenOffice.stw"

then I went to:
**/home/myname/.config/user-dirs.dirs**
and made "user-dirs.dirs" point to the right place in this way:

**Before:**
XDG_TEMPLATES_DIR="$HOME/"

**After:**
XDG_TEMPLATES_DIR="$HOME/myname/afolder/a Folder With Space Number & Caps in Name/Templates"


also looked at:
OpenOffice.odt,Tools,Options,openoffice.org,Paths,Templates,edit,add


still Nothing / no templates installed

thinking that maybe it wouldn't let put them where I want 
(file name e.g: "/folder/My 4 Stuff/Templates") ?

I tried to do the same with: "/home/myname/Templates"
**XDG_TEMPLATES_DIR="$HOME/myname/Templates"**


still Nothing / no templates installed

my "/home/" only has "/home/myname/" 
thats it no hidden, and cant make a new folder there


Thanks for looking this over
not sure what is the next step
Thanks
Ronok     [http://www.gongkuo.com/index.htm]("http://www.gongkuo.com/index.htm")

Ubuntu 9.10 (karmic)
GNOME: 2.28.1 
Kernel: 2.6.31-15-generic 
Intel(R) Atom(TM) CPU N280   @ 1.66GHz
openoffice.org 3.1.1

---

### Post by augustuen on 2010-04-10
I had a problem with that my templates didn't show up, and I couldn't seem to fix it, but I finally found out what was wrong: the name of the templates folder changes depending of what language you use on ubuntu, if you use a different language then english, the folder you need to create (or that already is created) has to be called "Templates" in your own language ;)

---

