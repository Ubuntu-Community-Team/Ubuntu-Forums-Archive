---
title: "Resolution Stuck"
date: 2006-05-20
forum: General Help
---

### Post by white_tiger_daniel on 2006-05-20
Hi.

Well I got my second computer a while ago.  I only have one monitor and I was switching the monitor but now it's stuck on 640x480 on 60hz.  When I try and switch it back those are the only options in the menus.

Any help?

Dan :-({|=

---

### Post by empthollow on 2006-05-20
gnome's screen resolution utility reads information from the /etc/X11/xorg.conf file.  if the resolutions are not listed in that file, they do not show up in the configuration tool. try adding something like this to your * section "screen" * of your xorg.conf file:

```

DefaultDepth     24
SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

```

you will need to restart X after doing this.  you can log out or force quit by
ctrl + alt + backspace

---

### Post by white_tiger_daniel on 2006-05-20
Thanks man I'll try it out soon. :) 

Dan

---

### Post by frup on 2006-05-20
can you set that to non-standard resolutions then? like could i make a 1500*1500 square resolution if i wanted to? is the depth the amount of colours?

---

### Post by empthollow on 2006-05-20
i believe you can set it to non-standard, though i've never tried and yes depth is  the amount of colors and 24 is the max though you could specify 32, it will still use 24 (at least that's what i've read)

---

