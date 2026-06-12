---
title: "run command and release terminal?"
date: 2011-10-21
forum: General Help
---

### Post by dhysk on 2011-10-21
How do you run a command in the terminal so that the terminal will continue on awaiting another command?

for instance:
```
VBoxHeadless -s "Windows_XP"
```
The terminal will freeze after the last output.  If i put it in the background same thing.  So if I do this:
```
VBoxHeadless -s "Windows_XP" &
```
it still stops untill I hit cntr+c and I can go on.  Problem is I cant send cntr+c using a script ;(... 

I also tried with nohup and still the script stops there untill I hit enter or ctrl+c than it moves on like it's supposed to.  very annoying.

---

### Post by jim_deadlock on 2011-10-21
If I understand you correctly what you're trying to do is make your script start this other process and then move on and do something else (or exit) while it does its own thing? In Perl you would use the 'fork' function to launch the child process.

---

### Post by dhysk on 2011-10-24
i couldn't find anything for bin/bash script that acts like 'fork' any other guidance?

---

### Post by dave01945 on 2011-10-24
I might be wrong, someone will say if I am but kill sends the same signal as ctrl-c SIGINT I think

---

### Post by dhysk on 2011-10-24
The problem is if I were to add 'kill' after the command it would never get there.

basically what I'm doing now is I have this script named: desktop-terminal
```
#!/bin/bash


Usage="Usage: '$0' -r for remote
                   -c to send command
                   -v virtualbox [start|poweroff]"
ipaddress=my.home.network.ip

while getopts rc:v:h OPT
do 	case "$OPT" in
	r) ipaddress=my.house.ip.address;;
	c) comnd="$OPTARG";; 
	v) if [ $OPTARG = "start" ]; then
		comnd='VBoxHeadless -s "Windows_XP" &'
	   fi

	   if [ $OPTARG = "poweroff" ]; then
		comnd='vboxmanage controlvm Windows_XP poweroff'
	   fi
	;;
	h) echo $Usage
	   exit 1;;
		
	esac
done

ssh -p 6022 -C rick@"$ipaddress" ""$comnd""

exit
```

I can, via ssh, power on and off my virtual machine without having to actually log in type the command just to close it and open my remote desktop to my virtual machine.

I also have this script named: rdesktop-Windows_XP
```
#!/bin/bash

ip=my.home.network.ip

while getopts rs OPT
do	case "$OPT" in
	r) ip=my.house.ip
	   Remote="r";;
	s) desktop-terminal -"$Remote"v start
	   sleep 5;;
	esac
done

echo "$VdeskOptions"

rdesktop-vrdp -r usb -r sound -r clipboard -N "$ip":3389 &

exit


```

this opens a virtual desktop connecting to the virutal machine on my desktop computer with sound and USB support.  It can also with the option "-s", for start, invoke the other script to turn on the virtual machine.

problem is the whole thing pauses after it sends the command to start the VM.  it also pauses after it starts rdesktop-vrdp as well but that matters less since that command actually opens up the remote desktop.

---

### Post by xianbei on 2011-10-24
no answer here, but it sounds like it may be more related to the program you are starting:

rdesktop always seems to hold the terminal window hostage until it is closed.

firefox does the same thing, as does gedit

komodo edit, for example, has a nice way of being started via command line, then immediately releasing the terminal (or script) to continue on to other processes.

---

### Post by dhysk on 2011-10-24
that was my thought.  although with gedit atleast for me if i add the '&' at the end it always releases back to the terminal as it gets put in the backround.

```
gedit yourtextdochere &
```

---

### Post by emiller12345 on 2011-10-24
Is this what your looking for?
```
VBoxHeadless -s "Windows_XP" 2>&1 > /dev/null &
```

or you could do this
```
xterm -geometry 75x15 -e "VBoxHeadless -s Window_XP" &
```

---

### Post by dhysk on 2011-10-24
SOOOO CLOSE miller. If I log in via ssh and do that it does go back to the terminal.  Unfortunatly the script still hangs only when starting the VM though.  The poweroff works as designed.

could you explain the '2>&1 > /dev/null &' part?

I also have confirmed its the desktop-terminal that hangs after it starts the vm.

edit had to add another & at the end... just looks ugly

was
```
ssh -p 6022 -C rick@"$ipaddress" ""$comnd""
```

now is
```
ssh -p 6022 -C rick@"$ipaddress" ""$comnd"" &
```

problem is now it hangs on the power off command but that is WAY less irritating.  ;)

Thanks for the help so far, almost there.  My first shot at scripting so I I'm sure its a bit ugly.

---

### Post by emiller12345 on 2011-10-24
> **dhysk said:**
> could you explain the '2>&1 > /dev/null &' part?


the first part ```
2>&1
``` tells the program to send everything that is destined for the stderr ('2' anything that is an error message) to be sent to the regular ol' stdout ('1' normal output)

the second part ```
 > /dev/null 
``` says, take everything from the stdout and dump it somewhere. /dev/null is like a blackhole and disappears stuff.  the & on the end forks the command.

---

### Post by dhysk on 2011-10-25
awesome thanks you're last reply is much more valuable than the first that pretty much fixed the issue.

now just for me to figure out how to get the poweroff to work again ;)..

---

