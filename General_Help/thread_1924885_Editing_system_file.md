---
title: "Editing system file"
date: 2012-02-13
forum: General Help
---

### Post by europaflyer on 2012-02-13
Hi all,
 
I'm trying to edit the file 
 
/sys/class/net/eth0/queues/rx-0/rps_cpus
 
to prevent receive packet steering being used (as this is incompatible with my network). I can't. I'm a Linux newbie! How is this done? I've tried the commands sudo nano, gksudo nautilus, sudo nautilus, gksudo gedit... all with no result, when I try to edit the file it doesn't allow it, the text editor shows 'a backup cannot be created...save anyway?' but the button is dead. Editing within the terminal just doesn't do anything.
 
Help please!

---

### Post by bluexrider on 2012-02-13
I don't have any problem using

```
gksudo gedit /sys/class/net/eth0/queues/rx-0/rps_cpus
```

edit the file and save. When the Red bar comes up hit cancel and reload.

---

### Post by HiImTye on 2012-02-13
you can echo directly to the file but you must do it as root. for instance:
```
sudo sh -c "echo <value> > /sys/class/net/eth0/queues/rx-0/rps_cpus"
```to see the current value
```
cat /sys/class/net/eth0/queues/rx-0/rps_cpus
```

---

### Post by europaflyer on 2012-02-13
Thanks - but neither work!!
 
bluexrider - tried gksudo gedit, ended up with the same 'cannot perform backup - save anyway?' box with the dead button. Not sure what you mean by the 'red bar' with a cancel button - didn't happen to me!
 
HiImTye - I used
 
```
sudo sh -c "echo 0 > /sys/class/net/eth0/queues/rx-0/rps_cpus"
```
 
to replace it with 0, but no result. Just went to the next line when I hit enter.
 
Could this be because I'm running using Wubi? Wouldn't have thought it would make a difference, but...
 
Anyway, thanks for the help, its appreciated.

---

### Post by bluexrider on 2012-02-13
I was able to use nautilus and go to the file, then right-click and "open as administrator" using that method it opened with my default editor and I was able to save it again after making changes.

---

### Post by jerrrys on 2012-02-13
> **bluexrider said:**
> I was able to use nautilus and go to the file, then right-click and "open as administrator" using that method it opened with my default editor and I was able to save it again after making changes.

Weird.  I can't make any changes either.  This is inside a link, can changes even be made like this?

---

### Post by HiImTye on 2012-02-13
you can do a quick and dirty script like this:[FONT=monospace]
[/FONT]```
sudo rm /sys/class/net/eth0/queues/rx-0/rps_cpus; sudo sh -c "echo <value> > /sys/class/net/eth0/queues/rx-0/rps_cpus"
```but removing it might not be the best idea. it's the best solution I can think of off the top of my head atm

---

### Post by HiImTye on 2012-02-13
oh it went to the next line, like it returned you to the shell? it should do that. to view the value, use[FONT=monospace]
[/FONT]```
[FONT=monospace]cat /sys/class/net/eth0/queues/rx-0/rps_cpus[/FONT]
```I thought you meant it appended it to a new line like
```
00
0
```

---

### Post by bluexrider on 2012-02-13
> **jerrrys said:**
> Weird.  I can't make any changes either.  This is inside a link, can changes even be made like this?

I changed it twice, once to see if it would work and again to the original settings. So I don't know....Guess try something else because this doesnt work either.


```
$ sudo rm /sys/class/net/eth0/queues/rx-0/rps_cpus; sudo sh -c "echo 1 > /sys/class/net/eth0/queues/rx-0/rps_cpus"
rm: cannot remove `/sys/class/net/eth0/queues/rx-0/rps_cpus': Operation not permitted

```
```
cd:/sys/class/net/eth0/queues/rx-0$ ls -l
total 0
-rw-r--r-- 1 root root 4096 2012-02-13 17:23 rps_cpus
-rw-r--r-- 1 root root 4096 2012-02-13 12:54 rps_flow_cnt
cd :/sys/class/net/eth0/queues/rx-0$ 

```

---

### Post by HiImTye on 2012-02-13
to be clear, this is the way that it should work:
> **europaflyer said:**
> HiImTye - I used
 ```
sudo sh -c "echo 0 > /sys/class/net/eth0/queues/rx-0/rps_cpus"
```to replace it with 0, but no result. Just went to the next line when I hit enter.
it should just move to the next line like this:
```
tye@T:~$ sudo sh -c "echo 1 > /sys/class/net/eth0/queues/rx-0/rps_cpus"
tye@T:~$ cat /sys/class/net/eth0/queues/rx-0/rps_cpus
01
tye@T:~$ sudo sh -c "echo 0 > /sys/class/net/eth0/queues/rx-0/rps_cpus"
tye@T:~$ cat /sys/class/net/eth0/queues/rx-0/rps_cpus
00
```

---

### Post by bluexrider on 2012-02-13
The files under /sys/  aren't real files, they're representations of  the kernel's internal state. You can tweak kernel parameters by writing  stuff to them, but as they are not actual files, you cannot delete them.
  If what you want is to put a "1" there, try this:
  ```
echo 1 | sudo tee /sys/class/net/eth0/queues/rx-0/rps_cpus 
```Read more about /sys/ here: [http://en.wikipedia.org/wiki/Sysfs](http://en.wikipedia.org/wiki/Sysfs)

this works

---

