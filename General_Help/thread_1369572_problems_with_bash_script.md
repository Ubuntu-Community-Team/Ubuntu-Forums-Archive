---
title: "problems with bash script"
date: 2010-01-01
forum: General Help
---

### Post by spiky001 on 2010-01-01
I have got a bash script i have been playing with I need to start a process then close terminal with in the script but leave program running hope some 1 can help.

```
#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
firefox & exit
```

---

### Post by chewearn on 2010-01-01
Remove "exit".

```
#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
firefox &
```

---

### Post by spiky001 on 2010-01-01
i will give it a try

---

### Post by spiky001 on 2010-01-01
nope did not work still terminal sits there not even returned to prompt.

---

### Post by spiky001 on 2010-01-01
update to problem, if you run the script by right click run in terminal all works fine, but when executed from terminal terminal wont close at end???

---

### Post by Leppie on 2010-01-01
> **spiky001 said:**
> update to problem, if you run the script by right click run in terminal all works fine, but when executed from terminal terminal wont close at end???

maybe if you divert output to another terminal?

---

### Post by CharlesA on 2010-01-01
Check here: [http://ubuntuforums.org/showthread.php?t=548947](http://ubuntuforums.org/showthread.php?t=548947)

It suggested exec command.

EDIT: I just tried exec firefox and it closed the terminal window and opened firefox.

---

### Post by spiky001 on 2010-01-01
ok thks for help still not closing terminal i must have something wrong I now get the terminal back to prompt which is better but i would like it gone, i know i can make a desktop icon that would solve the problem but thats not what i want

```
#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
sleep 7
xterm -e firefox
& exit

```

I have a pic of what happens when script is run

This is my 1st attempt with scripts or anything like this

---

### Post by zenxi on 2010-01-01
> **spiky001 said:**
> ok thks for help still not closing terminal i must have something wrong I now get the terminal back to prompt which is better but i would like it gone, i know i can make a desktop icon that would solve the problem but thats not what i want

```
#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
sleep 7
xterm -e firefox
& exit

```I have a pic of what happens when script is run

This is my 1st attempt with scripts or anything like this

bumping out of curiosity

---

### Post by Leppie on 2010-01-01
i was actually also thinking of an exec solution, have you tried that?

---

### Post by spiky001 on 2010-01-01
as i said i,m totally new to this, so dont understand it, is the code above not that otherwise i dont now how to code it

---

### Post by pbrane on 2010-01-01
Why do you have to run this script from a terminal, and why does the scrip have to close the terminal? Wouldn't it be easier to ALT+F2 and run it that way?

---

### Post by zenxi on 2010-01-01
> **spiky001 said:**
> as i said i,m totally new to this, so dont understand it, is the code above not that otherwise i dont now how to code it

there are tons of books written on bash scripting, most friendly to noobies. but if your like me and cant afford $50 books you can check out your local library or download some ebooks..... *cough* TPB *cough*

---

### Post by Barriehie on 2010-01-01
Tutorial for [[color="Blue"]BASH[/color]](http://tldp.org/LDP/abs/html/). :)

---

### Post by chewearn on 2010-01-01
Ok, I misunderstood your first question.  This one should work:

```

#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
firefox && kill -9 $PPID

```

---

### Post by spiky001 on 2010-01-01
no still the same prob terminal not exiting

---

### Post by falconindy on 2010-01-01
I'm curious why the OP wants to bandaid the problem rather than fix the issue with his NIC...

If you're insistant...
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
exec firefox %u
```

---

### Post by chewearn on 2010-01-01
> **spiky001 said:**
> no still the same prob terminal not exiting

That's mighty strange.  It worked in my system.  The "logic" of the situation is thus:

0. Say, the script is named "restart-network-launch-firefox.sh"
1. You have a terminal open.
2. You ran the script by typing "./restart-network-launch-firefox.sh" and hit enter.
3. The terminal create a child process for the script.
4. The child process do it's thing, execute the script.
5. After firefox is launched, the script run "kill -9 $PPID".  This command tells it to kill it's parent.
6. Thus, the original terminal get the kill command, and closes.

Am I still misunderstanding what you are trying to do?

---

### Post by spiky001 on 2010-01-01
no sorry that didn,t work either, the reason i want it is i run off another pc for net when i connect laptop i have to ifconfig each time to get net i found another way in the end, then i thought make the script do abit more just to experiment just trying to learn.

If u type firefox straight into terminal it starts up but terminal sits there not able to use it so thought have it close

---

### Post by falconindy on 2010-01-01
> **chewearn said:**
> That's mighty strange.  It worked in my system.  The "logic" of the situation is thus:

0. Say, the script is named "restart-network-launch-firefox.sh"
1. You have a terminal open.
2. You ran the script by typing "./restart-network-launch-firefox.sh" and hit enter.
3. The terminal create a child process for the script.
4. The child process do it's thing, execute the script.
5. After firefox is launched, the script run "kill -9 $PPID".  This command tells it to kill it's parent.
6. Thus, the original terminal get the kill command, and closes.

Am I still misunderstanding what you are trying to do?
The problem with your script is that you're using the && operator, meaning "do action b if and only if action a terminates successfully". A single & would be more appropriate, allowing the prepended command to run in the background while execution continues at the terminal. Still, it won't work because the PPID of the script is the subshell created for the script to run in. You'd need the PPPID, if such a thing existed (GPPID?).

The exec command (in this particular scenario) replaces the current shell with the argument specified. Occurs to me that my solution won't work either because the script creates its own subshell and exec terminates THAT shell instead.

I'll give this one more shot... Create a gnome-terminal launcher that runs:
```
gnome-terminal -x /path/to/script
```
Run that from the desktop. Highly circuitous, and I'm sure that an easier way to accomplish this would just be to request a dhcp lease rather than bounce the connection.

---

### Post by spiky001 on 2010-01-01
ok looks like i'll run it in gnome ter it all works ok there thks ppl for helping

---

### Post by chewearn on 2010-01-01
> **falconindy said:**
> The problem with your script is that you're using the && operator, meaning "do action b if and only if action a terminates successfully". A single & would be more appropriate, allowing the prepended command to run in the background while execution continues at the terminal.

Alright, I made a mistake.  I already have an instance of Firefox running when I tested the script.  Therefore, the "firefox" command in the script opened a new Firefox window and return immediately.

When I retested the script with no running instance of Firefox, the "firefox" command did not return.

> Still, it won't work because the PPID of the script is the subshell created for the script to run in. You'd need the PPPID, if such a thing existed (GPPID?).I'm not sure if what you said here is correct, because it did find the actual (parent) terminal and killed it.

---

I tinkered a bit more, and it occurred to me:
1. You need to launch Firefox into the background
2. But you need to detach Firefox from the script process (else it will get killed when the parent terminal process is killed)
3. Then (after a short delay), you can kill the parent terminal process.

So, I got the following script:
```

#!/bin/bash

sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up

nohup firefox > /dev/null &
sleep 5
kill -9 $PPID

```---

No doubt, there are better ways to skin the cat, but I looked at this as an exercise to improve my grasp of the amazing CLI.

---

### Post by spiky001 on 2010-01-01
that sorted it out thks, i did go off on net looking couldn,t find much out there

---

### Post by HiImTye on 2010-01-01
```
#!/bin/bash
sudo ifconfig eth0 down
sleep 5
sudo ifconfig eth0 up
firefox &
exit
```should be what you want

---

