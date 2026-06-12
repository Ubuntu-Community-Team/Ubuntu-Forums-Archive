---
title: "Qt fonts not being antialiased"
date: 2009-11-05
forum: General Help
---

### Post by itsjareds on 2009-11-05
I installed Skype so that I could share a webcam of my desktop with my friend. The problem is, the fonts on Skype are ugly. I know it's not a Skype-specific problem because I saw this in Virtualbox-OSE in Karmic beta. I installed 'qt4-qtconfig' which is the settings interface for KDE fonts (I think) and I can't figure out what to do to get antialiasing working.

Pictures speak better than words so I attached a few screenshots.

I've searched through these forums but none of the topics were about antialising.. all I could find was over-antialiasing and complete bug-out issues.

Hope someone has an answer. Thanks.

---

### Post by itsjareds on 2009-11-05
Found the solution. Just had to manually specify what my Gnome font settings were in ~/.fonts.conf.

~/fonts.conf
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<match target="font">
		<edit name="rgba" mode="assign">
			<const>rgb</const>
		</edit>
		<edit name="antialias" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>hintfull</const>
		</edit>
		<edit name="hinting" mode="assign">
			<bool>true</bool>
		</edit>
	</match>
</fontconfig>
```

---

