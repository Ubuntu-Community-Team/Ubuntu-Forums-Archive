---
title: "Update problem"
date: 2006-04-13
forum: General Help
---

### Post by Anilkumar on 2006-04-13
Hello everybody,

I am getting for update. when i type apt-get update. i am getting this following error .

what is this error?
what should i do?

plz fix me


anilkumar@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory
anilkumar@ubuntu:~$ sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Qrk on 2006-04-13
You can't use apt-get when synaptic or update-manager is running. Close out of those programs and you should be fine. That gets rid of the second error, the first is because you need to use "sudo apt-get update"

---

### Post by xenon2000 on 2006-04-19
I too ran into this issue when I SSH'd to my server and tried to sudo apt-get,

Even doing sudo, I get the 1st error:

Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

So this is what I did via SSH:

ps aux | grep synaptic

Listed:
gksu /usr/sbin/synaptic
/usr/sbin/synaptic

Of course it also listed the pids, so I did a
sudo kill <PID> for each one and done.

Now sudo apt-get is working fine via SSH for me. :)

---

