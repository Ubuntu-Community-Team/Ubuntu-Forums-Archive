---
title: "Why are shutdowns slower in Oneiric?"
date: 2011-12-26
forum: General Help
---

### Post by HunterDX77M on 2011-12-26
After updating from Natty to Oneiric, I noticed that the shutdowns take almost three times as long. Last week, when I shut my laptop down, I went under the table to pull the plug only to realize that it still didn't shutdown when I pulled. What could be the cause? How can I speed up the shutdown (at least to the same speed in Natty)?

Note: it's slower whether shutdown from the command line or from the GUI.

---

### Post by Frogs Hair on 2011-12-26
On my clean installation shutdown is very fast , so you must have a process or application is not shutting down properly. It could be the  last application used or a process running in the background . Before you shutdown run the following command in the terminal to see what is running before shutdown . ```
top
```

---

### Post by HunterDX77M on 2011-12-26
> **Frogs Hair said:**
> On my clean installation shutdown is very fast , so you must have a process or application is not shutting down properly. It could be the  last application used or a process running in the background . Before you shutdown run the following command in the terminal to see what is running before shutdown . ```
top
```

Okay I ran it. But I am not sure of what processes are what and what I need or should get rid of. Can you make any sense of it please?
```


top - 20:08:25 up 43 min,  1 user,  load average: 0.04, 0.09, 0.13
Tasks: 163 total,   3 running, 157 sleeping,   0 stopped,   3 zombie
Cpu(s):  5.5%us,  2.0%sy,  0.0%ni, 92.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4090300k total,  1221772k used,  2868528k free,    89992k buffers
Swap:  1476604k total,        0k used,  1476604k free,   669900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                      
 1680 murshed   20   0  312m  86m  22m R    4  2.2   1:46.53 compiz                                                                                                       
 1153 root      20   0 87508  19m 7940 S    3  0.5   1:28.10 Xorg                                                                                                         
 1778 murshed   20   0  134m  19m  10m R    3  0.5   0:03.55 unity-panel-ser                                                                                              
 2114 murshed   20   0 82184  20m 3828 S    3  0.5   0:55.50 beam.smp                                                                                                     
 2942 murshed   20   0  132m  15m  10m S    1  0.4   0:01.04 gnome-terminal                                                                                               
 1563 murshed   20   0  6260 2824  916 S    1  0.1   0:07.74 dbus-daemon                                                                                                  
  910 messageb  20   0  4380 2096 1136 S    0  0.1   0:02.18 dbus-daemon                                                                                                  
 2080 murshed   20   0 22488  12m 4348 S    0  0.3   0:03.37 desktopcouch-se                                                                                              
 3041 murshed   20   0  2820 1176  868 R    0  0.0   0:00.25 top                                                                                                          
    1 root      20   0  3320 1932 1264 S    0  0.0   0:00.81 init                                                                                                         
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                     
    3 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0                                                                                                  
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                  
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                  
    9 root      20   0     0    0    0 S    0  0.0   0:00.17 ksoftirqd/1                                                                                                  
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                       
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                      
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                                        
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                                                  
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                                  
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                                                                  
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                                                                      
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                                                                      
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                        
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                                                                           
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                                                   
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                      
   25 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                                                         
   26 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                                                                                   
   27 root      20   0     0    0    0 S    0  0.0   0:00.04 fsnotify_mark                                                                                                
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                              
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                                                                       
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                                                                     
  224 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                    
  225 root      20   0     0    0    0 S    0  0.0   0:00.07 scsi_eh_1                                                                                                    
  226 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                                    

```

---

### Post by West201 on 2011-12-26
Welcome to Gnome 3. For some reason I noticed the same. My desktop consumes more power and resources.

---

### Post by Frogs Hair on 2011-12-26
The processes are on the far right and I don't see anything unusual , Compiz and Xorg are for the operation of the desktop environment . I see nothing using a lot memory of CPU . You could check the log file viewer for any thing that may be happening at shutdown .

---

### Post by HunterDX77M on 2011-12-26
> **Frogs Hair said:**
> The processes are on the far right and I don't see anything unusual , Compiz and Xorg are for the operation of the desktop environment . I see nothing using a lot memory of CPU . You could check the log file viewer for any thing that may be happening at shutdown .

Err, how do I do that?

---

### Post by vasa1 on 2011-12-26
> **HunterDX77M said:**
> ... shutdowns take almost three times** as long**. ...
How long in seconds?

---

### Post by HunterDX77M on 2011-12-27
> **vasa1 said:**
> How long in seconds?

I just checked and it was about 16 seconds (give or take a second). Before upgrading to Oneiric, it was usually 5 seconds.

---

### Post by collisionystm on 2011-12-27
when you shutdown, and you have the purple splash screen, press the UP arrow key to show the output. Let us know what it is hanging on

---

### Post by HunterDX77M on 2011-12-29
> **collisionystm said:**
> when you shutdown, and you have the purple splash screen, press the UP arrow key to show the output. Let us know what it is hanging on

It stops for a while when it says "Waiting for remaining tasks to close" and then the next thing on the screen was something called "modem-manager[891]." Any idea what that means? I think that is the one that is taking the most time.

---

### Post by mc4man on 2011-12-29
A known bug that has not been addressed
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)

Myself am now using Wicd so after installing it & setting up, ect. I removed Network manager & shutdowns/restarts are back to normal, about 2 sec's here.

The bug report does mention a workaround that works for some, ie. edit in a new line to /etc/init/network-manager.conf as shown - 

stop on runlevel [06]

---

### Post by collisionystm on 2011-12-29
> **HunterDX77M said:**
> It stops for a while when it says "Waiting for remaining tasks to close" and then the next thing on the screen was something called "modem-manager[891]." Any idea what that means? I think that is the one that is taking the most time.

I was reading and It could be an issue with X server.

kill X manually and then shutdown the system. see if it improves.

switch to TTY1 or 2

CTRL + ALT + F1  ( or F2 )

CTRL + ALT + F7 to return to your desktop

login at the TTY

sudo pkill X

sudo shutdown -P 0

any improvement?

---

### Post by HunterDX77M on 2011-12-29
> **collisionystm said:**
> I was reading and It could be an issue with X server.

kill X manually and then shutdown the system. see if it improves.

switch to TTY1 or 2

CTRL + ALT + F1  ( or F2 )

CTRL + ALT + F7 to return to your desktop

login at the TTY

sudo pkill X

sudo shutdown -P 0

any improvement?

As soon as I typed "sudo pkill X" I was forcibly logged out (rather quickly I must say) and didn't get to type the last line, "sudo shutdown -P 0."

By the way, what does "sudo pkill X" do any way?

---

### Post by collisionystm on 2011-12-29
> **HunterDX77M said:**
> As soon as I typed "sudo pkill X" I was forcibly logged out (rather quickly I must say) and didn't get to type the last line, "sudo shutdown -P 0."

By the way, what does "sudo pkill X" do any way?

it stops X   ( the gui on the screen )

which is why i said to do it at tty1 

lol

---

### Post by collisionystm on 2011-12-29
nevermind, my own logic failed me!

---

### Post by collisionystm on 2011-12-29
you want

sudo service lightdm stop

it stops X

then do

sudo shutdown -P 0

---

### Post by HunterDX77M on 2011-12-30
> **collisionystm said:**
> you want

sudo service lightdm stop

it stops X

then do

sudo shutdown -P 0

I'll try it out and let you know in a little while. For the record, I was using tty1 when I was forcibly logged out. :)

---

### Post by HunterDX77M on 2011-12-30
> **collisionystm said:**
> you want

sudo service lightdm stop

it stops X

then do

sudo shutdown -P 0

Sorry, didn't seem to do it. It still took just as long and still hung up on that modem-manager thing that I mentioned in an earlier post.

---

### Post by HunterDX77M on 2012-01-02
Thread bump

---

### Post by yoramdavid on 2012-01-02
I notice the same here. It is not a fresh install...

I use gshutdown and I notice when I use it to shut the computer down, it is much faster!
Also when I shut down the normal way, a message warns about docky to be not responding and i have to click on shut down any way.
With gshutdown, there are no questions asked.

The command I use in gshutdown to poweroff is:

```
shutdown -h now
```

Regards

---

### Post by chipbuster on 2012-01-02
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

Not sure if this is your issue.

---

### Post by HunterDX77M on 2012-01-07
Bumpity bump

---

### Post by HunterDX77M on 2012-01-25
bump

---

### Post by Maximus559 on 2012-01-25
Try the solution in post #19 of this bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635")

Worked for me. I'm using Xubuntu 11.10, and this brought my boot time down from ~55 seconds to ~35 seconds, and my shutdown time from ~15 seconds to ~5 seconds. Not a bad improvement. I regularly switch between Xubuntu and Windows XP, so these times are fairly important.

---

### Post by HunterDX77M on 2012-01-26
> **Maximus559 said:**
> Try the solution in post #19 of this bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635")

Worked for me. I'm using Xubuntu 11.10, and this brought my boot time down from ~55 seconds to ~35 seconds, and my shutdown time from ~15 seconds to ~5 seconds. Not a bad improvement. I regularly switch between Xubuntu and Windows XP, so these times are fairly important.

Cool thanks. That worked. It shutdown in like 5 seconds just now.

---

