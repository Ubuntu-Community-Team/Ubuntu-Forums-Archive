---
title: "Bash Script help"
date: 2011-08-09
forum: General Help
---

### Post by Plasma_NZ on 2011-08-09
Ok, i dont know much about writting bash-scripts, wondering if someone could help me...

My goal is...

I am trying to make a bash-script toggle to do the following...

enable eth1 and disable eth0 wait 8 seconds do a "sudo umount -a" then wait 4 seconds then do a "sudo mount -a"

then if i hit the toggle again, do the reverse.;... disable eth1 and enable eth0 but not the umount/mount process...

eth0 - internet
eth1 - wireless ap

---

### Post by karlson on 2011-08-09
> **Plasma_NZ said:**
> Ok, i dont know much about writting bash-scripts, wondering if someone could help me...

My goal is...

I am trying to make a bash-script toggle to do the following...

enable eth1 and disable eth0 wait 8 seconds do a "sudo umount -a" then wait 4 seconds then do a "sudo mount -a"

then if i hit the toggle again, do the reverse.;... disable eth1 and enable eth0 but not the umount/mount process...

eth0 - internet
eth1 - wireless ap

I suggest using perl but in bash it would look something like this:

```

if [ ! -f /tmp/toggle_flag ]; do
ifup eth1
ifdown eth0
sleep 8
sudo umount -a
sleep 4 
sudo mount -a
touch /tmp/toggle_flag
else
rm /tmp/toggle_flag
ifdown eth1
ifup eth0
fi

```

Seems to be something really really complicated.

---

### Post by Toz on 2011-08-09
> **Plasma_NZ said:**
> Ok, i dont know much about writting bash-scripts, wondering if someone could help me...

My goal is...

I am trying to make a bash-script toggle to do the following...

enable eth1 and disable eth0 wait 8 seconds do a "sudo umount -a" then wait 4 seconds then do a "sudo mount -a"

then if i hit the toggle again, do the reverse.;... disable eth1 and enable eth0 but not the umount/mount process...

eth0 - internet
eth1 - wireless ap

```
#!/bin/bash

state=`cat /tmp/toggler_state`

[ $? -eq 0 ] || state=0

case $state in
	0) 	ifdown eth0 
		ifup eth1 
		sleep 8s
		umount -a
		sleep 4s
		mount -a
		echo "1" > /tmp/toggler_state
	;;
	1)
		ifdown eth1 
		ifup eth0 
		echo "0" > /tmp/toggler_state
	;;
	*)
	;;
esac
```

Run the script with sudo.

---

### Post by Synoc on 2011-08-09
the main problem I'm seeing is, creating a script that has your password in it, if you call on sudo, I don't know a way to NOT have it ask. you'd have to read the password into the script. the only way I know to do that is to put it into a variable, read in at the beginning of the script. not a very secure thing to do it. you could run a "sudo bash" then have the script exit at the end. but you'd still have to put the password in once. unless you are running in root mode from the get-go.

The best way to have it to multiple things with  one button push however it to create a hidden file in your home folder, say ".eth_toggle.txt". this will store the current state.

then create script that says 
```
ethernet=`cat eth-_oggle.txt` #this will read the current state of the last time you  pushed   the button   #this reads the current state of the last time the button was pressed.
if [[ $ethernet = 1 ]]
   then 
      insert actions here          #these are the actions you want it to do first time you push the button, then tells it to do something else next time
      ethernet=0                    
   else
      alternate actions here     #this is what it will do next time, then tell it to do the first action next time
      ethernet=1                    
fi

echo $ethernet > ~/.ethernet.txt  #this will save the state to the file after the script is finished 
```

this is very similar to the trackpad toggle I have on my system. I DO NOT know how to add the password to the sudo command and make it secure if that file is found. and echo command after the sudo command , say "pswd=Yourpassword" as the variable for your password, then "sudo  command" and "echo $pswd" should do it. but I do not recommend that

---

### Post by angry_johnnie on 2011-08-09
to avoid having to type in your password, without having to include it in the script, you could just save this script to /usr/local/bin or /usr/bin and then edit the sudoers file to include something like ```
%admin ALL=NOPASSWD: /usr/local/bin/yourscript
```

then, you can either do

```
sudo script
```

or create an alias in your .bashrc that will summon "sudo script"

---

### Post by Plasma_NZ on 2011-08-10
Thanks guys for all your help, will give them all a test when i get home and let you know the results...  :o

---

### Post by Plasma_NZ on 2011-08-11
well the results were too complex for the person trying to run the script.... spose i should find another way...


Can i enable both wireless and wired connections on there laptop and specify samba to use eth1 and everything else use eth0 for internet related stuff..??

Ip ranges are as follows...

eth0 - connects to adsl modem with ip info as follows

192.168.1.64 / 255.255.255.0 / 192.168.1.254



eth1 - connects to wireless ap that only allows samba access

10.0.0.4 / 255.255.255.0 / 10.0.0.1



is there anyway i can get it to play nice together? currently when both are enabled all internet access die's and only samba access works...

---

