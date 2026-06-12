---
title: "What is process name of Flash player running inside Firefox?"
date: 2010-01-09
forum: General Help
---

### Post by abcuser on 2010-01-09
Hi,
using Ubuntu 9.10 I open up Firefox and run a video from youtube.com web page. How can I monitor if flash player is running using terminal ps (process) command? What is the flash player process name?
Regards

---

### Post by x33a on 2010-01-09
it doesn't spawn a separate process yet. though firefox devs are planning on adding this functionality to later releases.

---

### Post by abcuser on 2010-01-09
I have written small bash program to control how many hours can some games on Ubuntu be played by children. Bash script is checking if games are played for more then 1 hour and then kills any "game" process (I have made a list of games, so I know what to kill).

But now I have discovered that children are smart and when time expires they fire Firefox and start playing flash games over internet. I would like to omit time they are playing games to max. 1 hour per day. I thought the blocking would be the easiest way by killing flash process after 1 hour of playing. But I don't want to kill a browser, because children also need internet for school work.

So is there any way I could block flash animations e.g. block flash entirety after 1 hour of playing? Like fire some add-on to block flash or something similar. Any idea?

The other idea was to block some internet web sites by firewall (iptables), but I quickly found out that children finds new games on internet. So disabling flash animations would be the best way of doing it after 1 hour of playing time expires.

---

### Post by stoneage on 2010-01-09
What about killing npviewer.bin? That will kill any flash or video running in a browser.

---

### Post by abcuser on 2010-01-09
stoneage, in Firefox 3.5.7 in Ubuntu 9.10 I have started youtube.com video and executed:
```
ps aux | grep npviewer
```
and got no process back. How can I find out PID (process id) with ps command for flash animations?

---

### Post by stoneage on 2010-01-09
I think it only starts when Flash or something like it is running in a browser.

Look in the System Monitor. System -> Administration -> System Monitor -> Processes.

......or use top when video/Flash is running.


EDIT - I get:-
> 
organic@organic-desktop:~/blender$ ps aux | grep npviewer

organic   5976  1.8  2.1 235244 43476 ?        Rl   17:36   1:17 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/2619-3
organic   6060  0.0  0.0   7340   892 pts/0    S+   18:47   0:00 grep --color=auto npviewer

Is the difference maybe that I use 64 bit Ubuntu?

---

### Post by x33a on 2010-01-09
@ stoneage

which browser are you using? i think you are using chrome.

---

### Post by abcuser on 2010-01-10
Hi,
I have solved the problem using help from [Firefox form](http://forums.mozillazine.org/viewtopic.php?f=7&t=1689015&p=8416585).

For using flash Firefox uses /usr/lib/flashplugin-installer/libflashplayer.so libary.
When time expires I disable read access to this library. I have written the following commands to disable flash:
```

chmod -r /usr/lib/flashplugin-installer/libflashplayer.so
killall firefox

```
and "chmod +r file" to enable flash in Firefox.

Note: Killing firefox is required, because when library is once loaded there is no more access to this.
Regards

---

### Post by stoneage on 2010-01-10
> **x33a said:**
> @ stoneage

which browser are you using? i think you are using chrome.

Firefox 3.5.6

---

