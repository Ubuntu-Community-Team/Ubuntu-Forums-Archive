---
title: "Default Resolution"
date: 2006-04-21
forum: General Help
---

### Post by jonnymccullagh on 2006-04-21
My default resolution is set to 1600x1200 which is a little big even with good eyesight. I would prefer 1280x1024 but which I configure the desktop display it always reverts back  to 1600x1200 when I restart. ](*,) 
I have seen other threads about this on gnome. I figure it is something to do with /etc/x11/xorg.conf - can I safely remove all occurences of 1600x1200? Some of the text is shown below:
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Monitor		"GDM-5402"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

So my questions are:
1. How can I esily fix this?
2. Why does this not work as a newbie would expect?
3. Will it be fixed in Dapper?

Thanks in advance,
jonny

---

### Post by cgjones on 2006-04-21
You should be able to remove each instance of "1600x1200" and then restart the computer or just restart the x server.

---

### Post by jonnymccullagh on 2006-04-22
That worked fine but this could be much better - I wouldn't expect a newbie "computers for dummies" to have to do this.
Thanks for the help,
j

---

