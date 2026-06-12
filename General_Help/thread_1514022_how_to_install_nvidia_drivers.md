---
title: "how to install nvidia drivers?"
date: 2010-06-20
forum: General Help
---

### Post by Mogwuy on 2010-06-20
So I got past my first issue of getting Steamed installed and when I launch any games I notice that its laggy (very choppy). So googled around and it seems alot of people found it was there driver for there graphics card. So I went and downloaded a driver from the nvidia site for my card. And can't get installed.

So I googled more went through tons of forums and they all seem to say the samething which is to open a terminal and type the following:

$ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] purge nvidia[COLOR=#000000]*****[/COLOR]to remove any previous versions of nvidia drivers then
[FONT=monospace]
[/FONT]blacklist nouveau --- to block whatever that is, then

$ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] nvidia-current <---which im assuming is getting the latest driver

$ [COLOR=#c20cb9]**sudo**[/COLOR] modprobe nvidia-current <--- I managed to do this once...
I tried to uninstall and reinstall abunch cause it was failing here..
it wouldn't recognize the command or it would give me an error

$ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**lsmod**[/COLOR] [COLOR=#000000]**|**[/COLOR] [COLOR=#c20cb9]**grep**[/COLOR] [COLOR=#660033]-i[/COLOR] nvidia <--- I entered this and it didn't seem to do anything..
.did I miss something do I need to open a doc somewhere to see what this says?
$ [COLOR=#c20cb9]**sudo**[/COLOR] nvidia-xconfig <----this didn't do anything either just errored on me. I can't remember the message

All sites have a variation of this...I've gone through several different methods and nothing. 
Under my hardware drivers it doesn't show any drivers at this point. I added app for nvidia, which doesn't appear to help...

Any ideas on how to do this properly? Did I screw something up? Can anyone help me, a distraught ubuntu beginner? 
I'm using a Geforce9600 Nvidia PCI 2.0 express card. Running a dual core intel processor, with 4gigs of ram (not sure if linux reads it all).  I'm running the 32bit version of Ubuntu 10.04 (Lucid Linux). 

Any help is appreciated!

---

### Post by Mogwuy on 2010-06-20
Just an update. I managed to get a driver installed. However in the Hardware Drivers screen it tells me its install but not activated. So now my question is how to activate it.

---

### Post by wojox on 2010-06-20
You didn't install it correctly. It should activate when you install. Did you reboot your computer?

---

### Post by Mogwuy on 2010-06-20
Yeah I did

---

### Post by wojox on 2010-06-20
Try this link

[http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx)

---

### Post by Mogwuy on 2010-06-20
Well...i think that worked...though i'm not totally sure. It doesn't list any drivers under the hardware drivers page, but it says it set to direct rendor now..

EDIT: ok yeah it worked. My games are no longer choppy. Thanks wojox!

---

