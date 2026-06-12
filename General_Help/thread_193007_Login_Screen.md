---
title: "Login Screen"
date: 2006-06-09
forum: General Help
---

### Post by wizzkid on 2006-06-09
When I start my computer, the login screen is too big, but once login to the system, everything is okay. I installed 915resolution to fix my resolution to 1240X800. how can i fix the login screen to make it 1024X800? :) i think its on /etc/rc*? right? but there are many /etc/rc* there, i dont know which ?

Any suggestions and help will be highly appreciated.

Thanks.

---

### Post by TuxCrafter on 2006-06-09
take a look in /etc/X11

and try to change the file xorg.conf as root

look for the Section "Screen"

and try changing these lines to your resolutions

```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
```

haven't try my own custom resolution yet so don't now if it works

---

