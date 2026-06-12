---
title: "advantages of reducing the no:of virtual consoles ?"
date: 2010-09-30
forum: General Help
---

### Post by siju on 2010-09-30
Hi,

can any one explain me the advantages of reducing the no:  of virtual consoles in a linux distro ?


The advantages that i know of are

What are the advantages of reducing the no: of virtual consoles in a linux distro ?
 
  *Reducing the number of virtual consoles will reduce the amount of used RAM
  
  *Reducing the number of VTs means a little less work for init to do during boot so boot will be a little faster. After boot has completed it will make no difference unless the system has very little memory.

is there any other advantage that I have missed ?

---

### Post by mcduck on 2010-09-30
No, not really. And I should add that the impact on RAM usage is very minimal, and the effect in boot time is way too small to measure.

Well, perhaps it makes sense if you never use them and wish to assign the Ctrl-Alt-F* shortcuts to something else. Apart from that, I really wouldn't bother unless you are trying to run Ubuntu on a very low end machine and need to squeeze every single byte of RAM you can get.

---

### Post by siju on 2010-09-30
> **mcduck said:**
> No, not really. And I should add that the impact on RAM usage is very minimal, and the effect in boot time is way too small to measure.

Well, perhaps it makes sense if you never use them and wish to assign the Ctrl-Alt-F* shortcuts to something else. Apart from that, I really wouldn't bother unless you are trying to run Ubuntu on a very low end machine and need to squeeze every single byte of RAM you can get.


I was trying to reduce the number of virtual consoles using the following link

_[http://crunchbanglinux.org/wiki/howto/disable_extra_ttys](http://crunchbanglinux.org/wiki/howto/disable_extra_ttys)_

but i couldn't figure out how  to  edit the tty files to stop them running on system boot ?

there is no /etc/event.d/ in my machine( I use ubuntu 10.04),

can any one  help me ?


the  file(s) i could find was /etc/init/tty4.conf

/etc/init/tty5.conf
/etc/init/tty1.conf
/etc/init/tty3.conf
/etc/init/tty6.conf
/etc/init/tty2.conf


with the contents of tty4.conf as follows:-

# tty4 - getty
#
# This service maintains a getty on tty4 from the point the system is
# started until it is shut down again.

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /sbin/getty -8 38400 tty4

should I comment all the lines in this file to stop tty4 running on system boot.

---

