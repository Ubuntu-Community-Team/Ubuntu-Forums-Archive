---
title: "how to make deamon process?"
date: 2005-02-27
forum: General Help
---

### Post by isaac on 2005-02-27
Hi,
    Recently I wrote a C program but I intend to make it run as soon as my computer starts..  But I don't really know how to make my program into a deamon process.. I only know that it have something to do with init? but which file do i need to add command line in? what type of command line should i put?

thanks in advance ;)

---

### Post by NULL on 2005-02-27
You have to ways to do this:

1-  add '&' on the prompt

  ex: 'foobar&'   (foobar being your executable)


2- Make your program fork, just google something like 'c linux deamon'
    It's very easy to do and it's only a dozen lines or so.

then if you want it to start at bootup, maybe you could try looking what srcipts are started by inittab (don't know where it is on ubuntu, try /etc) and add it to the approriate one (when going multiuser?).


Good Luck

---

### Post by isaac on 2005-02-28
sorry i can't really under stand how to do it? how to make a program fork? and adding the '&' ito :-s  where exactly? to the program i created? if so how to do it ?

---

### Post by NULL on 2005-02-28
Adding a '&' to the end of a executable in a terminal makes it run in the background, try running your program from a terminal this way, you will see that it starts and that you get your prompt back.  This is a cheap way of doing it that might work.

Your other option is to had a few lines to your source so that your program will actually be a daemon.  Like I said just do a search for it.


google is your friend...

---

### Post by isaac on 2005-03-01
thanks .. i'll do some research on the script for deamon process than =)

---

### Post by isaac on 2005-03-01
i have found a site very good in describing making daemon process.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html)

But it require "chkconfig" command. but this commond is not avaiable in default ubuntu installation. 

My question is, if i want to use this "chkconfig" command what package do i need to install ?? or are there any way?

---

### Post by isaac on 2005-03-01
i have tried to write a script to run my program ... but it makes alot of errors until i can't boot the ubuntu..

I need help!.. Which level should i put my script to if my program which i choose to run in background is continuous process(looping) my computer now shows error 


"/dev/hda1:
Duplicate or bad block in use!
/dev/hda1: Duplicate/bad block in use! in node 235474, ........

---

### Post by isaac on 2005-03-01
are there difference in daemon and init files? i confused that init files are usually written in bash shell and daemon files are written in C? daemon files that proper management or ProcessID .? and Is it init files need a deamon file? i'm quite confused all around ?!?!?! :?:  :?:  :?:  :?:

---

### Post by NULL on 2005-03-01
init files and daemon are two different things, and you need both of them.  What you want is to have a script (init file) to call your daemon.

So you're program needs to work as a daemon (see [http://www.linuxprofilm.com/articles/linux-daemon-howto.html](http://www.linuxprofilm.com/articles/linux-daemon-howto.html)) or simulate it (the '&' trick).  Then you find a init script (one that already exist) and add a line that calls your program.  For the init script you might want to try inittab or a script called by it (I'm not sure what's the 'proper' way of doing it but try the find one that starts other daemon like samba, ssh, ... or  something)

If you get problems getting your program to run as daemon (from the instructions on the site above) post your code...

good luck

---

### Post by isaac on 2005-03-01
here is what i wrote for my init.d script

#!/bin/sh
#
# Startup script for program
#
# chkconfig: 345 85 15 - This statement tells the chkconfig command how to add or delete this process to the boot process
# description: Description of program
# processname: process-name
# pidfile: /var/run/process-name.pid

# Source function library. This creates the operating environment for the process to be started
. /lib/lsb/functions

case "$1" in
start)
echo -n "Starting process-name: ispy"
#this is where i put  my program
/var/www/ispy/ispy& 
;;
stop)
echo -n "Shutting down process-name: "
killproc /var/www/ispy/ispy&
echo

;;
status)
status process-name
;;
restart)
$0 stop
$0 start
;;
reload)
echo -n "Reloading process-name: "
killproc /var/www/ispy/ispy&
echo -HUP
echo
;;
*)
echo "Usage: $0 {start|stop|restart|reload|status}"
exit 1
esac

exit 0

amazingly when i type put this script in /etc/init.d/myscript and run it with "/etc/init.d/myscript start commond it keeps on going but unabile to write files(my program is to store picture type)  but when i try to kill the process it won't work :confused:  :confused:

---

### Post by Wim Sturkenboom on 2005-03-01
Who is the owner of the process? You can find this with *ps -ef |grep ispy* If you want to kill it, you need to be the owner of the process.
Where does your program try to write the files?

---

### Post by NULL on 2005-03-02
When you're doing a 'killproc', try removing the path and the '&'

ex:  

       killproc /var/www/ispy/ispy&

should be

       killproc ispy

---

