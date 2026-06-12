---
title: "Broken X?"
date: 2010-07-27
forum: General Help
---

### Post by corncob on 2010-07-27
Yesterday I turned on my desktop (eeebox) and Ubuntu came up apparently okay till I tried to move the mouse cursor and nothing happened.  I have a USB optical mouse and the light was out.  Unplugging and plugging it back in turned the light on but it still wouldn't work.  The cursor was blinking in Tomboy Notes (which comes up although I don't want it to) but I couldn't type anything in.  Also [ALT][F2] didn't bring up the command line.  [CTR][ALT][F1] did work.  I didn't do anything in the terminal except to press [CTR][ALT][F7] to bring me back and then everything worked.  The thing is that I do turn the computer off when not in use and I have to do the same thing every time I turn it on in order to use it. (I did set the [CTR][ALT][BACKSPACE] sequence to kill the X server and that works too). Hopefully somebody has some ideas.

---

### Post by linux18 on 2010-07-27
> **corncob said:**
> Yesterday I turned on my desktop (eeebox) and Ubuntu came up apparently okay till I tried to move the mouse cursor and nothing happened.  I have a USB optical mouse and the light was out.  Unplugging and plugging it back in turned the light on but it still wouldn't work.  The cursor was blinking in Tomboy Notes (which comes up although I don't want it to) but I couldn't type anything in.  Also [ALT][F2] didn't bring up the command line.  [CTR][ALT][F1] did work.  I didn't do anything in the terminal except to press [CTR][ALT][F7] to bring me back and then everything worked.  The thing is that I do turn the computer off when not in use and I have to do the same thing every time I turn it on in order to use it. (I did set the [CTR][ALT][BACKSPACE] sequence to kill the X server and that works too). Hopefully somebody has some ideas.
Are you using LXDE by any chance?

in any case the commands to type are:


STEP 1:
-choose recovery mode at grub

STEP 2:
-drop to a root prompt

STEP 3:
-type: 
```

telinit 3

``` and login

STEP 4:
-then type:
```

 xinit

```STEP 5:
-when xinit starts type:
```

metacity &

```- for ubuntu OR:
```

compiz &

```- if you have it OR flux/openbox & - if you have it OR:
```

fvwm4 & 

```- for xubuntu

STEP 6:
-then type:
```

 gnome panel & 

```-for ubuntu OR:
```

 xfce4-panel & 

```-for xubuntu

STEP 7:
-lastly type:
```
 
nm-applet & 

```-for networking

---

### Post by corncob on 2010-07-28
Thank you for the reply.  I'm using gnome.  I went through those steps and all seemed to work except the last (nm-applet &)(anyway I have networking, at least wired which is what I'm using).  However, it didn't help with the problem.  Something I noticed, even before I went through those steps, that if I waited 2 minutes (120 seconds) after everything came up on the screen (which itself seems to take longer than it used to) then the mouse and keyboard started to work.  I guess I should change the wording of my problem from "broken" to "slow".  If I just turned the computer on in the morning and went to breakfast before I started using it, I wouldn't have noticed this.

---

### Post by linux18 on 2010-07-28
get bootchart and post the chart of your boot up, there may be something wrong with a startup item.

---

### Post by corncob on 2010-07-28
I got bootchart but don't know how to use it.  It seems to need a file and I don't know what to tell  it.
```
corncob@eeebox:~$ which bootchart
/usr/bin/bootchart
corncob@eeebox:~$ ls -l /usr/bin/bootchart
lrwxrwxrwx 1 root root 14 2010-07-28 12:11 /usr/bin/bootchart -> pybootchartgui
corncob@eeebox:~$ ls -l /usr/bin/pybootchartgui
-rwxr-xr-x 1 root root 804 2009-12-01 19:38 /usr/bin/pybootchartgui
corncob@eeebox:~$ /usr/bin/pybootchartgui
No path given, trying /var/log/bootchart.tgz
warning: path '/var/log/bootchart.tgz' does not exist, ignoring.
Parse error: empty state: '/var/log/bootchart.tgz' does not contain a valid bootchart

```

---

### Post by linux18 on 2010-07-28
you have to reboot then wait a minute or two and look in /var/log/bootchart/ for a png file which is the "chart". It contains all of the interesting boot up information and can be used diagnostically.

---

### Post by corncob on 2010-07-28
Does this tell you anything?
```
corncob@eeebox:~$ bootchart '/var/log/bootchart/eeebox-lucid-20100728-1.tgz' 
parsing '/var/log/bootchart/eeebox-lucid-20100728-1.tgz'
parsing 'header'
parsing 'proc_stat.log'
parsing 'proc_diskstats.log'
parsing 'proc_ps.log'
warning: no parent for pid '2' with ppid '0'
merged 0 logger processes
pruned 249 process, 0 exploders, 188 threads, and 30 runs
False
bootchart written to 'bootchart.png'
corncob@eeebox:~$ which bootchart.png
corncob@eeebox:~$ 

```
I wasn't able to find a 'bootchart.png' on the computer.

---

### Post by linux18 on 2010-07-28
```
 display /var/log/bootchart/*.png 
```

I'm pretty sure that this is the code

---

### Post by corncob on 2010-07-28
Actually, bootchart.png was in my home directory.  I wonder why my searches didn't show it.  I'll try to attach it -- I never did this before either.

---

### Post by linux18 on 2010-07-28
it's a little blurry, try uploading it to imageshack and link to it. Most of the stuff is self-explanatory and you can probably start a new thread on this problem to attract the attention of users more experienced in this area.

---

### Post by corncob on 2010-07-29
[http://img37.imageshack.us/f/bootchart.png/](http://img37.imageshack.us/f/bootchart.png/)

---

### Post by corncob on 2010-07-29
Thanks to you telling me about imageshack I was able to show a friend my bootchart.png.  He said he didn't see anything wrong with it for the one minute that it covers.  He said its trying to find or start something, times out in 120 seconds, and finally goes on to load the mouse and keyboard after that.  I don't have much attached to the computer beside the mouse and keyboard but disconnected the printer and DVD drive to no avail.  I did do one more thing though:  I disconnected the DSL cable for a couple minutes to check out a neighbor's modem for her.  After that I turned my computer on and everything is fine!  Even the little problems that came along with the slow boot, like unable to switch work spaces, are fixed.  My friend did specifically mention 'network' but it was working so I didn't fool with it.  Unplugging and replugging the DSL line sounds pretty close to doing nothing at all and I'm wondering if it just didn't fix itself lol.  While having the problem I got a lot of errors in the ring buffer (dmesg) that aren't there now:
>  46.648143] usb 1-4: device descriptor read/64, error -110
[   61.865146] usb 1-4: device descriptor read/64, error -110
[   62.080146] usb 1-4: new high speed USB device using ehci_hcd and address 5
[   67.101274] usb 1-4: device descriptor read/8, error -110
[   72.221234] usb 1-4: device descriptor read/8, error -110
[   72.437091] usb 1-4: new high speed USB device using ehci_hcd and address 6
[   73.161101] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 103
[   77.457163] usb 1-4: device descriptor read/8, error -110
[   82.577155] usb 1-4: device descriptor read/8, error -110
[   82.681196] hub 1-0:1.0: unable to enumerate USB device on port 4
[   

---

### Post by linux18 on 2010-07-29
that's very unusual, but sometimes computers are like that! sorry I counldn't respond in the last day or so, I tried to remove plymouth (very bad idea) so a reinstall later (using my own distro (see sig)) and everything is working fine (and only 800MB of disk usage). Sounds like everything is working ok, so mark the thread as solved and feel free to send a private message to me if you experience any problems in the future.

---

### Post by corncob on 2010-07-30
Its a new day and the problem remains fixed!  I'll mark the thread as solved.

---

