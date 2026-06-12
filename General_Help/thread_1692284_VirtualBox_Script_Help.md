---
title: "VirtualBox Script Help"
date: 2011-02-21
forum: General Help
---

### Post by MrMeier on 2011-02-21
Okay, I got this huge problem that I can't seem to get working.. 
I'm in need of some kind of loop or repeat function, and the World Wide Web don't got the answer that I'm looking for, so please take your time and help me :D

I got a VirtualBox with a VM called BSS, and I got a script looking like this:

> #!/bin/bash
ps -u bss1 | grep "VirtualBox" > {5f1c2e4a-d81c-4fa0-9cdd-037c6f771c09}

if [ -s {5f1c2e4a-d81c-4fa0-9cdd-037c6f771c09} ] ; then
REPEAT THE DAMN SCRIPT
else
sudo halt
fi

What I wan't it to do, is where it says "REPEAT THE DAMN SCRIPT", I wan't it to repeat the script every 1-2 seconds, until I close the VM, then it should move on to the sudo halt command.. 
All is working fine, I just need a repeat command, so it keeps running the script :)
Can someone give me a clue to do this? 

Thanks in advance :)

---

### Post by Spyderkid on 2011-02-21
replaces REPEAT THE DAMN SCRIPT with

```

watch -n PUT HERE HOW LONG YOU WANT IT TO BE BETWEEN REPEATS

```
so *watch -n 3* would repeat it every 3 seconds

---

### Post by Spyderkid on 2011-02-21
for more info run *man watch * in a terminal

---

### Post by MrMeier on 2011-02-21
> #!/bin/bash
ps -u bss1 | grep "VirtualBox" > {5f1c2e4a-d81c-4fa0-9cdd-037c6f771c09}

if [ -s {5f1c2e4a-d81c-4fa0-9cdd-037c6f771c09} ] ; then
watch -n 1
else
sudo halt
fi^Well, that didn't work.. It doesn't repeat? :(

---

### Post by Habitual on 2011-02-21
n/m

---

### Post by Habitual on 2011-02-21
give us the output of 
 
```
ps -u bss1 | grep "VirtualBox"
```

Thank you.

You may wish to read up at 
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by MrMeier on 2011-02-21
The output is that it checks if my Virtualbox is running, and if it is, it do nothing at the moment, but I want it to repeat the script, until I close the Virtualbox, then it should move on to the sudo halt command :)

---

### Post by Habitual on 2011-02-21
no kidding it doesn't work.

Have a look at [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by MrMeier on 2011-02-21
I have looked at that page, but I don't understand anything, I'm pretty stupid.. :D

---

### Post by Habitual on 2011-02-21
no kidding it doesn't work.

Have a look at [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by Habitual on 2011-02-21
do while true
pidof VirtualBox
else
sudo halt

is a possible answer.

Others may have a more elegant solution.

---

### Post by DaithiF on 2011-02-21
you could do it something like this:

```
while true
do
    if ! pgrep -u bss1 VirtualBox > /dev/null; then
        echo "virtual box is not running, about to halt"
        sudo halt
    fi
done
```

---

### Post by MrMeier on 2011-02-21
> **DaithiF said:**
> you could do it something like this:

```
while true
do
    if ! pgrep -u bss1 VirtualBox > /dev/null; then
        echo "virtual box is not running, about to halt"
        sudo halt
    fi
done
```
That didn't work either, trying your solution now Habitual.

---

### Post by DaithiF on 2011-02-21
> **MrMeier said:**
> That didn't work either

care to elaborate?  did running the command produce any output / errors that might indicate *why *it didn't work for you?

---

### Post by MrMeier on 2011-02-22
It just run the script once, and don't even close the system when I run it without VirtualBox open.. Sorry for my low info, I'm still new in this area :(

---

### Post by MrMeier on 2011-02-22
Anyone? :(

---

### Post by DaithiF on 2011-02-22
with virtual box running please post the output of these 2 commands:
```

ps -ef | grep -i virtual
pgrep VirtualBox
```

---

### Post by Spyderkid on 2011-02-22
okay here you go

```

yes COMMAND

```

that should repeat you command continously then after that add something to stop the script. for example

```

yes COMMAND
watch -n 1 && sudo halt

```

---

### Post by MrMeier on 2011-02-22
> **DaithiF said:**
> with virtual box running please post the output of these 2 commands:
```

ps -ef | grep -i virtual
pgrep VirtualBox
```
I get this with the ps -ef | grep -i virtual
```
bss1      3798     1 40 13:08 ?        00:00:00 /usr/lib/virtualbox/VirtualBox
bss1      3803  3798  1 13:08 ?        00:00:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
bss1      3812     1  9 13:08 ?        00:00:00 /usr/lib/virtualbox/VBoxSVC --automate
bss1      3826  3824  0 13:08 ?        00:00:00 grep -i virtual
```
And this with the pgrep VirtualBox
```
3687
```> **Spyderkid said:**
> okay here you go

```

yes COMMAND

```that should repeat you command continously then after that add something to stop the script. for example

```

yes COMMAND
watch -n 1 && sudo halt

```
That didn't work either, don't know why.. Not even the Watch command will work, maybe it's just my script that are wrong? I have no clue what it is, actually I don't know what I'm exactly doing.. Still newbie :D

---

### Post by DaithiF on 2011-02-22
> **MrMeier said:**
> I get this 
```
3687
```


thats the output from the second command ... what about the first command?

---

### Post by Spyderkid on 2011-02-22
the watch command probably doesn't because the one before hasn't ended.

It does work because I use it sometimes.

try just running this in a terminal 

***yes echo 'test'***

---

### Post by Spyderkid on 2011-02-22
okay I finally found this...

(it should work for sure.



```

while [ condition ]
do
   command1
   command2
   command3
done

```


here's an example of the above...
```
#!/bin/bash
counter=$1
factorial=1
while [ $counter -gt 0 ]
do
   factorial=$(( $factorial * $counter ))
   counter=$(( $counter - 1 ))
done
echo $factorial

```

---

### Post by MrMeier on 2011-02-22
> **Spyderkid said:**
> the watch command probably doesn't because the one before hasn't ended.

It does work because I use it sometimes.

try just running this in a terminal 

***yes echo 'test'***
Well, that worked all fine :D

---

### Post by DaithiF on 2011-02-22
@SpyderKid:
```
yes echo 'test'

```continuously outputs the string **echo 'test'**
it doesn't run any command

so its not going to help the OP here.


man yes:
yes - output a string repeatedly until killed

---

### Post by MrMeier on 2011-02-22
> **Spyderkid said:**
> okay I finally found this...

(it should work for sure.



```

while [ condition ]
do
   command1
   command2
   command3
done

```
But that is what I have been trying all this time, and I can't get it working? :(
What should it say a [condition] and command1 - 2 - 3?

---

### Post by Spyderkid on 2011-02-22
Here's a whole page on it where I got what I last posted from...

Might take a bit of time for you to get your head round it but read everything...

[HERE!]("http://www.cyberciti.biz/faq/bash-while-loop/")

---

### Post by DaithiF on 2011-02-22
this is frustrating ... the solution i gave you 22 hours ago is exactly of that form, and 'filled in the blanks', but you have failed to provide information on why/how your attempt to follow my solution hasn't worked for you.  Trust me, it does work, so you need to give more details on what exactly you did, and what results it gave.  Otherwise we can't help.

please post the output of ps -ef | grep -i virtual

and post the contents of the script you have run,

and a copy/paste of the terminal output as you run it.

thanks

---

### Post by MrMeier on 2011-02-22
> **DaithiF said:**
> please post the output of ps -ef | grep -i virtual
I'm sorry it's so frustrating for you guys, and I thank you a lot for all your time, but still, i began doing this yesterday, and have never tried anything like it before, so please don't be to hard on me.. But here is the output of that while VirtualBox is open:
```
bss1      3997     1 13 13:23 ?        00:00:00 /usr/lib/virtualbox/VirtualBox
bss1      4002  3997  0 13:24 ?        00:00:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
bss1      4011     1  3 13:24 ?        00:00:00 /usr/lib/virtualbox/VBoxSVC --automate
bss1      4025  4023  0 13:24 ?        00:00:00 grep -i virtual
```

> **Spyderkid said:**
> Here's a whole page on it where I got what I last posted from...

Might take a bit of time for you to get your head round it but read everything...

[HERE!]("http://www.cyberciti.biz/faq/bash-while-loop/")
I will begin reading again, thanks :)

---

### Post by DaithiF on 2011-02-22
how about these two?

> 
and post the contents of the script you have run,
and a copy/paste of the terminal output as you run it.

---

### Post by MrMeier on 2011-02-22
Can you tell me how to see the terminal output? It won't show anything in the terminal..

---

### Post by DaithiF on 2011-02-22
are you not running it from a terminal ?  

how **are** you running it?

---

### Post by mciverza on 2011-02-22
Terminal is available at 
Applications --> Accessories --> Terminal

---

### Post by MrMeier on 2011-02-22
I am running it as a script? That's where the #!/bin/bash comes in :)
And when i wonna see the output, I just add this > /home/bss1/output.txt
> **mciverza said:**
> Terminal is available at 
Applications --> Accessories --> Terminal
I know that, but when I run a script, it don't show it in the terminal.

---

### Post by DaithiF on 2011-02-22
Heres what a useful reply might have looked like:

I run it from a terminal
or
I double-click it in nautilus and choosing the 'Run' (rather than the 'Run in Terminal' option in the dialog that appears.
or
I run it via the Alt-F2 dialog box
or
I run it via a launcher that I have created.

why is this important?  because if the script is run without an attached terminal then any sudo command in that script is going to fail because it has no way of asking you for your password.  In which case the command will run and run and run and look to you like its doing nothing.

oh and I've asked about 4 times already for the contents of the script you tried (with my solution) and you still haven't provided it.

---

### Post by MrMeier on 2011-02-22
Well, I'm sorry to be new in this, and I don't understand the half of what you are saying s;
But, I run it in a script because it should be executed when I log in, and that's easier that way..

---

### Post by DaithiF on 2011-02-22
ok great, so this script is run automatically at startup?

If so, then how?

e.g.: 

an entry you have added to System->Preferences->Startup Applications ?

or a line you have added to /etc/rc.local ?

or some other method?

---

### Post by MrMeier on 2011-02-25
Yes it does, and it do it with the System->Preferences->Startup Applications :)

---

### Post by DaithiF on 2011-02-25
ok, the implication of this is the script is running without an attached terminal.  If sudo needs to ask for a password and there isn't an attached terminal then it will throw an error because it has no way of asking for a password.

There are a couple of ways around this ... you could configure sudo so that it doesn't require a password to invoke a particular command (ie. halt or shutdown).  Or you could use gksudo instead which doesn't require a terminal as it will pop up a graphical dialog box when it needs to ask for a password.

So my first suggestion is to use gksudo rather than sudo in your script.
My second suggestion is to put in a sleep command of say, 1 second, between checks, so that this isn't running constantly (probably thousands of times per second) and eating up your CPU cycles.

My third suggestion is a more general point about what to do when a script isn't working ... which is to try to figure out what is going on by capturing the output from the script.

so if the original script had been something like:
```
#!/bin/bash

while true
if ! pgrep -u bss1 VirtualBox; then
    sudo halt
fi
sleep 1
done
```

then adapt it something like the following to (a) capture output in a file, and (b) be more verbose about what is happening at various steps,
```
#!/bin/bash

logfile=/path/to/somelog
while true
echo "About to do pgrep check for Virtual Box" >> "$logfile"
if ! pgrep -u bss1 VirtualBox; then
   echo "Virtual box is not running, about to call sudo" >> "$logfile"    
   sudo halt >> "$logfile" 2>&1
else
    echo "Virtual Box is running" >> "$logfile"
fi
sleep 1
done
```

if you did this you would probably have seen something 'sudo: no tty present ..." in the output which would have given you an avenue of investigation

good luck

---

### Post by MrMeier on 2011-02-25
Okay, thank you so much, that helped alot.. 

Now, I got everything to work, almost.. It looks like this now 

```
#!/bin/bash
ps -u bss1 | grep "VirtualBox" > {5f1c2e4a-d81c-4fa0-9cdd-037c6f771c09}

while :
 do
ps -u bss1 | grep "VirtualBox" > {5f1c2e4a-d81c-4fa0-9cdd-037c6f771c09}
   if [ -s {5f1c2e4a-d81c-4fa0-9cdd-037c6f771c09} ] ;
    then echo "****" > /home/bss1/open.txt
   else
    sudo halt
   fi 
done
```But as you said, it wont shut down due the password error.. So instead of doing the sudo halt, then I should write gksudo halt, or didn't I understand it right? :)

#EDIT! 
-Okay, I just realized that I need a way around the password, it should just shutdown without asking for at password..

---

### Post by DaithiF on 2011-02-25
see:
[http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/](http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/)

this doesn't really matter at this point ... but why do the redundant ps check outside the while loop.  why use ps / grep / output redirection to a bizarre filename and then check the contents of that file rather than the straightforward pgrep command I gave you?  why no sleep command?  in short, why ignore virtually all the advice you have asked for?

---

