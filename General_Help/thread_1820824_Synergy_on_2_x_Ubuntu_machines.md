---
title: "Synergy on 2 x Ubuntu machines"
date: 2011-08-08
forum: General Help
---

### Post by Gordonisnz on 2011-08-08
Hello.

I've dumped my WIN XP box (old...)  & now have 2 Linux / Ubuntu machines - trying to install Ubuntu.

my old Ubuntu already has Quicksynergy  & Ive installed it on my 2nd machine (it does have internet access now, So i know it is connected to my Router.

I activate both Quicksynergy..

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

This just says " On the server  " >>Move the mouse to the edge of the Host screen -- it should now appear on the client screen.

however nothing happens.


ISSUE - On my old Win box, I could see an icon at the bottom of the screen turn green - When it was actually connected.  There isn't any icon as such or "status" - On either Ubuntu machines.

Is there a debug  or other way - to know its connecting / trying to ?
(OR - do i need to specify a port number ?  & *WHICH* port ? - how do i find out ?)



PS - On one machine i altered something & get an error :-

> 
.....etc..    .quicksynergy/synergys: File not found.


How do I find the original directory ? (Tried to de-install & re-install, but didnt work..)

---

### Post by Gordonisnz on 2011-08-08
Ive fixed the error (looked on the other machine & copied the directory :) )

But still no go. - both are activated / on - but i cant get my curser from the main PC to the client..

---

### Post by Gordonisnz on 2011-08-09
Hi.

On my host machine / Server - i have this :-

> 
gordon@gordon-desktop:~$ synergys -f
INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64
DEBUG: synergys.cpp,1051: opening configuration "/home/gordon/.synergy.conf"
DEBUG: synergys.cpp,1062: configuration read successfully
DEBUG: CXWindowsScreen.cpp,847: XOpenDisplay(":0.0")
DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00000000
DEBUG: CXWindowsScreen.cpp,117: screen shape: 0,0 1360x768 
DEBUG: CXWindowsScreen.cpp,118: window is 0x05e00004
DEBUG: CScreen.cpp,38: opened display
WARNING: synergys.cpp,505: cannot listen for clients: cannot bind address: Address already in use
DEBUG: synergys.cpp,519: retry in 10 seconds
WARNING: synergys.cpp,505: cannot listen for clients: cannot bind address: Address already in use
DEBUG: synergys.cpp,519: retry in 10 seconds
WARNING: synergys.cpp,505: cannot listen for clients: cannot bind address: Address already in use
DEBUG: synergys.cpp,519: retry in 10 seconds



Is there a special DEBUG area of Synergy website so we can go to & self-debug things & understand  step-by-step what to do to fix it..

---

### Post by Gordonisnz on 2011-08-09
Hmm Killed all processes of Synergy on both PC's.

loaded synergys on 1, & synergyc (IP NUMBER).

still no go...

Shall I give up ?  Is there a debug screen ? 
(Listening for synergy client on ip xx/xxx/xxxx  port xxx etc...  )
(Listening for synergy server on ip xx/xxx/xxxx  port xxx  etc...  )

---

### Post by Grenage on 2011-08-09
It'll be worth posting your config files and other details.

---

### Post by Gordonisnz on 2011-08-09
/home/gordon/.quicksynergy/synergy.conf   EDIT :- server PC

> 
section: screens
    gordon-desktop:
    gordon-System-Product-Name:
end
section: links
    gordon-desktop:
        right = gordon-System-Product-Name
    gordon-System-Product-Name:
        left = gordon-desktop
end



EDIT 2 :- what "other" information ?

---

### Post by Gordonisnz on 2011-08-09
FIXED...

Not sure how - But i re-installed quicksynergy (visual programme - whatever the word is) & restarted that..

Its now working.

---

### Post by thunderbirdje on 2011-08-28
Had the same problem, by reading the tutorial [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto) I have managed to get it to work! Thanks!

---

