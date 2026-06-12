---
title: "Redirect output to terminal based on window title"
date: 2012-04-18
forum: General Help
---

### Post by jba3 on 2012-04-18
Is there a way to redirect output to a specific terminal based on the window title? I've done the 'embedded terminal', so I have a terminal permanently attached to the desktop background.

I also have some scripts that run some cron jobs. I want to send the results of those to the desktop terminal; I can do:

bash myscript.sh >> /dev/pts/0

and it sends the output to the terminal. The problem is, when I reboot, the terminal number seems to randomly change. Is there some way to redirect to it based on the title (like with a COMPIZ selector?), or force the terminal to start specifically as /dev/pts0 (or other identifier)?

(Writing to a text file and displaying via Conky isn't an option, as I'm using unison for synchronizing in part of the cron, and I want a real-time display of what unison is doing with things in the terminal.)

---

### Post by dcstar on 2012-04-19
> **jba3 said:**
> Is there a way to redirect output to a specific terminal based on the window title? I've done the 'embedded terminal', so I have a terminal permanently attached to the desktop background.

I also have some scripts that run some cron jobs. I want to send the results of those to the desktop terminal; I can do:

bash myscript.sh >> /dev/pts/0

and it sends the output to the terminal. The problem is, when I reboot, the terminal number seems to randomly change. Is there some way to redirect to it based on the title (like with a COMPIZ selector?), or force the terminal to start specifically as /dev/pts0 (or other identifier)?

(Writing to a text file and displaying via Conky isn't an option, as I'm using unison for synchronizing in part of the cron, and I want a real-time display of what unison is doing with things in the terminal.)

Use the **who** command to find the tty.

---

### Post by HiImTye on 2012-04-19
this will output what each output is to said output:
```
tye@T:~$ max="$(ls /dev/pts | grep '[0-9]\{1,2\}' | tail -1)"; max=$(expr $max + 1) current=0 ; while [ "$current" -lt "$max" ] ; do echo /dev/pts/$current > /dev/pts/$current ; current=$(expr $current + 1) ; done
/dev/pts/1
```

---

### Post by jba3 on 2012-04-19
> **dcstar said:**
> Use the **who** command to find the tty.

It randomly changes on reboots, and when it does, my script won't output until I update the /dev/pts/# by hand.

> **HiImTye said:**
> this will output what each output is to said output:
```
tye@T:~$ max="$(ls /dev/pts | grep '[0-9]\{1,2\}' | tail -1)"; max=$(expr $max + 1) current=0 ; while [ "$current" -lt "$max" ] ; do echo /dev/pts/$current > /dev/pts/$current ; current=$(expr $current + 1) ; done
/dev/pts/1
```

That worked to get it to show the redirect path. How do I get it to save from the specific embedded terminal, though? There's nothing like:

bash ~/script.sh > [title=test-terminal]

? I think I could use that loop to just output to all terminals, but that would make working in the terminal impossible while the crons are running. It's a start though, thanks!

---

### Post by HiImTye on 2012-04-20
you could get it to look for a global variable and then output to that variable, for instance, make a bash script like this:
newscript.sh
```
#!/bin/bash
# output the current /dev/pts/ path to all terminals
 # if the --test or -t switches are used
if [ "$1" = "-t" -o "$1" = "--test" ]; then
 max="$(ls /dev/pts | grep '[0-9]\{1,2\}' | tail -1)"
 max=$(expr $max + 1)
 current=0

 while [ "$current" -lt "$max" ]; do
  echo /dev/pts/$current > /dev/pts/$current
  current=$(expr $current + 1)
 done
 exit
fi

# set our current /dev/pts/ path as the input for our other script
if [ ! "$1" = "-t" -o ! "$1" = "--test" ]; then
 currentpath=/dev/pts/$1
fi
exit

```then set your other script to use the global variable you set in your script 'currentpath' in your cron script like:
```

/path/to/program -arguments > $currentpath

```

---

### Post by jba3 on 2012-04-29
When I run that bash file, then echo $current, I get a blank/empty/null variable. When I tried to start a terminal with --test or -t, it isn't happy - I'm using "gnome-terminal", if that makes any difference. I also tried with XTerm, which didn't work either.

When I do a simple output for $1, that seems to be blank too. What does $1 reference in that script?

The closest I have got is to have a gnome terminal profile that runs a script that dumps the /dev/pts/# to a text file. However, when I try to tail from that file, and use that to redirect output, I end up with a permission denied message that chmod and chown don't seem to fix.

---

