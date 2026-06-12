---
title: "Get process details by name"
date: 2010-10-14
forum: General Help
---

### Post by djeyewater on 2010-10-14
I'm trying to get pid, memory and command of specific process by name. To get details of perl process I tried
```
ps -u djeyewater -C perl -o pid,rss,cmd
```but it just lists all processes. Is there a way to do this or should I pipe ps output to grep?

---

### Post by lordberic on 2010-10-14
I would use 

ps -aux | grep perl

it gives you 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
for the process you want 

:)

---

### Post by ac14112 on 2010-10-14
```
ps -ef
```
is another good command that gives you lots of info.

You can also pipe it out to grep to find the specific process you are looking for like the post above.

---

### Post by endotherm on 2010-10-14
ps -ef | grep <processname>

---

### Post by djeyewater on 2010-10-14
So there's no way to do this without piping the output to grep?

Reason I would prefer not to pipe to grep is that it means the column headers aren't included and also the grep process is grepped
```
djeyewater@rusty-ubuntu:~$ ps -ef | grep perl
1005      2270     1  0 15:50 ?        00:00:00 /usr/bin/perl /home/djeyewater/apps/perl-fcgi/fastcgi-wrapper.pl
1005      2621  2199  0 19:59 pts/0    00:00:00 grep perl

```

---

### Post by endotherm on 2010-10-14
this should get you the basics:
```

v= echo `ps -ef | grep [U]ID`; w= echo `ps -ef | grep [n]autilus`; echo $v $w

```far from perfect however. I'm sure someone can do it in one command. just replace [n]autilus with whatever process you are grepping.
BTW, when you grep a process, it always returns the grep process as a secondary result, unless you surround one of the grepped characters in square braces as above. and those quotes are "backqoutes" (on the tilde key, under esc on an en-us keyboard)

here is the output:
```

UID PID PPID C STIME TTY TIME CMD
User 1391 1285 0 09:08 ? 00:00:02 nautilus

```

---

### Post by ac14112 on 2010-10-14
Try this out:

```
ps -ef | sed -n -e '/sed/d' -e 1p -e '/nautilus/p'
```

Its kind of long, but it should work like you want it to. just replace nautilus with whatever process you are searching for.

If you want options on shortening it via an alias or script, let me know.

---

### Post by ac14112 on 2010-10-14
If you want to shorten up the command, add this to the end of your .bashrc file in your home directory:


```
psgrep() {
ps -ef | sed -n -e /sed/d -e 1p -e /$1/p
}
```

Then type:

```
source ~/.bashrc
```

To test if the alias worked, run:

```
psgrep nautilus
```

You should get the same output as using the long command.

---

### Post by djeyewater on 2010-10-15
Thanks endotherm and ac14112. I like ac14112's solution best.

Regarding storing it for future use, what's the best practice[LIST]
[*]Adding function to ~/.bashrc / ~/.bash_profile or
[*]Adding script to my $HOME/bin folder?
[/LIST]Both work the same, is it just a matter of personal preference?

---

