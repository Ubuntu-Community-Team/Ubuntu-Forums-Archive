---
title: "List of Compose key combinations?"
date: 2006-05-09
forum: General Help
---

### Post by silhouette on 2006-05-09
Is there anywhere I can find a list of letters and symbols I can type using the Compose key? I Googled this and came across various sources that pointed to the /usr/share/X11/locale/iso8859-1/Compose file. First of all, I know Kubuntu uses kbd for the keyboard layout, but does it use X for other keyboard stuff -- is this file in fact used? If so: What about the en_US.UTF-8 Compose file -- if the ISO 8859 file is used, how can I tell Linux to use the UTF-8 one?

Thanks!

---

### Post by ComplexNumber on 2006-05-09
do you mean a character set type thing so that you have a list of western alphabetic, greek, japanese, hebrew, etc characters that you can cut and paste into text editors and such like? its in the menu. i can't remember the exact name of the kde one, though, unfortunately. maybe someone else can

---

### Post by silhouette on 2006-05-10
No, I already know about KCharSelect, but I don't want to have to open it every time I want to type a symbol, even for the rarer ones. Instead I've decided to use deadkeys -- only I'm using a Compose key to activate deadkey mode, instead of changing my keyboard layout. Correct me if I'm wrong, but as I understand it, one can type (or "compose") more symbols this way.

That said, it's fairly obvious that <'><e> = é and <~><n> = ñ -- but what about a trademark symbol, or curly quotes, or an emdash, or an ellipsis? So it would be helpful if I could get a list of all the possible deadkey combinations one can Compose. (Or at least tell me how I can type these, and how you know this.)

If there is no such list I suppose I can edit /etc/X11/xkb/symbols/us, but of course that would take longer :)

---

### Post by shecky on 2006-05-24
There are lists for compose key combos in /usr/share/X11/locale/, e.g. /usr/share/X11/locale/iso8859-1/Compose.

---

### Post by kalle314 on 2006-10-22
I am not sure what Compose key combination that my system uses.
My locale is sv_SE.UTF-8 I guess, at least that is whay I have in my LANG variable. In the file "/usr/share/X11/locale/compose.dir" it says something about "en_US.UTF-8/Compose sv_SE.UTF-8" so I thought that maybe I am using en_US.UTF-8/Compose, but that can not be the case, since many of the combinations there doesn't work. 
For example, I couldn't type ° (degree symbol) with compose+o+o suggested there, and neither with the combinations in iso8859-1/Compose for this symbol (compose+^+0, compose+*+0).
However, many other combinations work, for example compose+R+O=®, compose+x+x=×.

In the thread [http://ubuntuforums.org/showthread.php?t=209115](http://ubuntuforums.org/showthread.php?t=209115) it is instead suggested that "export GTK_IM_MODULE=xim" should be added to /etc/environment and  /usr/share/X11/locale/en_US.UTF-8/Compose copied to  ~/.XCompose, but that instead took away all my compose key combinations.

EDIT: I discovered that simply "^+0" gives me a °, but my problem remains, a lot of usual compose key combinations doesn't work, for example compose + 3 + 4 does not result in ¾.

---

### Post by Yeti can't ski on 2008-02-29
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=4429013](http://ubuntuforums.org/showthread.php?p=4429013) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a very old post, but I can tell that quoted threads resolve the issue of key combinations on Ubuntu 7.10. Best regards.

---

