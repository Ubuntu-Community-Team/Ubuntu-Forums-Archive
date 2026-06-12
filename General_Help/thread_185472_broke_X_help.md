---
title: "broke X help"
date: 2006-05-31
forum: General Help
---

### Post by nalgene on 2006-05-31
Hello the title says it all i treid to install ati drivers and i guess i broke it.  it says xorg is not installed or something

dpkg-reconfigure xserver-xorg does not work.  can some one help i would hate to  do a clean install..

thanks..

---

### Post by Patrick-Ruff on 2006-05-31
if your gettting a terminal at start, instead of the actual desktop enviornment or logon screen, do sudo, then type 'startx'

---

### Post by nalgene on 2006-05-31
[QUOTE=Patrick-Ruff]if your gettting a terminal at start, instead of the actual desktop enviornment or logon screen, do sudo, then type 'startx'[/QUOTE]
When i do sudo starx i get this

Fatel Server error
no screens found
X10:fatel 10error 104(connection reset by peer) on xserver"0:0"
after 0 requests 00 known processed) with 0 events reamaning

---

### Post by Nikos.Alexandris on 2006-05-31
[QUOTE=nalgene]Hello the title says it all i treid to install ati drivers and i guess i broke it.  it says xorg is not installed or something

dpkg-reconfigure xserver-xorg does not work.  can some one help i would hate to  do a clean install..

thanks..[/QUOTE]


OK... 

I upgraded through the net... Everything seemed to work fine and after reboot the gdm wouldn't start.

Trying to reconfigure somehow the gdm was unsuccesful.

I removed all the fglrx related packages (for ATI graphic card) and installed them manually again.

It worked...

!

Maybe this could help U!

Cheers...

---

### Post by nalgene on 2006-05-31
i'm still a newb, can you explain how i can uninstall all the ati drivers using the terminal only.

But he porblem with dpkg-reconfigure is that it says xorg is not installed can reinstall this through the net, and what do i have to sudo apt to install it again

thanks..

---

### Post by nalgene on 2006-05-31
Heresd what i tried to do, i tried 

sudo apt-get install xorg-driver-fglrx 

to reinstall xorg, however i get another error

i get 
dpkg rename invlolves overwriting '/usr/lib/libGL.so.1' with
diffrent file 'usr/lib/fglrx/libGL.so.1.xlibmesa',
not allowed


edit i fixed what i did was mv /usr/lib/libGL.so.1, and it let me isntall xorg driver..

---

