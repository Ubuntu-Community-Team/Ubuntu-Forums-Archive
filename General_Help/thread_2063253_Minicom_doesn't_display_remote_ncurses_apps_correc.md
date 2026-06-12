---
title: "Minicom doesn't display remote ncurses apps correctly"
date: 2012-09-26
forum: General Help
---

### Post by chaz572 on 2012-09-26
Two different Linux systems I'm working with here....   My development laptop is running Ubuntu 10.04 LTS, and minicom 2.4-1.  I'm using minicom to control an embedded ARM-based device that is itself running a basic, stripped-down Linux, a RidgeRun customized 2.6.33 kernel, plus glibc 2.6.1 and ncurses 5.6.  The embedded ARM device has no keyboard or monitor, just a serial console, which I access with minicom on my development laptop.

The embedded ARM device has some custom control apps that use ncurses-based text menus to provide a nice UI.  I have the ability to run an x86 version of the same control app (compiled from the exact same source) on my development laptop, and the UI renders just peachy in an xterm.  But when I look at it through minicom, running on the ARM, the rendering sucks.

When I set minicom to emulate "vt102" terminal, and set the TERM environment variable on the target to match, I get a monochrome UI.  I'm presuming this is because minicom is telling the target ncurses that the terminal doesn't support color.  All the text renders in the proper locations, but the box drawing characters are all off.  The majority of them render as inverse question marks in an oval.

When I set minicom to emulate "ansi" terminal, and set the TERM environment variable on the target to match, all the colors are correct, but the text doesn't render in the proper locations.  Box borders don't line up from one line to the next, things from a derived window rendering outside their derived window bounds, etc.  And the box drawing characters are, again, mostly inverse question marks in an oval.

I've gotten it so that minicom itself, in its own menus, renders the box drawing characters correctly.  All it needed was export MINICOM="-8 -L -l -c on -a on".  And again, the exact same control app, compiled for x86 and running natively on my laptop renders everything correctly.  So I'm thinking it's got to be something with minicom interpreting and munging the attribute and movement escapes coming across the serial line from the target ncurses.  The "ansi" terminfo file on the target was copied directly from my development laptop, so it comes from Ubuntu 10.04, just like minicom does.  Seems to me they ought to be compatible, but it doesn't appear they are.

I'd greatly appreciate any hints anyone has.

---

### Post by chaz572 on 2012-09-28
I got it to work, but I didn't get it to work in minicom.  I got it to work in putty.  Here's the relevant putty settings I used to make it work....

Under Window:Translation:
    Change remote character set to ISO-8859-1.  (The default of "use font encoding" doesn't seem to work.)
    Uncheck "Override with UTF-8 if locale says so".  (The default of checked also doesn't seem to work.)
    Select "Use Unicode line drawing code points".  (This is the default.)

Then I had to set the remote target's TERM environment variable to "xterm", and make sure it had the xterm terminfo file from my Ubuntu laptop in place.
With all that, I got the ncurses UI to render perfectly over the serial console, and it looked exactly like it does when I run the local x86 version.

\\:D/

Thanks to Bob S. for the hint of trying putty.  I had only used it before as an ssh client when forced to suffer Windows.  I had no idea it was available for Linux, and had completely forgotten it could do a local serial port, not just network connections.

---

