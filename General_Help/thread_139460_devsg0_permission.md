---
title: "/dev/sg0 permission"
date: 2006-03-04
forum: General Help
---

### Post by yopnono on 2006-03-04
Hi. I have had some problems burning cd's because the permission on "/dev/sg0" is set to group "root", so the burning program could not get access to it.

Have search high and low on this issue, and I could not make the permission group "cdrom" stick. I could only burn a cd after i change the permission on ths sg0, but on next upstart, is was back to root.

So I tried to add this string "chown root:cdrom /dev/sg0"
in the startup script  "/etc/init.d/bootmisc.sh"

And now the group is set to "cdrom" at startup for sg0.
But really, this can't be right way to do?

---

### Post by RagingOcelot on 2006-04-26
I'm having trouble getting sg0 to stick for me too.  Anyone else with the same issue?

---

### Post by lg3 on 2006-05-02
Me toooooo. Is there a "How to" on setting up DVD/CD drives. I have checked the New User Guide and followed but my machine still likes to be difficult.

---

### Post by kb2wdi on 2006-06-04
I had this issue in NeroLinux and cdrecord as well. First I added the line;

KERNEL=="sg0",                GROUP="cdrom"

to "/etc/udev/rules.d/40-permissions.rules" which fixed the permission, but caused NeroLinux to lockup. The device "/dev/sg0" did not exist for me in breezy, and I do not use ide-scsi (although I do have a SCSI HD). My final solution was to just remove it. Comment out the line;

#RUN+="/sbin/modprobe -Qba sg"

in "/etc/udev/rules.d/90-modprobe.rules" and it's gone.

I am able to burn DVD's at 16x again in nero! :D

---

### Post by bootleg on 2006-07-25
I changed the "starter" for my Nero-Desktop-Icon from "/usr/bin/nero" to "gksudo /usr/bin/nero". Maybe not elegant, but it works.

---

### Post by oobe-feisty on 2007-10-23
i know this thread is old but i just installed nerolinux and had the same problem and found a few threads like this i solved  it with a work around i added this line to /etc/rc.local 

chmod 666 /dev/sg0 /dev/sg1 

it does not need to be chmod 777 read write is enough the reason why i added it to start script is cause after doing an manual chmod the permissions reset after reboot

---

