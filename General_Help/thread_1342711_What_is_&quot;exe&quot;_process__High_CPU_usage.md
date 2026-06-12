---
title: "What is &quot;exe&quot; process?  High CPU usage"
date: 2009-12-01
forum: General Help
---

### Post by mizunoX on 2009-12-01
Anyone know what this process is?

"exe"..  I've seen it stuck at 100% cpu usage at times in the past.
I killed it and it came back a few hours later w/ high cpu usage again as you can see in the screen shot.

What is this?

---

### Post by jrusso2 on 2009-12-01
Are you running or installing anything that uses WINE?

---

### Post by mizunoX on 2009-12-01
> **jrusso2 said:**
> Are you running or installing anything that uses WINE?

That was my first thought too.
I have wine installed and one application which is the apple airport configuration utility.  I haven't used it since starting my computer though.

Maybe still?

---

### Post by JBAlaska on 2009-12-01
Kill it and see what happens..

---

### Post by bolucpap on 2009-12-01
Also, if you enter ```
wineserver -k
``` from the terminal and the process dies, you will know for sure that it's spawned by WINE. If it keeps going, then it was started by something other than WINE.

---

### Post by mizunoX on 2009-12-01
Okay, I figured it out.  Thanks for the help guys.

It's the Adobe Flash plugin.
I'm using beta version 10.1 - maybe that's why it's stuck in memory from time to time.
I tested this by playing a youtube video then killing the exe process.  The video changes to an error message.

---

### Post by martini1179 on 2009-12-02
Funny thing, though, I've NEVER seen the exe process until yesterday. And I haven't updated my flash player in several months. 

Usually, when I have high CPU usage and a high memory usage, it's a "chrome" process that it the culprit (I'm using Chrome 4.0.249.21). I kill it and my flash dies, so I'm guessing that that's the flash player. "Exe" never came up before yesterday. It almost seems as if it took over memory leak duties from the previous chrome (flash player) plugin. 

Strange, no? Anyone have an answer for this?

---

### Post by idodos on 2009-12-03
I've also just now got that "exe" process taking up all the resources. Weird.. perhaps a recent update?

---

### Post by sonicbs on 2009-12-04
Started experiencing the same thing a couple of days ago.
Is there a bug report about this?

---

### Post by Agroth on 2009-12-06
I've got the exact same problem here. youtube and such is working okay, but flash games are impossible. "exe"process goes up to ~80%

---

### Post by thib on 2009-12-08
Same problem here. Probably coming from one of the laste update of chromium...

---

### Post by Zorael on 2009-12-08
It seems to (always?) max out at nigh-100% usage when resuming from suspend or hibernate. I have a script ready to put into /etc/pm/sleep.d/ to automatically kill any exe processes when resuming/thawing, but I want to log the event a bit first.

---

### Post by gradinaruvasile on 2009-12-08
Its a Chromium process, actually the Flash player. And a hungry one aswell.

---

### Post by plafond on 2009-12-08
I'm currently having the same issue.  I did recently update my chromium install to:

build: 4.0.263.0 (Ubuntu build 33682)


I don't recall seeing the issue before updating my chromium instance.

@martini1179 - I also haven't updated my flash plugin in a while.  I'm guessing the 'exe' process is a new plugin wrapper that chromium introduced (recently?).


Hopefully this issue gets resolved soon.

---

### Post by rgrig on 2009-12-16
The link /proc/<pid>/exe always points to the executable of the process with the identifier <pid>. Also, /proc/self/exe points to the executable of the current process. So, strictly speaking, the 'exe' process can be anything.

Using 'ps -eo pid,ppid,args' (perhaps in combination with grep) you can see what is the parent (ppid) of the exe process and then look up that one to see what it is. In othe word: (1) find the line that says /proc/self/exe in the third column, (2) see what number X it has in the second column, (3) find the line that has X in the first column, and (4) see what is in the third column of that line.

It's likely you'll discover that the problem is chrome. Apparently chrome starts itself with certain arguments in order to start an extension. Now you can start Task Manager in Chrome (Shift-Escape) and see what uses lots of CPU or memory. In my case, the GMail Checker extension uses about 180MB. That's not really acceptable :P

---

### Post by marcoc2 on 2009-12-16
Same here.

exe flash process takin ~90% of cpu and after some time memory usage goes to ~500mb

I'm using Chromium 4.0.270.0 (Ubuntu build 34458) and this is starting to piss me off..

---

### Post by Zorael on 2009-12-17
Well, kill it. :3
```
$ killall exe
```
But as rgrig said, you could be killing something entirely different.

You can probably also use the built-in task manager in Chromium; a bit more reliable, that. (Shift+Esc)

---

### Post by JokerNishki on 2009-12-17
Same problem, but I use google chrome 4.0.249.43...think it's in beta. From 90MB ram usage in just few minutes it's eating 200+. Only opened facebook and this forum. CPU usage is litle bit over 30% and swap is 10MB.

---

### Post by promet on 2009-12-26
I have been experiencing this as well, with Goole Chrome 4.0.249.43. 

I am wondering though, do you guys experience, what appears to be, excessive Hard Disk I/O at the same times that the "exe" process decides to go wild?

I say "appears to be" because my disk activity light goes on, pretty much solidly, but a desktop disk activity widget shows no really unusual read/write activity at the same time. Unsure what to make of that...

---

### Post by igor47 on 2009-12-28
I just uninstall (purged with aptitude) flashplugin-installer and have no further issue.

Using Chromium 4.0.284.0. And my flash sites are rendering fine.

I don't know why I needed flashplugin-installer in the first place - still - maybe this info can help a few who are experiencing the same annoying CPU usage problem.

---

### Post by wolf2588 on 2010-01-02
well, how did you purged?? there are noobs here so please give us some details

Don't get me wrong but, if people start giving details on how to do stuff, specificly, maybe the newbie team could stop asking this kind of questions always.

So you said you purged the flash-installer, how can I do this in order to post my results?


Thanks, happy new year btw

---

### Post by DeMus on 2010-01-02
> **gradinaruvasile said:**
> Its a Chromium process, actually the Flash player. And a hungry one aswell.

My Chromium build is "4.0.285.0 (35334) Ubuntu" and when I visit Youtube and start a video System monitor also shows exe, but it takes 0% of the CPU.
When yours is going up to 100% you either have a version which is not correct in that field or something else is wrong in your installation. You have the right graphics driver installed? When you watch Youtube with an other browser what happens then?

---

### Post by monster on 2010-01-07
I have 4.0.288 and have the same problem. I turned off plugins running $google-chrome --disable-plugins

---

### Post by Zorael on 2010-01-07
Remember that you can pop up Chrome/Chromium's internal task manager with shift+ESC and monitor the cpu and memory usage of tabs, extensions and plugins. If it's soaring, just kill it there, from another system monitor or from a terminal.

```
#!/bin/bash
# Script to kill Chromium Flash processes

pid=$(ps x | grep libflashplayer.so | grep -v grep | awk '{ print $1 }')

if [ "$pid" ]; then
  echo "Killing process: $pid"
  kill $pid
else
  echo "Could not find pid of Flash process"
fi
```

---

### Post by promet on 2010-01-07
> **wolf2588 said:**
> well, how did you purged?? there are noobs here so please give us some details

Don't get me wrong but, if people start giving details on how to do stuff, specificly, maybe the newbie team could stop asking this kind of questions always.

So you said you purged the flash-installer, how can I do this in order to post my results?


Thanks, happy new year btw

to "purge" an installed package, you would use the following command:

```
sudo apt-get purge <package-name>
```

Where "<package-name>" is, of course, the name of the package that you want to uninstall, in this case, I guess, <package-name> = "flashplugin-installer" (Also, of course, without the quotation marks)

Hope that is helpful...

Cheers! ;)

---

### Post by davidacampbell on 2010-02-12
I see the same thing here.  I have to kill it off because it makes the system quite slow.

---

