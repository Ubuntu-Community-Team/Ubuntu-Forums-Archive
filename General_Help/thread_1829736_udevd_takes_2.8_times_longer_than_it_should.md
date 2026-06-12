---
title: "udevd takes 2.8 times longer than it should"
date: 2011-08-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-08-20
Running 10.04.3 on my rig specs in signature
this happened after i tried oracle virtulabox 4 trying to get unity in it
before i installed it udevd took about 2-2.5 seconds now it takes 7 seconds (it takes less than 1 second in my virtualbox)
i still could not get unity in it i reverted back to my 3.1.6 virtualbox and udevd is still slow 
BEFORE:[INDENT][[IMG]http://i55.tinypic.com/vxyqn8.png[/IMG]]("http://i.imgur.com/gHM6Z.png")
[/INDENT]AFTER:[INDENT][[IMG]http://i54.tinypic.com/6h6zp4.png[/IMG]]("http://i.imgur.com/ySVIv.png")
[/INDENT]i have removed all the junk i could find left over from virtualbox 4[INDENT] /etc/rc{0..6}.d/{K20vboxballoonctrl-service,K20vboxdrv,K20vboxweb-service,S20vboxdrv}
/var/lib/update-rc.d/{vboxdrv,vboxweb-service,vboxballoonctrl-********* *-> boards are apparently not letting the post that right*
[/INDENT]from what i have been able to find out about udev it it does stuff with kernel events
is there a way i can clean up udev/few what it is doing and remove what ever junk got in it it appears to be timing out IMO 
i have been looking for a solution for over 24 hours at this point 
if i have to replace udev with a manual version so be it as long as i have a app that can generate it

for the record my virtual 10.04.3 boots faster then my main install on a ssd as a result of this and that is just sad a install can boot faster on a 80 Mbps than a 240Mbps drive i should be able to boot to the login in about 5 seconds after post
i know 5 seconds is not much time but percentage wise it is about 50% of my boot time

also anyone know how the system keeps track of how many times a file system has been mounted

---

### Post by pqwoerituytrueiwoq on 2011-08-22
[img]http://t2.gstatic.com/images?q=tbn:ANd9GcQTFMcBRCq0mXPLoC0Iz5YfTRlYSVj_MwXB0sKi303cw36x4c9D[/img]

---

### Post by pqwoerituytrueiwoq on 2011-08-23
...

---

### Post by pqwoerituytrueiwoq on 2011-08-24
looks like i will be bumping this as long as i keep this install :(

---

### Post by Slim Odds on 2011-08-24
If someone has some information, they will reply.

Otherwise your bumping is just plain annoying.

---

### Post by pqwoerituytrueiwoq on 2011-08-24
OMFG i found the issue :D
credit:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/498485](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/498485)
This file needs to have the UUID of swap in it 
/etc/initramfs-tools/conf.d/resume
[FONT=Courier New]RESUME=UUID=047fac32-955c-4318-b70c-479c433a24a8[/FONT]

Why have i never seen this file mentioned when people are repartitioning there HDD and told to update there fstab file when they make a new swap partition?
wonder if anyone other than me would have going this crazy over 5 seconds :lolflag:

---

