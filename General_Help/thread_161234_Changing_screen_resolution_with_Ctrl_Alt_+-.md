---
title: "Changing screen resolution with Ctrl Alt +/-"
date: 2006-04-16
forum: General Help
---

### Post by harisund on 2006-04-16
Hello people

Simple. What I want to do is just this: change the screen resolution using Ctrl Alt + and Ctrl Alt -. 

My xorg.conf file has the following details:
 	SubSection "Display"
		Depth		16
		Modes		"1280x960"	"1024x768"
	EndSubSection

I am able to use gnome-display-properties to successfully choose any resolution between 1280x960 and 640x480, and evrything works absolutely fine. 

But how do I change it using Ctrl Alt + and Ctrl Alt -? Those two don't work. I want to be able to chage my resolution like that, and not going through the gnome-display-properties panel. 

Thanks !

---

### Post by z_diver on 2006-04-16
Mine works if I use Ctrl+Alt in addition to the + or - on the numpad but not if I use the keys next to the number keys on the top row.  

Hint: to make it real big right off the bat, hit the - key first.  It loops around.

---

