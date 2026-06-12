---
title: "Need help resolving a .lircrc file"
date: 2011-10-14
forum: General Help
---

### Post by voncloft on 2011-10-14
Recently I bought a IR Remote from newegg....got it to work long story short.

I am running ubuntu 11.10 and would like to run multiple programs with one program assigned to one single button.  What I mean is I would like to run gedit (keep it open).. run totem (while keeping gedit open)...open thunderbird (with gedit and totem both open)....etc...

I can "sort of" do that now....with the exception of totem and thunderbird...I can open totem...but thunderbird will not open until totem is closed...and gedit will not open until totem or thunderbird is closed.

below is my configuration file of my .lircrc file

-----------------------------------------------------------
      begin
           button = KEY_1
           prog = irexec
           config = firefox %u
	   repeat=0
	   mode = irexec
      end
       begin
           button = KEY_2
           prog = irexec
           config = totem
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_3
           prog = irexec
           config = transmission-gtk %U
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_4
           prog = irexec
           config = thunderbird
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_5
           prog = irexec
           config = gedit
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_6
           prog = irexec
           config = gnome-terminal
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_7
           prog = irexec
           config = xdg-open /media
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_8
           prog = irexec
           config = synaptic-pkexec
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_9
           prog = irexec
           config = /usr/bin/update-manager
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_0
           prog = irexec
           config = /usr/lib/indicator-session/gtk-logout-helper --logout
	   repeat=0
	   mode = irexec
      end
      begin
           button = Hash
           prog = irexec
           config = /usr/lib/indicator-session/gtk-logout-helper --shutdown
	   repeat=0
	   mode = irexec
      end
      begin
           button = Star
           prog = irexec
           config = /usr/lib/indicator-session/gtk-logout-helper --reboot
	   repeat=0
	   mode = irexec
      end
      begin
           button = KEY_UP
           prog = irexec
           config = xte 'mousermove 0 -10'
	   repeat = 1
      end
      begin
           button = KEY_DOWN
           prog = irexec
           config = xte 'mousermove 0 10'
repeat = 1
      end
      begin
           button = KEY_RIGHT
           prog = irexec
           config = xte 'mousermove 10 0'
repeat = 1
      end
      begin
           button = KEY_LEFT
           prog = irexec
           config = xte 'mousermove -10 0'
repeat = 1
      end
      begin
           button = KEY_OK
           prog = irexec
           config = xte 'mouseclick 1'
repeat = 1
      end

-----------------------------------------------

any advice on this would really be appreciated.

---

