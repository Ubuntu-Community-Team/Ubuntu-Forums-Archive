---
title: "compiz memory leak?"
date: 2011-05-14
forum: General Help
---

### Post by kuntau on 2011-05-14
This has happened a couple of times but this is the only time I managed to see what the cause of this problem. Before this when I leave my computer overnight and when I wake up the system already not responsive I'am not been able to turn wake my monitor from standby.

This time I just go out for couple of hours and when I get back my computer already become sluggish. So a quick check with System Monitor I found out compiz is using 2.4GB from my total memory of 4GB and 100% swap was used.

Anyway picture worth a thousand words. So here it is.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192133&stc=1&d=1305391795[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192134&stc=1&d=1305391795[/IMG]

---

### Post by mc4man on 2011-05-14
Are you using the indicator-multiload? ( or similarly named

If so then get rid of - it causes a continual mem leak in unity - if that's what you're using?

There are some very small compiz leaks, mainly per use of the dash and the places, nothing that would cause anywhere what you see

If inclined post - (put in a code box or attach text file
```
ps -A u
```

Edit: as example - this machine has been online for about 8 hrs., lots of activities - compiz is only using around 100MB, this machine boots up @ about 75MB RSS

> $ pidstat -r -p ALL |grep compiz
01:46:22 PM      3737     11.59      0.00  267728  99848   3.23  compiz


---

### Post by kuntau on 2011-05-14
Hi thank you for the reply. I don't know what is indicator-multiload and I can't even find it on my system so I guess I don't have it installed.

Anyway here is my *ps -A u* result

[http://pastebin.com/iEEFDGLL](http://pastebin.com/iEEFDGLL)

edit:
ok before I make the first post I do compiz --replace and solve the 2.4GB memory usage and now here is my compiz memory usage, still climbing up.

```
pidstat -r -p ALL | grep compiz
02:18:24 AM     19583      2.18      0.01  882692 296980   7.32  compiz

```

---

### Post by mc4man on 2011-05-14
Well, whatever is setting compiz off is not normal.
I think I'd start with a fresh boot, _do nothing_ and see what happens w/ compiz (don't use system monitor to ck., either pidstat, free -m or htop
If it starts climbing anyway then you'd want to disable unnecessary processes and then see if you can figure out what's causing.

If it remains relatively static from a fresh start then start up things one at a time, ect.
In that case use the pidstat as below but don't log, you'll be able to see in the terminal in realtime as you start things up

You could set up a logging of comiz w/ pidstat though maybe not useful yet (get the pid, then something like this - 1st # is sec's between reports, 2nd is the number of reports
pidstat -r -p XXXX 30 100 >> compiz_mem.log

Would be interesting to see what you have right after a fresh boot (wait about 30 secs, if you wanted to re-run after a bit and append then use >> instead

pidstat -r -p ALL > base_mem.log

What is "indicator-virtualbox" and do you know why you have all these volume monitors running?

---

### Post by kuntau on 2011-05-14
Hi. I just reboot my machine so here is my current pidstat for compiz. I'm logging now using your command above and will report back.

```

03:29:26 AM      2116    182.62      0.01  705536 142160   3.50  compiz

```

Indicator-virtualbox is some applet I got on taskbar (what should I call it? near the clock) for launching my vm.

Sorry but what do you mean by volume monitor running? I got banshee running on background and I have MS SideWinder X6 keyboard with volume knob if that help.

Thank you

---

### Post by mc4man on 2011-05-14
> you mean by volume monitor running?
I see these 2, not familiar with
/usr/lib/gvfs/gvfs-afc-volume-monitor
 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor

It still would be useful to see what was running at start up (from a fresh start, what I mentioned as the base_mem) Your 142MB above is a bit high, though that could depend on what's running at the start.

Generally here on several different machines unity from fresh boot starts w/ comiz at between 70 - 85 MB.
  I fully expect it and several other processes (Xorg, nautilus, ect.) to rise a bit in RSS over the course of a session
(some I believe is proper, some not so.

---

### Post by kuntau on 2011-05-14
> **mc4man said:**
> I see these 2, not familiar with
/usr/lib/gvfs/gvfs-afc-volume-monitor
 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor

It still would be useful to see what was running at start up (from a fresh start, what I mentioned as the base_mem) Your 142MB above is a bit high, though that could depend on what's running at the start.

Generally here on several different machines unity from fresh boot starts w/ comiz at between 70 - 85 MB.
  I fully expect it and several other processes (Xorg, nautilus, ect.) to rise a bit in RSS over the course of a session
(some I believe is proper, some not so.

To be honest I also don't know where it come from and I don't know how to track where it come from too :(

Anyway after 2+ hours this is what I got.

ps -A u > [http://pastebin.com/DCXraLjV](http://pastebin.com/DCXraLjV)

compiz memlog > [http://pastebin.com/CKDrmxUj](http://pastebin.com/CKDrmxUj)

```
05:47:48 AM      2116     21.08      0.00  719852 254976   6.28  compiz
```

---

### Post by mc4man on 2011-05-14
Possibly I was confusing you - so to clear up?
First forget about those volume monitors - I see them here, not important.

There are small leaks in natty inc. compiz, but normally nothing close to approaching what you showed in post 1

addon indicators can be suspect, the indicator-multiload is one example

What I thought you should do - 
Restart to clear all, take a reading to establish what's running by default and how much mem in use.
Leave the pc alone for a period of time and them take another reading (maybe an hr.
( if you have chrome starting by default than I'd disable for the moment
Delete any logs and just use this to start and after a period of no activity run again to compare

```
free -m >> base_mem.log &&  pidstat -r -p ALL  >> base_mem.log
```


If mem use has increased more than a small amount then something you're starting by default is the cause.
If it hasn't, then start processes one by one, wait a bit and recheck just compiz itself to see if it starts going up significantly in the RSS value

Some current open bugs
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/720446](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/720446)
[https://bugs.launchpad.net/indicator-multiload/+bug/779717](https://bugs.launchpad.net/indicator-multiload/+bug/779717)

---

### Post by nlucaroni on 2011-05-18
I have had my compiz take up ~13GB of Memory twice in the past two days. Doing `compiz --replace &` in a terminal temporarily fixes the issue. 

I do have the indicator-multiload running; I just uninstalled it and hopefully wont run into another problem. I cannot imagine 13GB being consumed by a little indicator, and will report back if I can narrow this consumption down.

---

### Post by TwoD on 2011-05-18
I get the same symptoms with filled RAM and swap several times a day. I've got 4GB RAM and 2GB swap. I upgraded the RAM a while ago but only noticed today I forgot to increase the swap space. That has not been a problem until I upgraded to Natty though since swap usage never went above 200MB before.

I've previously been able to recover without a full reboot by killing compiz and restarting it. For some reason Unity/Compiz will not notice that my desktop is stretched across two windows with TwinView so I also have to swap back and forth too another resolution for Unity's element to reposition themselves correctly.

Thanks to mc4man for the indicator-multiload tip and nlucaroni for the ```
compiz --replace &
``` tip! It seems to have taken care of things for now.

If killing indicator-multiload helped for you too, I suggest subscribing to [https://bugs.launchpad.net/indicator-multiload/+bug/779717](https://bugs.launchpad.net/indicator-multiload/+bug/779717) and also click the "This bug affects # people, does it affect you too?"-link.

There's also [https://bugs.launchpad.net/unity/+bug/720446](https://bugs.launchpad.net/unity/+bug/720446) which seems interesting.

---

### Post by mc4man on 2011-05-18
> If killing indicator-multiload helped for you too,....
If using Unity then that indicator can't be used, and if adding any other indicators one should ck. and see if there are any ill effects
(either in compiz mem use, the indicator itself or supporting libs of the indicator.

The other bug is long-standing and has gone thru several variations - atm there is a per use penalty of certain functions - some I think may be expected (initial use of the various elements) , some not - the continual _small_ bump per repeated use

---

### Post by nlucaroni on 2011-05-19
Stayed stable overnight.

I have the weather-indicator and dropbox indicator running without any issues. What is the best alternative for load indicator?

(I like to see it to easily know if my co-worker is running jobs on my system).

---

### Post by cdysthe on 2011-05-21
> **kuntau said:**
> This has happened a couple of times but this is the only time I managed to see what the cause of this problem. Before this when I leave my computer overnight and when I wake up the system already not responsive I'am not been able to turn wake my monitor from standby.

This time I just go out for couple of hours and when I get back my computer already become sluggish. So a quick check with System Monitor I found out compiz is using 2.4GB from my total memory of 4GB and 100% swap was used.



I'm having the same problem. It started about a week ago on my Natty 64 bit laptop. Compiz eats 1.5 to 2.5 gb memory which isn't released.

---

### Post by nlucaroni on 2011-05-25
As mentioned, are you running the load indicator?

I've been running for about a week straight and it has been stable at 800MB. What plugins are enabled? (I'm using Desktop Cube with Unity, and some Windows Management plugins).

---

### Post by nasrat on 2011-08-12
This is happening to me,

ubuntu 64bit, I do not have indicator multiload at all, I do have other indicators and custom icons.

[check-gmail]("http://checkgmail.sourceforge.net/")
[minbar]("https://launchpad.net/ubuntu/natty/+package/minbar")
dropbox

+ standard unity/ubuntu indicators.

The problem is not isolated with a specific indicator, its a compiz bug as stated earlier in one of the posts here, the indicators use a feature which is severely damaged in compiz.

---

### Post by nasrat on 2011-08-21
> **nasrat said:**
> This is happening to me,

ubuntu 64bit, I do not have indicator multiload at all, I do have other indicators and custom icons.
[...]
dropbox


I think it is dropbox, Even with kwin (KDE) I am getting massive memory leaks. I disabled dropbox on autostart for now, testing.

---

### Post by habtool on 2011-09-04
> **nasrat said:**
> I think it is dropbox, Even with kwin (KDE) I am getting massive memory leaks. I disabled dropbox on autostart for now, testing.

I have removed dropbox from startup applications, logged out and back in again. I ran the PC over night and compiz memory was stable.
So in my case it looks like dropbox was the culprit.

Thanks @nasrat

---

### Post by TwoD on 2011-12-14
> **mc4man said:**
> If using Unity then that indicator can't be used...
Umm, yes it can. It's in the Universe repo.

---

### Post by mikevp on 2012-02-01
I've been seeing the same thing on Oneric.  The symptom was that I'd come in to work, and my system would not come back from the screen blanker - nothing visible but the cursor.  I could type in my password, and it seemed like something was happening, the cursor would change to the "busy" indicator for a while, but it would never unblank the screen. Until now, the only way to get it back was the power button.

A few days ago, I found the config to enable CTRL-ALT-BS to kill the X server.  This morning, I tried that, and it did unblank, and I was able to log in.

I found compiz was using over 2 GB (out of 3 GB), and the system was running very, very slowly.  I did a kill -9 on the compiz process (it ignored lesser kills), it restarted itself, and everything sped up to normal.

Lacking a fix yet, I think I'm going to set up a cron script to do the compiz --replace & thing if compiz ever takes up more than 100 meg or so.

Edit: I just did that.  Crontab I added:

> 0 5 * * * if [ `ps --no-headers -o pmem -C compiz | sed -e 's/\..*//'` -gt 10 ]; then DISPLAY=:0 compiz --replace >/tmp/compiz.rep 2>&1 &; fi
That'll kill it if it ever takes up more than 10% of my system memory.  (Currently, it's taking 2.1%.)

---

### Post by mikevp on 2012-03-05
Well, compiz --replace often fails to restart compiz.  So,  my current crontab is

> 0 5 * * * if [ `ps --no-headers -o pmem -C compiz | sed -e 's/\..*//'` -gt 10 ]; then pkill -9 compiz; fiWhen I ssh into the afflicted desktop and pkill -9 compiz, that works, and compiz  usually respawns.   But when compiz has gone rabid, it uses so much system resources that it takes quite a while to get logged in.

---

### Post by mikevp on 2012-05-08
Well, I had hoped that this would get better in Pangolin, but it's worse.  Much worse.

I don't have indicator-multiload, but I just went into apt-get and removed several of the indicators I do have.  We'll see if I got the one that was causing the problem, if it was an indicator that's doing it.

The ones I still have are: appmenu datetime application session

I like having the calendar instantly available.  I'm not sure if the others do anything that I care about.

The ones I removed were sound power messages printers telepathy

---

