---
title: "Help with Perl script"
date: 2011-02-11
forum: General Help
---

### Post by inverser on 2011-02-11
Hey, how's it going? I'm using this script to run a few commands when my system goes idle:

```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {
#When Ubuntu idles these commands will run
system("dtop3");
system("firefox www.d5-p.com/geo/ -fullscreen");
system("xdotool key ctrl+shift+s"); 
} elsif (m/^\s+boolean false/) {
#when Ubuntu returns from idle these commands will run
system("wmctrl -c "geolocation"");
}
}
```
And it works beautifully to get the compiz screensaver, which I have bound to ctrl+shift+s, running. But the script does not run dtop3 (alias for switch to desktop #3) or open firefox.

Does anyone know why it's not working? Did I mess up syntax?

---

### Post by inverser on 2011-02-14
Bump. 

I'd really appreciate the help. There's gotta be someone that knows Perl on the forums.

---

