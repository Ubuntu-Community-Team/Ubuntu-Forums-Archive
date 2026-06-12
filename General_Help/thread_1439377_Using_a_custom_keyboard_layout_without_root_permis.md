---
title: "Using a custom keyboard layout without root permissions with X.org"
date: 2010-03-26
forum: General Help
---

### Post by IvarTJ on 2010-03-26
So I have made a personalized keyboard layout like the one described in [this tutorial]("http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html"). It works on both Cygwin and Ubuntu if I replace /usr/share/X11/xkb/symbols/no with my file and then run the command "setxkbmap no -variant noprogdv" - where noprogdv is the name of the layout variant that I have made. I wish to use the same keyboard layout on a computer where I don't have root permissions, and requests for replacing the file have been fruitless.

According to the administrator I should be able to use the -config option on the setxkbmap command in order to use a custom keyboard layout without root permissions. He does not elaborate further on how to use it. Using the -config option on my file results in the message "Couldn't find configuration file '<filename>'," and I fail to understand what kind of configuration file the option requests.

The computer runs the X.Org server.

Thanks in advance.

---

### Post by IvarTJ on 2010-04-17
I found a solution, and relay it here for anyone interested.

My solution was to do “xmodmap -pke > newfilename” on a computer where my custom keyboard layout was enabled, and then send the resulting file to a different computer on which I wished to use it. On that computer I could enable the layout by doing “xmodmap filename”

---

