---
title: "startup terminal command"
date: 2009-08-17
forum: General Help
---

### Post by mCion on 2009-08-17
So I'm trying to run a terminal command in the startup applications.

When I'm in a terminal I type
```
 /home/miguel/Temp/changer 60
```

And my command executes every 60 seconds

when I put that same command in the command line in startup applications I get an error...

how could I make this work?

Thanks

---

### Post by michy99 on 2009-08-17
What is the error you get?

---

### Post by mCion on 2009-08-17
sorry, should have said "it doesn't run"

---

### Post by mCion on 2009-08-17
does anyone else have any ideas?

---

### Post by credobyte on 2009-08-17
Does it work if you launch it from a shell script ?

launcher.sh
```
/home/miguel/Temp/changer 60
```
Startup -> /path/launcher.sh

---

### Post by mCion on 2009-08-17
created launcher.sh with the command

typed in startup applications

/home/miguel/Temp/launcher.sh

no luck

then tried

sh /home/miguel/Temp/launcher.sh

same luck (none).

why would the command

/home/miguel/Temp/changer 60 

work in the terminal but not in startup applications?

(I got much to learn)
Thanks!

---

### Post by asmoore82 on 2009-08-17
what does the command attempt to do?

I don't think Startup Apps inherit your full Environment...
So they wouldn't automatically be able to interact with DBUS, for example.

---

### Post by mCion on 2009-08-17
Im trying to get a script working so the background wallpaper changes randomly.  I do not want to use applications like wallpapoz

I finally found a code online that works! (when I type it in terminal, perferct)

So I just want it to run when I log in instead of having to go to the terminal everytime to get it running
```
cd $HOME/Pictures/Backgrounds && if ! test "$1" = ""; then if test $1 -gt 0; then while /bin/true; do ls -1 *.jpg | head -n`expr $RANDOM % \`ls -1 *.jpg | wc -l\`` | tail -n1 | echo `pwd`/`xargs` | gconftool-2 -t string -s /desktop/gnome/background/picture_filename "`xargs`" && sleep $1; done; fi; fi
```

....
maybe someone knows some other way to do this

---

### Post by asmoore82 on 2009-08-18
I cleaned up the code you posted and came up with this, saved as "~/bin/wallcycle" :
```
[COLOR="Blue"]#!/bin/bash[/COLOR]

[ -d [COLOR="DarkOrchid"]"$HOME/Pictures/Backgrounds"[/COLOR] ] [COLOR="Red"]||[/COLOR] exit 1
cd   [COLOR="DarkOrchid"]"$HOME/Pictures/Backgrounds"[/COLOR]   [COLOR="Red"]||[/COLOR] exit 127

delay="${1:-300}"
[ [COLOR="DarkOrchid"]"$delay"[/COLOR] -lt  [COLOR="DarkOrchid"]"0"[/COLOR] ] [COLOR="Red"]&&[/COLOR] delay=$(( delay * -1 ))
[ [COLOR="DarkOrchid"]"$delay"[/COLOR] -gt [COLOR="DarkOrchid"]"-1"[/COLOR] ] [COLOR="Red"]||[/COLOR] exit 128

gconftool-2 -s [COLOR="DarkOrchid"]"/desktop/gnome/background/picture_options"[/COLOR] \
	-t string [COLOR="DarkOrchid"]"scaled"[/COLOR]
picturesc=$( ls *.jpg | wc -l )
[COLOR="Red"]while true[/COLOR]
[COLOR="Red"]do[/COLOR]
	picture=$( ls *.jpg | head -n$(( RANDOM % picturesc + 1 )) | tail -n1 )
	gconftool-2 -s [COLOR="DarkOrchid"]"/desktop/gnome/background/picture_filename"[/COLOR] \
		-t string [COLOR="DarkOrchid"]"$PWD/$picture"[/COLOR]
	sleep [COLOR="DarkOrchid"]"$delay"[/COLOR] [COLOR="Red"]||[/COLOR] exit
[COLOR="Red"]done[/COLOR]

[COLOR="Blue"]#End of File[/COLOR]
```
^that works as a startup app for me.

---

