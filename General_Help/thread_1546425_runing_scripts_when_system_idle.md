---
title: "runing scripts when system idle"
date: 2010-08-05
forum: General Help
---

### Post by n00ne on 2010-08-05
I'm trying to write a script to run motion when the computer is idle
but for some reason the script I found online doesn't work.

I tried to write a simple command to put some echo in a file
when the screen server starts and stops but this doesn't work also.

this is the script I'm using  -
```

#!/usr/bin/perl

#open (IN, "$cmd |");
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
	 if (/^\s+boolean true/) {
		#when Ubuntu idles these commands will run		
		system("echo 'vvvvvvvvvv' >> /home/user/test.test");
		#system("COMMAND"); #you can remove or add more commands by adding another system("COMMAND"); line
	} elsif (/^\s+boolean false/) {
		#when Ubuntu returns from idle these commands will run, delete these two system lines if not wanted/needed
		system("echo 'zzzzzzzz' >> /home/user/test.test");
		#system("COMMAND");
	}
}


```

any one know why it shouldn't work ?
10x
Yoni

---

### Post by estragib on 2010-09-06
Steve_54 suggested in [HOWTO: Run a Program or Windows Screen Saver when System is Idle]("http://ubuntuforums.org/showthread.php?t=1029704"):

> Mine quit working with 9.10. I changed member='SessionIdleChanged' to member='ActiveChanged' and now it works again.

I've tested this and it does work on a current lucid. To conveniently test this yourself (without waiting for the idle counter), manually activate the screen saver with:

```
dbus-send --type=method_call \
          --dest=org.gnome.ScreenSaver \
          /org/gnome/ScreenSaver \
          org.gnome.ScreenSaver.SetActive \
          boolean:true
```

---

