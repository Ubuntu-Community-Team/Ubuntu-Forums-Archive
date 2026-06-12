---
title: "cron job starts before all kernel modules are loaded"
date: 2011-04-22
forum: General Help
---

### Post by shadowlmd on 2011-04-22
I have an @reboot cron job (virtual machine) that depends on a kernel module (vboxdrv). It was working fine for a long time but I believe since last kernel upgrade (2.6.32-31-server) it fails because vboxdrv kernel module is not loaded yet. Is is a bug in latest kernel or I was just lucky before and I will have to insert something into a cron script to wait for vboxdrv loded before starting virtual machine?

---

### Post by DaithiF on 2011-04-22
Hi,
probably a stupid question, but is vboxdrv definitely loading, just too late for the cron job?  (a kernel upgrade may require a recompile of the vboxdrv module ... which would mean the old one wouldn't load) ... **lsmod | grep vboxdrv** to check

if it is eventually loading, but too late for the cron @reboot job, then one solution would be to add a while / sleep loop to your script to wait for the module to be loaded.  something like:

```
while ! lsmod | grep vboxdrv > /dev/null
do
   sleep 1
done

# carry on from here ...

```

---

### Post by shadowlmd on 2011-04-22
Yes, it's loading few seconds after the cron job is launched:

Apr 22 22:56:38 shadow-server CRON[796]: (shadow) CMD (/home/shadowlmd/vmctl.sh start loshadka)
Apr 22 22:56:39 shadow-server kernel: [    9.369110] vboxdrv: Successfully loaded version 3.2.8_OSE (interface 0x00140001).

I was thinking about inserting something like that, but is it really normal that cron jobs are starting before kernel is ready? It looks like a bug to me.

---

### Post by DaithiF on 2011-04-23
Hi,
cron doesn't have any sophisticated mechanism for determining when a reboot is occurring / or has completed.  As far it is concerned, a reboot has occurred when the cron daemon has been started, and a marker file in /var/run does not exist ... (this file is then created by cron so that if/when the cron daemon is restarted before the next reboot it won't run the @reboot jobs again.

so the dependency question moves up a level, to the processes which start the cron daemon and which load the kernel modules.  The cron daemon gets started by upstart, as specified in the /etc/init/cron.conf file.  I'm not sure how you are loading the vboxdrv module, possibly via an entry in /etc/modules ?  If so, the loading of these modules is controlled by another upstart job, /etc/init/module-init-tools.conf.

so you probably want to add an upstart dependency to the cron job to tell it to wait until the module load job has completed.  I'm not familiar enough with upstart yet to tell you how to do this, but see here: [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/) and you'll probably figure it out.

---

### Post by shadowlmd on 2011-04-23
This looks too complex.. I don't wanna mess with system like this. I just installed virtualbox-ose package and it installed kernel module. It was just weird to see that system is trying to start some jobs while not all kernel modules are loaded, but if it's normal situation in linux or ubuntu, I will live with it.

---

