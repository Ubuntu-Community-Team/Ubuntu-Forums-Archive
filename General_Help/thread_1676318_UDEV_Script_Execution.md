---
title: "UDEV Script Execution"
date: 2011-01-27
forum: General Help
---

### Post by phanie on 2011-01-27
Hello guys,this is my second thread and my good lord it is still about UDEV. The first UDEV problem I posted was already solved and if you wanna check it out it's entitled "UDEV help!please". Ahm,dont mind the plea. Im desperate. LOL. And i still am. This time the problem is about the script execution of the rule.

i have a bash named draft2.sh which contains a script placed in my home folder which is /home/babyjessie and the script goes like this.

> echo mann2x >> log.txt

i made it as simple as possible because i am currently testing results.

my rules goes like this:

> ACTION=="add", KERNEL=="sdb1", SUBSYSTEM=="block", ATTR{partition}=="1", ATTR{start}=="8192", ATTR{size}=="3936256", PROGRAM+="/home/babyjessie/draft2.sh", MODE = 0777


Judging from the result udevadm test, i think the rule is fine except for the part where a script is supposed to be executed. It printed out something like this:

> udev_rules_apply_to_event: PROGRAM '/home/babyjessie/draft2.sh' /lib/udev/rules.d/96-mann.rules:1

util_run_program: '/home/babyjessie/draft2.sh' started

util_run_program: '/home/babyjessie/draft2.sh' (stderr) 'util_run_program: exec of program '/home/babyjessie/draft2.sh' failed'

util_run_program: '/home/babyjessie/draft2.sh' returned with exitcode 1



So guys,help me please. I'm on a deadline, a noob and in need of help. Thank you.

---

### Post by phanie on 2011-01-27
For all the viewers, please leave even a "don't know" or "just give" up message.LOL. Thank you very much.

---

### Post by gzarkadas on 2011-01-27
From the output, it seems that your sh script indeed executes but exits with an error (exit code is 1). I would suggest to check your sh script's logic. I can't tell more cause I haven't done any udev-specific scripting yet.

PS: The output says an exec has failed. If you do an exec in your script, this is the first place to start with.

---

### Post by AlphaLexman on 2011-01-27
Post your entire script in ```
 tags (click the # sign in the toolbar before pasting)

Also, unless your username's home directory is in your $PATH you should start your script with a './' before the scriptname...
[CODE]./draft2.sh
``` assuming you are in your home directory.

---

### Post by phanie on 2011-01-28
What do you mean with the ./draft?could you please give me an example of the path using such?Should it be like "/home/babyjessie/./draft.sh"

---

### Post by phanie on 2011-01-28
> echo mann2x >> log.txt

and this is already my entire code..

---

### Post by AlphaLexman on 2011-01-28
> **phanie said:**
> What do you mean with the ./draft?could you please give me an example of the path using such?Should it be like "/home/babyjessie/./draft.sh"
No, ...
```
#!/bin/bash
if [[ $PWD -eq '/home/babyjessie' ]]; then
    ./draft2.sh
else
    ~/draft2.sh
fi

```
What I meant is that if you are in your $HOME directory, you need to put './' in front of the script name, since it is in your $HOME directory. The shell does not implicitly read the current directory, only the $PATH. Therefore you have to give a **relative** path so the shell can find the script.

Else,

An **absolute** path to your $HOME directory to find the script.

'fi' ends the 'if' statement.

---

### Post by phanie on 2011-01-29
Got it! Thanks dude!=)

---

### Post by phanie on 2011-01-30
Got a development. After some series of testing, I was able to make my script running whenever I insert a flash drive. The code that I've discussed is just for testing purposes. What I'm really trying to do is to make the screen locked after inserting a flash drive. 

So here it goes, I just changed the code inside the script. Tested it using the terminal (it workedjust fine). I restarted the udev. But when I inserted a flash drive, the script was not executed. Looking on the log of udevadm test I saw this message:

> Failed to connect to the D-BUS daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

What's d-bus daemon? How to connect to it? How to make my script working?

Thanks!

---

### Post by phanie on 2011-02-01
I finally got it all to work!Thanks to all those who posted. Now, if you could just help me with this tiny bit of feature i wanna add. Please answer theses questions:

1. Is it possible to run 2 or more programs in a single rule.
2. Can a device be auto unmounted after being mounted given that it is identified as a storage device?
3. Can auto-unmount and lock-PC be executed in a single rule or each of them is exclusive to a single rule?
4. Can you guys give me a more effective script to unmount a device other than "umount /dev/sdb1"?

Thank you all!

---

### Post by gzarkadas on 2011-02-02
1: The docs say so; I never tested it myself.

2: I suppose you mean by device name. See link #2. Two possible strategies to auto-unmount:

a. Use 'sleep <number-of-seconds>' and then 'umount -l <mount-point>' inside a subshell (so that your main script continues). Example:
```
( sleep 2 ; umount -l /dev/sdb1 )
```b. Schedule the umount at a time in the future with at (type 'man at' in a terminal to find options).

3: Any sequence of shell commands can be attached to a rule (just put them in the script), so I suppose "yes" is the answer; though you will have to verify this yourself.

4: I suppose you mean by device name. See link #2. 

Documentation links:

1. man udev (locally) or [there]("http://manpages.ubuntu.com/manpages/karmic/man7/udev.7.html") 
2. [Create your own udev rules...]("http://ubuntuforums.org/showthread.php?t=168221") 
3. [Writing udev rules]("http://reactivated.net/writing_udev_rules.html")

NB: see in particular section "Running external programs upon certain events" in link #3; it is what applies in your case.

---

