---
title: "shutdown script"
date: 2010-01-18
forum: General Help
---

### Post by loki_dre on 2010-01-18
I would like to make a program run when ubuntu is shutting down
Anyone know how to do this?

---

### Post by Leppie on 2010-01-18
launch your script from the gdm script /etc/gdm/PostSession/Default

---

### Post by loki_dre on 2010-01-18
hmmm....maybe I using it wrong.....

but I need it to be running around the time that other running terminal programs are being closed....
any advice?
The program that is launching after shut down communicates with a usb-serial port

---

### Post by Leppie on 2010-01-18
could you please explain what it exactly is that you are trying to achieve?
also, if you find it hard to explain maybe you could post the code of your script?

---

### Post by loki_dre on 2010-01-18
[COLOR=blue]i am trying to print the text "shutting down..." on a 20x2 character lcd display when the computer is shutting down.[/COLOR]

##################################################################################
###########################/etc/gdm/PostSession/Default##############################
#!/bin/sh

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

[COLOR=Red]sudo /root/NetBeansProjects/JavaApplication2-mysql/SD.py[/COLOR]

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}
exit 0
##################################################################################

##################################################################################
##############[COLOR=Red]/root/NetBeansProjects/JavaApplication2-mysql/SD.py[/COLOR]########################

#!/usr/bin/env python
import sys
import string
import glob
import os
from subprocess import *

ps = Popen('ps -la | grep java',shell=True, stdout=PIPE, stderr=PIPE, close_fds=True)
ops = ps.communicate()[0]
while (len(ops) > 0):
    ps = Popen('ps -la | grep java',shell=True, stdout=PIPE, stderr=PIPE, close_fds=True)
    ops = ps.communicate()[0]


pusb = Popen('sudo cat /proc/tty/driver/usbserial | grep "FTDI USB Serial"',shell=True, stdout=PIPE, stderr=PIPE, close_fds=True)
#pusb = Popen('sudo cat /proc/tty/driver/usbserial | grep "pl2303"',shell=True, stdout=PIPE, stderr=PIPE, close_fds=True)
ousb = pusb.communicate()[0]

while (ousb.find(':') > 0):
    print '/dev/ttyUSB' + ousb[0:ousb.find(':')] + '\n'
    Popen('/home/roadrunner/JavaApplication2-mysql/SD /dev/ttyUSB' + ousb[0:ousb.find(':')],shell=True, stdout=PIPE, stderr=PIPE, close_fds=True).wait
    ousb = ousb[ousb.find('\n')+1:len(ousb)]

##################################################################################

---

### Post by loki_dre on 2010-01-19
[color=blue]i am trying to print the text "shutting down..." on a 20x2 character lcd display when the computer is shutting down.
[/color]

---

### Post by loki_dre on 2010-01-19
I got it now.

must abort shutdown (shutdown -c)
run script
and then resume shutdown

##################################################  ################################
###########################/etc/gdm/PostSession/Default##############################
#!/bin/sh

PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

[COLOR=Red]sudo shutdown -c[/COLOR]
[COLOR=Red]sudo /root/NetBeansProjects/JavaApplication2-mysql/SD.py[/COLOR]
[COLOR=Red]sudo shotdown -P[/COLOR]

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}
exit 0
##################################################  ################################

---

### Post by Leppie on 2010-01-19
> **loki_dre said:**
> [COLOR=Red]sudo shutdown -c[/COLOR]
[COLOR=Red]sudo /root/NetBeansProjects/JavaApplication2-mysql/SD.py[/COLOR]
[COLOR=Red]sudo shotdown -P[/COLOR]
the gdm Default script is run with root permissions, you don't need to use sudo.
and i hope nobody was shotdown :P

---

