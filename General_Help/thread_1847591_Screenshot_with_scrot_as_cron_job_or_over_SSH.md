---
title: "Screenshot with scrot as cron job or over SSH"
date: 2011-09-21
forum: General Help
---

### Post by klockren on 2011-09-21
In older versions of Ubuntu (before 10.10 I think), I could run GUI commands in cron jobs or over a SSH connection if I defined the DISPLAY first.

That does not work anymore, so how do I take a screenshot every five minutes with a cron job, or take a screenshot when I am connected over SSH?

```

# DISPLAY=:0
# scrot
giblib error: Can't open X display. It *is* running, yeah?
#
# DISPLAY=:0.0
# scrot
giblib error: Can't open X display. It *is* running, yeah?

```

---

### Post by scarleo on 2011-09-21
Hmm, guess there is a :0 display active and someone logged in, right? Otherwise, if it's not active, it won't work. Did you try connecting to SSH with -X ? That's to forward X to your remote through SSH.

---

### Post by klockren on 2011-09-21
It worked flawlessly with old Ubuntu versions.
There is an active display, as the ssh connection I am working in is a
```
ssh localhost
``` from Gnome Terminal.
This guide (GUI part) does not work any more:
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

Has Ubuntu stopped using the XAUTHORITY environment parameter? Do I have to use X forwarding instead? How about cron jobs then?

---

### Post by scarleo on 2011-09-21
Can you post your actual cron job line?

---

### Post by klockren on 2011-09-21
The cron job calls this shell script:

```

#!/bin/sh
pushd /root/scrot
export DISPLAY=:0  
#export XAUTHORITY=/home/user/.Xauthority
scrot -z
popd

```

Cron job:
```
*/5 * * * * /root/scrot/scrot.sh
```

---

### Post by klockren on 2011-09-21
Also, I can not use X forwarding as I will first have to SSH to a firewall with busybox and it does not support X forwarding. And I much rather run this as a cron job!

---

### Post by scarleo on 2011-09-21
> **klockren said:**
> Also, I can not use X forwarding as I will first have to SSH to a firewall with busybox and it does not support X forwarding. And I much rather run this as a cron job!

Now hold on a second, you said you were doing this on localhost before? Hmmm, well ok, anyway, so did you try it the way the guide suggests that you linked me to before? I mean with *env DISPLAY=:0* on cron job and not have the display part in your script?

---

### Post by klockren on 2011-09-21
Yes I am testing this on the local machine first. Of course, ssh -X localhost works when being on the local machine.

Yes I tried the guide, and this link [http://askubuntu.com/questions/21923/how-do-i-create-the-xauthority-file]("http://askubuntu.com/questions/21923/how-do-i-create-the-xauthority-file") sais that .Xautority isn't used in recent Ubuntu versions. It works to manually do a 'scrot' if I set the display AND point the XAUTHORITY environment variable to the new location in /var/run/gdm/. So how can I make this cron job work then???

---

### Post by scarleo on 2011-09-21
Maybe try setting both DISPLAY and XAUTHORITY in cron line, like 

*/5 * * * * env DISPLAY=:0 XAUTHORITY=/var/run/gdm /root/scrot/scrot.sh

(not sure if it needs another env right before XAUTHORITY, try) and of course remove it from your script then.

---

### Post by klockren on 2011-09-21
> **scarleo said:**
> Maybe try setting both DISPLAY and XAUTHORITY in cron line, like 

*/5 * * * * env DISPLAY=:0 XAUTHORITY=/var/run/gdm /root/scrot/scrot.sh

(not sure if it needs another env right before XAUTHORITY, try) and of course remove it from your script then.

But the file has a random name and resides in /var/run/gdm, I will need the whole path, e.g. /var/run/gdm/auth-for-johndoe-wUM1sV/database

---

