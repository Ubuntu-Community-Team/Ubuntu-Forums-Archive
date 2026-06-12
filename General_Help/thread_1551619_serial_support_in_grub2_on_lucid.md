---
title: "serial support in grub2 on lucid"
date: 2010-08-12
forum: General Help
---

### Post by cyberyogi on 2010-08-12
I wanted to enable serial console support in Lucid and have made that mostly work, but still having some problems.  I have examined the following:

[the SerialConsoleHowto]("https://help.ubuntu.com/community/SerialConsoleHowto")
[the Grub Basics Guide]("http://ubuntuforums.org/showthread.php?t=1195275") &
[The Grub manual]("http://www.gnu.org/software/grub/manual/grub.html")

The desired behavior is:
1) grub should accept input from either the serial line or the console, whichever is pressed first, the way it use to be easy to do with the older grub;
2) to display startup console messages to whichever terminal is selected; and
3) to accept login and other terminal functions from both terminal sources.

This use to be pretty easy with the old grub.  I solved #3 using the GRUB_SERIAL_COMMAND directive in /etc/default/grub.  However, the GRUB_TERMINAL option does not seem to accept "console serial" as a parameter, giving an error when I try to run update-grub.  The GRUB_TERMINAL_INPUT option does accept "console serial" as the parameter but doesn't create any serial output when the menu comes up.  Trying "console serial" as a parameter to the GRUB_TERMINAL_OUTPUT directive, likewise produces an error when trying to run update-grub.  I can get a grub menu on the serial tty with "GRUB_TERMINAL=serial", but then I not only don't get the grub menu on the console, but I can't even get any response from the console keyboard after boot-up completes.

My current setup has the grub menu working through the console and gives me at least item #3; workable but less than ideal.  Are #1 & #2 possible with grub2?

---

### Post by cstork on 2010-10-21
Any news on this yet?

---

### Post by mapi on 2010-10-22
I'm also interested in getting both serial and graphic boot screens with grub and lucid.

Any news?

Brgds,
mapi

---

### Post by sunfreak on 2010-10-31
Hi folks,

I'm new in this forum, running kubuntu since some months on my laptop after struggling with opensuse for more than 10 years.
Just yesterday I installed kubuntu 10.04 LTS on my new (Sun) server and had to fix the serial problem too.

So I've found a solution to see the grub menu on console by adding a further kernel start with option text, removed quiet and splash from this line. Don't know, if it's required to change any grub options, as this works well for me having no screen connected to the server.

To have an serial login prompt after starting up I found this solution, which may help you as well:

[http://kisoku.net/articles/upstart_serial_console.html](http://kisoku.net/articles/upstart_serial_console.html)

>                  I've working quite a bit with Ubuntu recently at                 [                   work                 ]("http://opensource.qualcomm.com/")                 . Which is a bit of change from the RHEL environments I've used in the past.               
                                The new lucid release uses                 [                   upstart                 ]("http://upstart.ubuntu.com/")                 instead of the more traditional SysV init. Unfortunately, this means that                 the tried and true way of starting a getty process on a serial port via                 inittab(5) no longer works.               
                                After a bit of poking around in /etc/init, I managed to whip a very simple                 upstart job to start an instance of mgetty on ttyS0               
                                /etc/init/ttyS0.conf               
               # ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.
#
start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 9600 ttyS0                                All you need to do is kick off the upstart job               
               # start ttyS0
HTH,
Juergen

---

