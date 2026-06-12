---
title: "Ubuntu does not shutdown"
date: 2012-05-06
forum: General Help
---

### Post by Dutch-Man on 2012-05-06
i've recently installed Ubunt 12.04 and i love it. However i have one problem; i am unable to shutdown or reboot properly.

When i shutdown my laptop (acer aspire 5560) it hangs on the 5 dots and stays there.

When i reboot my laptop it does shutdown but when it boots back up it stay's on the purple screen (no logo what so ever)

Thing's ive id to stop this: 
"sudo service network-manager stop" before shutdown - nothing 
Adding some lines the the GRUB file - nothing 
installed other Ubuntu versions - nothing 
"sudo shutdown -h now" - nothing
"sudo init 0" - nothing
"sudo halt" - nothing

and some more.

At the moment i see a black screen in front of me with the text "Asking all remaining processes to terminate [OK]" and the 5 dots with only the last one orange.

On other tries i got this thing: "modem-manager:could not get the system bus......"

I first had Ubuntu dual boot Windows. And then it worked fine. However after a fresh install of Ubuntu alone i got this.

Afer booting into recovery mode i got this error: 
"unmount: /run/lock: not mounted" 
"Will now halt"

And there it stays.

---

### Post by Mark.R on 2012-05-06
Hi Dutch-Man,

are you using a NAS with cifs(samba) ?

I got the same problem and -sorry- no solution.
This solution [https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825) 
don´t work for me - but try for yourself.

---

