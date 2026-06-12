---
title: "Guest Session question (issue?)"
date: 2011-01-16
forum: General Help
---

### Post by Matt 6:27 on 2011-01-16
I'm going to start with Gen'l Help then maybe slide over to security.  Twice recently, when shutting down for the night, I've noticed a Guest Session has been activated on my system.  Since I'm the only one using this machine, I'm naturally curious.  Can anyone out there explain how Guest Session works and if it can be activated remotely... or otherwise explain how the check mark next to "Guest Session" might be activated?  Thanks in advance!!  - Chris

---

### Post by TeoBigusGeekus on 2011-01-16
```
last
```
from terminal, to see the last logged on users.

---

### Post by Matt 6:27 on 2011-01-18
I ran last and got the following report:

matt@HLDASUB:~$ last
matt      pts/0        :0.0       Tue Jan 18 20:02   still logged in   
matt      tty7         :0         Tue Jan 18 08:59   still logged in   
reboot   system boot  2.6.32-27-generi Tue Jan 18 08:58 - 20:02(11:03)    
matt      tty7         :0              Mon Jan 17 08:33 - down (14:14)    
reboot   system boot  2.6.32-27-generi Mon Jan 17 08:32 - 22:48(14:15)    
reboot   system boot  2.6.32-27-generi Sun Jan 16 21:11 - 23:10(01:59)    
matt      tty7         :0              Sun Jan 16 07:50 - 13:47(05:56)    
reboot   system boot  2.6.32-27-generi Sun Jan 16 07:50 - 13:47(05:56)    
guest    tty8         :1               Sun Jan 16 01:04 - 01:04(00:00)
...    

The guest appears to logged in, but the time logged in is 00:00. Thoughts?
Also, can you explain why I've two "matt"s logged in at the same time (as pts/0 and tty7?

Thanks much!

> **TeoBigusGeekus said:**
> ```
last
```
from terminal, to see the last logged on users.

---

### Post by sydbat on 2011-01-18
> **Matt 6:27 said:**
> I ran last and got the following report:

matt@HLDASUB:~$ last
matt      pts/0        :0.0       Tue Jan 18 20:02   still logged in   
matt      tty7         :0         Tue Jan 18 08:59   still logged in   
reboot   system boot  2.6.32-27-generi Tue Jan 18 08:58 - 20:02(11:03)    
matt      tty7         :0              Mon Jan 17 08:33 - down (14:14)    
reboot   system boot  2.6.32-27-generi Mon Jan 17 08:32 - 22:48(14:15)    
reboot   system boot  2.6.32-27-generi Sun Jan 16 21:11 - 23:10(01:59)    
matt      tty7         :0              Sun Jan 16 07:50 - 13:47(05:56)    
reboot   system boot  2.6.32-27-generi Sun Jan 16 07:50 - 13:47(05:56)    
guest    tty8         :1               Sun Jan 16 01:04 - 01:04(00:00)
...    

The guest appears to logged in, but the time logged in is 00:00. Thoughts?
**Also, can you explain why I've two "matt"s logged in at the same time (as pts/0 and tty7?**

Thanks much!the tty is your regular everyday login status. The pts is you in the terminal.

As for why your 'guest' account was logged in, I am not really sure. Doesn't look like anyone has remoted into your box.

---

### Post by Matt 6:27 on 2011-01-18
Thanks

---

### Post by GeorgeTI on 2011-04-30
I have the EXACT thing with my own PC, and I do have the impression that this is a bug of sorts. At least I am not the only one who has that thing :/ Let me ask you though, do you have any strange ports open, or random hard disk activity? You can check your open ports with nmap:
#nmap your.ip.address.here
You can check your ipaddress with ifconfig. Just type ifconfig, and look at your active connection.
I just want to see if there are the same open ports with me, no need to post your ip address too :)
This thing does creep you out a bit too?

SOMETHING NEW:
Go to the top panel, right click, click "Add to Panel..." and choose  Indicator Applet  Session. The same button will appear. Click that too.  If it does NOT show a v next to the "Guest Session" then it is probably a  glitch or bug. Do you have some occasional glitches at your panels too?  You know, icons appearing only half or not at all etc?

---

### Post by Matt 6:27 on 2011-06-13
I know this is a little old, but yes I'm still seeing this now & then and it is a tad creepy, but I do think it's a bug and not an intruder. I don't have any unusual disk activity or ports open.  It seems to appear only after I've left the system alone for a big chunk of time.  I either let the screen saver come on (which locks the system), or may lock it if I know I'll be gone more than a few minutes.  I haven't followed the scientific method on this one, but it seems like it may be tied to my screen saver.

Re your last question: yes, sometimes I lose the right side of my top panel (e.g., username and logoff button get truncated or cut entirely).  My quick fix is to right-click on the panel to get to "Properties", then change its orientation to another side of the screen for a moment, then back to the top and everything is back where it belongs.

---

