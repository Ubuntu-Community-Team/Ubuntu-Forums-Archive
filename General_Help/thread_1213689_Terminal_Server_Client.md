---
title: "Terminal Server Client"
date: 2009-07-15
forum: General Help
---

### Post by jalexakis on 2009-07-15
Hello, first off the confession: I´m a newbie. :p

Now the problem: I have installed ubuntu 9.03 on a new machine. This machine is intended to work as a client of a Win 2008 Terminal Server on a remote location. I have started the Terminal server client, the connection worked just fine, but only once. When i try to start the same connection again, it aborts with an "internal licensing error".

So I changed the hostname in the TSC-interface and it worked again, only once. The connection works in general only once for each given hostname. 

I´d be very thankful for any help.

---

### Post by SyL on 2009-07-15
Obviously you have an issue with the license O_o

Not sure but this topic may help: [http://ubuntuforums.org/showthread.php?t=143474](http://ubuntuforums.org/showthread.php?t=143474)

---

### Post by jalexakis on 2009-07-15
> **SyL said:**
> Obviously you have an issue with the license O_o

Not sure but this topic may help: [http://ubuntuforums.org/showthread.php?t=143474](http://ubuntuforums.org/showthread.php?t=143474)

Thanks for answering.

Yes, it seems i do have a licensing issue and unfortunately said thread doesn help. My problem is, the TS issues a temporary license when I login from my ubuntu-box, but I can't login a second time using the same hostname, although the license has another 90 days to expire. Also, i have unused installed licenses, so a second succesful login would lead to a regular license beeing issued to the machine, which would be my goal...

---

### Post by SyL on 2009-07-15
> **jalexakis said:**
> Thanks for answering.

Yes, it seems i do have a licensing issue and unfortunately said thread doesn help. My problem is, the TS issues a temporary license when I login from my ubuntu-box, but I can't login a second time using the same hostname, although the license has another 90 days to expire. Also, i have unused installed licenses, so a second succesful login would lead to a regular license beeing issued to the machine, which would be my goal...


Sorry i never use TS from an Ubuntu box. I even did not know about all those TS license things before i read you post ...
Hopefully someone will have an answer.

You may also consider to use [VNC]("https://help.ubuntu.com/community/VNC").

---

