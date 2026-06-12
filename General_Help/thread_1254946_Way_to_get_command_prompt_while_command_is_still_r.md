---
title: "Way to get command prompt while command is still running"
date: 2009-08-31
forum: General Help
---

### Post by SoftwareExplorer on 2009-08-31
I know that you can get a command prompt while you run a program in the background by adding & on the end like this 'gedit&'. But is there a way like how control c interrupts, but instead lets the program still run and gives you a command prompt?
Second, I'm trying zsh, so if you need zsh to be able to do that, it is ok with me, but don't let that discourage bash users from giving me advice.

---

### Post by NoaHall on 2009-08-31
Open another terminal, or use "ctrl +alt + 1" (numbers apart from 7) to open another.

---

### Post by SoftwareExplorer on 2009-08-31
> **NoaHall said:**
> Open another terminal, or use "ctrl +alt + 1" (numbers apart from 7) to open another.

This is mainly for when i'm sshed in to a computer, so I don't really want to have to login to ssh again. I'm looking for something that would do the equivalent of Ctrl-C and then run the program with &, without interrupting that program. 
It just seems like there should be a Ctrl-Something that would 'spilt' off a new command promt.
Thanks for trying to help, though.  :P

---

### Post by trhebig on 2009-08-31
Try ctrl+z, then type bg and hit enter to make the process run in the background.

---

### Post by Gen2ly on 2009-08-31
fg will bring it back up

---

### Post by blackened on 2009-08-31
For what you're asking, bg is the way to go.

If you're planning on leaving a text-based program open, but would like to close the terminal window (like something with a curses interface, e.g. htop or rtorrent), then screen is what you want.

---

### Post by SoftwareExplorer on 2009-08-31
What happens if I bg multiple processes? How does fg work after that?

---

### Post by DaithiF on 2009-09-01
> **SoftwareExplorer said:**
> What happens if I bg multiple processes? How does fg work after that?

run
```
jobs
```
to see all backgrounded jobs, then 
```
fg X

```where X is the number of the job from the jobs list that you want to bring to the foreground

---

### Post by nothingspecial on 2009-09-01
Try dvtm. It`s a tiling window manager for the terminal.

ssh in then launch dvtm

press Ctrl+G then C and your terminal will split into two with another prompt. I don`t know if there is a limit but I tend to have four going and use screen aswell. It can get tricky keeping track of what your doing.

It`s also good for learning terminal based apps. So launch dvtm, split the screen then type man dvtm in the other one and get used to the keybindings for a while.

Ctrl+G J and Ctrl+G K toggle the the windows but I think you can use your mouse.

---

### Post by blackened on 2009-09-01
Hadn't used dvtm before. Looks nice, thanks for the heads-up.

---

### Post by nothingspecial on 2009-09-01
No problem. I use it all the time. In fact my keyboard short cut to launch a terminal is bound to ```
gnome-terminal -x dvtm
```

I then split into four and press Ctrl+G G. This gives you a nice grid shape. cmus in one elinks in another and 2 more for whatever.

---

### Post by SoftwareExplorer on 2009-09-01
Thanks for the help. :) I'll have to try dvtm next time I'm bored. :P

---

### Post by SoftwareExplorer on 2009-09-11
> **DaithiF said:**
> run
```
jobs
```
to see all backgrounded jobs, then 
```
fg X

```where X is the number of the job from the jobs list that you want to bring to the foreground
I tried that, but I must not be getting the syntax right or something.
```
fg                                    (09-11 18:03:10)
[2]  - 22570 running    gcalctool
bg
^Z
[2]  + 22570 suspended  gcalctool
[bjorn@bjorn-desktop:~]$ bg                                    (09-11 18:03:30)
[2]  - 22570 continued  gcalctool
[bjorn@bjorn-desktop:~]$ jobs                                  (09-11 18:03:31)
[1]  + running    gedit
[2]  - running    gcalctool
[bjorn@bjorn-desktop:~]$ fg 2                                  (09-11 18:03:36)
fg: job not found: 2
[bjorn@bjorn-desktop:~]$ man fg                                (09-11 18:03:49)
No manual entry for fg
[bjorn@bjorn-desktop:~]$       
```

---

### Post by DaithiF on 2009-09-12
Hi,
you wouldn't normally use jobs/fg/bg etc to control GUI apps, they are more for controlling long-running command line processes.  But for the sake of illustration, to use your example:
```
$ gedit

```gedit app opens, command line doesn't return with a prompt as gedit is the 'foreground' app and the terminal is waiting for it to exit
Press ctrl-z
this causes the app to be suspended.  gedit is still running, but execution has been suspended so you can't interact with it.  in the terminal you now have a prompt again.
```
jobs

```this lists the jobs:
[1]+ Stopped               gedit
```
bg 1
```
resumes gedit in the background.  gedit is responsive again, and since the job is running in the background, the terminal gives you a prompt to enter more commands
```
fg 1
```
brings the app to the foreground, gedit remains responsive, but now the terminal is treating it as the foreground app again, so you don't have a command prompt.

---

### Post by SoftwareExplorer on 2009-09-13
Ok, after a little googling, I figured out that when you use zsh, you have to do %1 when you're referring to job 1. It's part of a syntax thing that lets you search the jobs by name so if you have 400 of them you can narrow it down to the 10 possible ones that you might want.:D
Thanks for the help I get it now.

---

