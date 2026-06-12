---
title: "daemon: unable to open pid file &quot;/var/run/mpd/pid&quot;"
date: 2009-11-29
forum: General Help
---

### Post by chaopoch on 2009-11-29
I installed mpd from Synaptic, but every time I reboot the computer and then try to play songs with mpd, mpd always fails with the error message,

[B][COLOR="Red"]daemon: unable to open pid file "/var/run/mpd/pid": No such file or directory
Aborted[/COLOR][/B]

I have to re-install mpd and run the following commands to make it work, but the same problem will happen again when reboot, any way to fix it? thanks a lot.

sudo mpd --kill
sudo mpd --create-db
mpc listall | mpc add

---

### Post by Locutus_of_Borg on 2009-11-29
sudo mkdir /var/run/mpd && sudo chmod -R +rw /var/run/mpd

that should fix the issue

---

### Post by chaopoch on 2009-11-29
> **Locutus_of_Borg said:**
> sudo mkdir /var/run/mpd && sudo chmod -R +rw /var/run/mpd

that should fix the issue

Directory /var/run/mpd will be created automatically while installing mpd, why should have to create it manually?

---

### Post by chaopoch on 2009-11-29
The problem is that pid file disappears every time the system reboots.

---

### Post by raktarok on 2009-11-29
Is there an /etc/init.d/ entry for mpd? and if you do **sudo /etc/init.d/mpd start**, does it work?

---

### Post by Locutus_of_Borg on 2009-11-30
> **chaopoch said:**
> Directory /var/run/mpd will be created automatically while installing mpd, why should have to create it manually?

because the pid file is created when you launch mpd, so if its saying no such file or directory then something is missing

---

### Post by chaopoch on 2009-11-30
> **Locutus_of_Borg said:**
> because the pid file is created when you launch mpd, so if its saying no such file or directory then something is missing

The problem is that **only** the pid file is lost, the directory /var/run/mpd is still there, so why should I create the directory again? I really don't understand what the is point to create /var/run/mpd manually?

---

### Post by Locutus_of_Borg on 2009-11-30
> **chaopoch said:**
> The problem is that **only** the pid file is lost, the directory /var/run/mpd is still there, so why should I create the directory again? I really don't understand what the is point to create /var/run/mpd manually?

are you saying that the command 'mpd' is not creating the pid file then?

cause it does on my system, and i did have to create that directory and i did have to make it read/write before mpd would work

---

### Post by chaopoch on 2009-11-30
Thanks for replies above, but can anyone tell me **[COLOR="Red"]why the pid file gets lost every time the computer reboots?[/COLOR]** thanks a lot.

---

### Post by raktarok on 2009-11-30
There should be a mpd daemon running and it should start automatically during boot, thus creating the pid file. Immediately after reboot, check if the daemon is running. Use system monitor or the command ps aux | grep mpd.
If the daemon is not running, then there is no question of pid file being created. 

The init script (corresponding to mpd) in the directory /etc/init.d/ handles the automatic start of the mpd daemon. Check if commands like sudo /etc/init.d/mpd start work.

Hope this helped and good luck!

---

### Post by Locutus_of_Borg on 2009-11-30
> **chaopoch said:**
> Thanks for replies above, but can anyone tell me **[COLOR="Red"]why the pid file gets lost every time the computer reboots?[/COLOR]** thanks a lot.

because rebooting ends the process, when the process is not running it gets no pid (process ID), if there is no pid, then you have not run mpd to begin with, you cant use mpd unless you first start it, when you start mpd it gets a process id (pid)

---

### Post by chaopoch on 2009-12-01
> **raktarok said:**
> There should be a mpd daemon running and it should start automatically during boot, thus creating the pid file. Immediately after reboot, check if the daemon is running. Use system monitor or the command ps aux | grep mpd.
If the daemon is not running, then there is no question of pid file being created. 

The init script (corresponding to mpd) in the directory /etc/init.d/ handles the automatic start of the mpd daemon. Check if commands like sudo /etc/init.d/mpd start work.

Hope this helped and good luck!

Of course mpd will start with command 'sudo /etc/init.d/mpd start', my question is **[COLOR="Red"]why the pid file gets lost every time the computer reboots?[/COLOR]**

I also confirm that there are symbol links s30mpd (link to /etc/init.d/mpd) in directories /etc/rc2.d, /etc/rc3.d, /etc/rc4.d and /etc/rc5.d respectively, so why does not the mpd daemon start at bootup?

---

### Post by chaopoch on 2009-12-04
No one knows how to load mpd (music player daemon) at bootup?

I remember mpd was actually loaded before, but just don't know why and since when it does not load at bootup anymore? hope any geek can help, thanks a lot.

---

### Post by chaopoch on 2009-12-04
I open Boot-Up Manager to check the status of mpd service, and find it is activated but not running, that is really weird.

Can I change the start priority of mpd to make it running at bootup?

---

