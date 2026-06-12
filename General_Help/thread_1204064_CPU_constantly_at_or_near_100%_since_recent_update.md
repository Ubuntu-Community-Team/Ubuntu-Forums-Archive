---
title: "CPU constantly at or near 100% since recent update"
date: 2009-07-04
forum: General Help
---

### Post by vor0nwe on 2009-07-04
It's an Intel Pentium(R) 4  CPU 3.20 GHz with HyperThreading, with 3 GB RAM.

Since the previous automatic update (I think it was sometime last week, or the week before that), whenever I start Ubuntu, the processor is constantly using between 85% and 100% of its capacity, even when I&#8217;m not running any programs.

I&#8217;ve got the system monitor applet on my panel, which shows me that.  Before that update, it averaged at about 5%.  The system fan now constantly blows furiously, whereas it would quiet down when I wasn't doing anything.

Funny thing is, when I open the full-fledged system monitor, I can't figure out how it gets to the total of 100%... (Perhaps that's also because even when I sort the list by CPU consumption, the biggest consumers aren't always at the top.  Very irritating).

EDIT: I just discovered that the console command 'top' seems to be more accurate.  That shows that Xorg is eating up between 15% and 45% of my CPU capacity.  So that seems to be the culprit.

Does anybody have the same problem, or any indications what could be causing this?  And especially: how can I fix this?

Thanks in advance,
-- 
Martijn

---

### Post by vor0nwe on 2009-07-04
Disabled System/Preferences/Remote Desktop, and all is back to normal.  I saw some other posts that vino-server is the culprit, which is the same thing.

So it seems the choice is: remote desktop enabled, or CPU hogging. :-(

I guess I'll have to look into an alternative VNC server...

---

### Post by tipiglen on 2009-07-04
The "system monitor" [system/administration/system monitor] seems to eat cpu time from the moment the "reources" tab is selected.  the graphs go from mid-range to the top of the scale and remain there.  

Top shows:```
3888 ed        20   0 31280  18m  13m S   73  3.7   0:39.80 gnome-system-mo    
 2826 root      20   0  360m  18m 8060 R   54  3.8   0:43.75 Xorg               
 3299 ed        20   0  243m 114m  23m R   49 23.0   2:57.19 firefox            
 3296 ed        20   0 34072  11m 7404 S    3  2.3   0:01.60 gnome-terminal     
 3605 ed        20   0 16512 2484 1328 S    2  0.5   0:00.94 gnome-screensav    
 3885 ed        20   0  2448 1188  912 R    1  0.2   0:00.51 top                

```
NOT A VERY USEFUL DEVICE!

In fact, leaving it running while typing the above caused a shutdown!

N.B. signature is inaccurate - now on Jaunty

Peace in all dialects:
<a href="http://home2.btconnect.com/tipiglen/loveandpeace3.gif"><b>Salaam/Shalom/Shanthi/Peace</b></a>
   Namaste -ed

---

### Post by lovinglinux on 2009-07-04
> **vor0nwe said:**
> Disabled System/Preferences/Remote Desktop, and all is back to normal.  I saw some other posts that vino-server is the culprit, which is the same thing.

So it seems the choice is: remote desktop enabled, or CPU hogging. :-(

I guess I'll have to look into an alternative VNC server...

Yes, vino-server is causing this very often.

You should try ssh. It's really a powerful method of connecting remotely. If you enable X forwarding you can launch applications from the remote machine on the local machine. You don't see the desktop of the remote, but you can do pretty much anything you need.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

