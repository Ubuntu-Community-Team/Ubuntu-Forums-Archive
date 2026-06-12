---
title: "DVDs problem"
date: 2010-06-25
forum: General Help
---

### Post by TroN-0074 on 2010-06-25
until a week ago I was able to play DVDs and copy videos from my hard drive to a blank DVD. Now the DVD player is not mounting the disk at all. If I go to Places > Computer I see the CD/DVD Drive there. But the actual disk is not mounted, the icon is not created on the desktop screen nor Movie Player start playing it as default.
Please I will appreciate some suggestion on how to approach this issue

Thank you.

---

### Post by Don Barzini on 2010-06-25
Was there any changes made about a week ago at the time this happened?

Is your username a member of the **cdrom** group? You can check by looking in the **/etc/group** file.

---

### Post by TroN-0074 on 2010-06-25
> **Don Barzini said:**
> Was there any changes made about a week ago at the time this happened?

Is your username a member of the **cdrom** group? You can check by looking in the **/etc/group** file.

No changes has been done other than the updates from the update manager, and yes my user loggin still appear as user of cdrom in the file.

I will appreciate if you have another advice. Thank you.

---

### Post by Don Barzini on 2010-06-25
> **TroN-0074 said:**
> No changes has been done other than the updates from the update manager, and yes my user loggin still appear as user of cdrom in the file.

I will appreciate if you have another advice. Thank you.

Are you a member of the **operator** group?

Has the machine not been rebooted in a while?

Does this happen with both CD's and DVD's?

Have you tried mounting a DVD manually to a directory that you own?

---

### Post by TroN-0074 on 2010-06-25
> **Don Barzini said:**
> Are you a member of the **operator** group?

Has the machine not been rebooted in a while?

Does this happen with both CD's and DVD's?

Have you tried mounting a DVD manually to a directory that you own?

Thank you for your re-ply

I am the only user of this computer so I am a member of the operator group, And the computer get reboot all the time. It has two devices one is a CD player and works good the other one is a CD/DVD R+W device which is not working at the moment. I have inserted a dvd and try to have movie player open it but it gets the "can't open disc /dev/ sr1" so I dont know what is happening.

Apparently I am the only one with this problem.:confused:

---

### Post by Don Barzini on 2010-06-25
> **TroN-0074 said:**
> Apparently I am the only one with this problem.:confused:

Apparently not. A Google search finds many people having the same problem.

[http://www.google.com/search?hl=en&source=hp&q=ubuntu+10.04+can%27t+open+disc+%2Fdev%2Fsr1&btnG=Google+Search&cts=1277532645092&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=en&source=hp&q=ubuntu+10.04+can%27t+open+disc+%2Fdev%2Fsr1&btnG=Google+Search&cts=1277532645092&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by TroN-0074 on 2010-06-26
I will appreciate if somebody suggest something about this problem I did a
mount disc /dev/sr1 and the return was that device is already mounted
So please some help will be highly appreciate it.

---

### Post by Don Barzini on 2010-06-26
There has been some bug reports filed on this issue. You should read this link....

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092)

There has also been some other threads on this issue. One is here....

[http://ubuntuforums.org/showthread.php?t=1466110](http://ubuntuforums.org/showthread.php?t=1466110)

Those links can give you some ideas on what others have done to solve the problem. Some report the problem not being solved.

---

### Post by TroN-0074 on 2010-06-27
Thank you, I would really like to have more inputs in this matter. By the way the computer in question is a Dell Dimension 2350 with an Integrated Intel 3D Extreme Graphic video controller.
I will appreciate any advice.

---

### Post by TroN-0074 on 2010-06-28
> **TroN-0074 said:**
> Thank you, I would really like to have more inputs in this matter. By the way the computer in question is a Dell Dimension 2350 with an Integrated Intel 3D Extreme Graphic video controller.
I will appreciate any advice.

Bump

---

### Post by nerdy_kid on 2010-06-28
i would first eject the disk, open up the system log either with the log viewer or the command tail -f /var/log/syslog and then insert the disk.  you should see messages about the disk pop up.  post them please :)  also is your laser dirty?  could be a (slight) possibility.

---

### Post by TroN-0074 on 2010-06-28
I dont really know what all this means, but here is the print of what I saw on the console
```
chavez@TroN-0074-desktop:~$ sudo tail -f /var/log/syslog 
[sudo] password for chavez: 
Jun 28 20:57:25 TroN-0074-desktop rtkit-daemon[1172]: Supervising 3 threads of 1 processes of 1 users.
Jun 28 20:57:25 TroN-0074-desktop rtkit-daemon[1172]: Sucessfully made thread 1211 of process 1211 (n/a) owned by '1000' high priority at nice level -11.
Jun 28 20:57:25 TroN-0074-desktop rtkit-daemon[1172]: Supervising 4 threads of 2 processes of 1 users.
Jun 28 20:57:25 TroN-0074-desktop pulseaudio[1211]: pid.c: Daemon already running.
Jun 28 20:57:26 TroN-0074-desktop acpid: client connected from 1225[108:114]
Jun 28 20:57:26 TroN-0074-desktop acpid: 1 client rule loaded
Jun 28 20:57:30 TroN-0074-desktop pulseaudio[1170]: ratelimit.c: 1 events suppressed
Jun 28 20:58:42 TroN-0074-desktop AptDaemon: INFO: Initializing daemon
Jun 28 21:02:07 TroN-0074-desktop anacron[831]: Job `cron.daily' started
Jun 28 21:02:07 TroN-0074-desktop anacron[1630]: Updated timestamp for job `cron.daily' to 2010-06-28
Jun 28 21:03:43 TroN-0074-desktop AptDaemon: INFO: Quiting due to inactivity
Jun 28 21:03:43 TroN-0074-desktop AptDaemon: INFO: Shutdown was requested

```

I will appreciate any advice

---

### Post by nerdy_kid on 2010-06-29
na thats not it, as soon as you reinsert the disk into the drive and it begins to read you should see messages about sr0 like this:

```


Jun 29 09:18:40 jesse-laptop kernel: [20734.857723] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 29 09:18:40 jesse-laptop kernel: [20734.857736] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun 29 09:18:40 jesse-laptop kernel: [20734.857748] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jun 29 09:18:40 jesse-laptop kernel: [20734.857762] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jun 29 09:18:40 jesse-laptop kernel: [20734.857788] end_request: I/O error, dev sr0, sector 0
Jun 29 09:18:40 jesse-laptop kernel: [20734.857797] Buffer I/O error on device sr0, logical block 0
Jun 29 09:18:40 jesse-laptop kernel: [20734.859701] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 29 09:18:40 jesse-laptop kernel: [20734.859711] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun 29 09:18:40 jesse-laptop kernel: [20734.859721] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jun 29 09:18:40 jesse-laptop kernel: [20734.859734] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jun 29 09:18:40 jesse-laptop kernel: [20734.859759] end_request: I/O error, dev sr0, sector 0
Jun 29 09:18:40 jesse-laptop kernel: [20734.859766] Buffer I/O error on device sr0, logical block 0
Jun 29 09:18:40 jesse-laptop kernel: [20734.861440] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 29 09:18:40 jesse-laptop kernel: [20734.861449] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun 29 09:18:40 jesse-laptop kernel: [20734.861460] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jun 29 09:18:40 jesse-laptop kernel: [20734.861473] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jun 29 09:18:40 jesse-laptop kernel: [20734.861498] end_request: I/O error, dev sr0, sector 0
Jun 29 09:18:40 jesse-laptop kernel: [20734.861506] Buffer I/O error on device sr0, logical block 0

```

thats what popped up as soon as the cd started reading.

if nothing pops up then i think something is wrong with your cd drive (like dirty laser possibly).

---

### Post by TroN-0074 on 2010-07-24
I got rid of this problem by installing a new DVD player/writer. Now is working good

---

### Post by ahso4271 on 2010-07-25
how did you install a new DVD player? My CD are not mounted as well so i might try your solution
Thanks

---

### Post by TroN-0074 on 2010-07-25
> **ahso4271 said:**
> how did you install a new DVD player? My CD are not mounted as well so i might try your solution
Thanks

When I bough the new DVD player it came with the instructions on how to installed, If you have your computer's manual it should also have instructions on how to replace pieces.

Good luck to you

---

### Post by bakegoodz on 2010-07-25
Confirms what I though from the first post. Your drive just died, it was a hardware problem.

---

