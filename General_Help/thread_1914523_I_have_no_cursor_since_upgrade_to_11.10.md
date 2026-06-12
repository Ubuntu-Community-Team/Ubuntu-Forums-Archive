---
title: "I have no cursor since upgrade to 11.10"
date: 2012-01-24
forum: General Help
---

### Post by Jonners59 on 2012-01-24
I upgraded my PC to 11.10 - 64-bit and since then I have lost the cursor.  Well not literally, I just can not see it.  It appears in some parts of the screen and when I pass over some of the "switches" on windows they change shade, but otherwise, it ain't there to see....

It is directly wired in to the mouse socket, not even a USB, not that it makes any difference.

Any help please?

---

### Post by Jonners59 on 2012-01-30
Any HELP please...???:(:(:(:(:(:(:confused:

Video card is

ATI Tech Inc. RS690 Radeon X1200 series

---

### Post by Jonners59 on 2012-03-13
Fixed.  See also thread 1922319:

Fixed by following this:
  	 	 	 	 	 	   [COLOR=#222222][FONT=Ubuntu Mono, Ubuntu Beta Mono A, monospace][SIZE=2]sudo apt-get --reinstall install humanity-icon-theme gnome-icon-theme[/SIZE][/FONT][/COLOR] [COLOR=#333333][FONT=Ubuntu Beta, UbuntuBeta, Ubuntu, B, serif][SIZE=2]If your icons are still not fixed you can also try[/SIZE][/FONT][/COLOR]
 [COLOR=#222222][FONT=Ubuntu Mono, Ubuntu Beta Mono A, monospace][SIZE=2]sudo apt-get --reinstall install gnome-icon-theme-full[/SIZE][/FONT][/COLOR] [COLOR=#333333][FONT=Ubuntu Beta, UbuntuBeta, Ubuntu, B, serif][SIZE=2]You can also try removing/moving [/SIZE][/FONT][/COLOR][COLOR=#222222][FONT=Ubuntu Mono, Ubuntu Beta Mono A, monospace][SIZE=2]~/.icons[/SIZE][/FONT][/COLOR]

Also look at changing the Theme to Radienze

---

