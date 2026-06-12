---
title: "cli to open a file with the default application"
date: 2009-11-17
forum: General Help
---

### Post by estyles on 2009-11-17
Is there any way to, via the command line, open a file using whatever is the default application for that type of file?  Frex, in nautilus, you can double-click a .sln file, and it will open in MonoDevelop.  Double-click a text file, and it will open in gedit.  

Is there a command-line switch to nautilus such that you could call it with, like nautilus -openfile blah.txt?  Or a system-wide command, like open blah.txt?  Or, maybe a script I could download or use as a reference to check the listing (wherever it may be) or associated apps and pick the one to open the file with?

The reason I specifically want it, is that I would like to create a desktop icon called "Open on Second Display" that basically does: DISPLAY=:0.1 && open file.  Currently, it works okay for applications, doing DISPLAY=:0.1 && $1.  Where $1 is the application whose icon you drop on the launcher.  But it doesn't work for other launchers (it just opens the launcher as a text file for some launchers, or else just pukes and ignores it for other launchers).

If anyone knows of a cli way to open a file (without knowing the associated app), or any other way of doing what I'm trying to do (other than making 2 sets of launchers for everything, with 1 launcher linking to a shell script that opens it on the second monitor - which is what I've fallen to doing for now), I would appreciate any guidance...

---

### Post by Simian Man on 2009-11-17
There are 2 ways I know of: 'xdg-open' and 'gnome-open'.  xdg-open is better since it should work on any desktop following the FreeDesktop.org standards.

I always alias xdg-open to "o" for fast usage :).

---

### Post by estyles on 2009-11-17
Thanks for the help!  That's definitely a useful command.  :D

I'm getting closer, but still not there yet.  gnome-open doesn't seem to know what to do with .desktop files (i.e. launchers) or apps.  I might be able to script a check if the file is executable or not (not sure how to do that, but can probably figure it out).

So, the main problem would be .desktop files and files with no associated application (which I would like to open in gedit).  Do you know if there's a way to check if the file has an associated app or not?

For .desktop files maybe grep for a "Exec" or "URL" field in the file?

Man, I'm really not good enough with bash scripting for this...

---

### Post by tom4everitt on 2009-11-17
The bash construct to use to check if a file is executable is 

if [ -x file ]; then
something
fi

where something is what you want to do if the file is executable

---

### Post by estyles on 2009-11-17
Awesome, thanks for the help.  Here is the script so far, for anyone that's interested:

```
#! /bin/bash

if [ -x "$1" ]; then
	DISPLAY=:0.1 && "$1"
else

case $( DISPLAY=:0.1 && xdg-open "$1" ) in
	2 ) echo "does not exist: " $1;;
	3 ) DISPLAY=:0.1 && gedit $1;;
	* ) echo "error: " $1;;
esac
fi

exit 0
```

I've got a launcher on the desktop pointed to that script, and it will succesfully open any file or executable that is dropped on it, with the exception of .desktop files.  It currently opens those in gedit.  I'm pretty sure I can successfully check the desktop files for a URL or command, it'll just take a little more scripting.  Will update this post when I fix it.

Thanks for the help, both of you!

---

### Post by estyles on 2009-11-17
Okay, here's the final script, in case anyone is searching and happens to come upon this thread. Just create a launcher on your desktop that points to this script, then drag an icon on it to launch on your second x display (you might have to change the name of your x display - mine is :0.1.  Yours may well be :1 or something else.  Terminal apps probably won't launch correctly, nor will firefox (firefox refuses to launch a second instance on a different x display no matter what you do), or any of the icons that Nautilus puts on your desktop - those icons don't exist as files, so when you drop them on the icon, the input is null.

```
#! /bin/bash

# if the name contains .desktop, that generally means it's a launcher
# look for URL= or Exec= and strip out the path
if [[ $1 == *.desktop ]]; then
	s=`cat "$1" | grep URL= | sed 's/URL=//'`

	if [ ${#s} -ne 0 ]; then
		DISPLAY=:0.1 && nautilus "$s"		
	else
		s=`cat "$1" | grep Exec= | grep -v TryExec= | sed 's/Exec=//'`
		DISPLAY=:0.1 && $s
	fi

	exit 0
fi

#check if it's executable, then execute it, or else send it to xdg-open, which
#will check for the preferred app
if [ -x "$1" ]; then
	DISPLAY=:0.1 && "$1"
else

case $( DISPLAY=:0.1 && xdg-open "$1" ) in
	2 ) echo "does not exist: " $1;;
	3 ) DISPLAY=:0.1 && gedit "$1";;
	* ) echo "error: " $1;;
esac
fi

exit 0
```

---

