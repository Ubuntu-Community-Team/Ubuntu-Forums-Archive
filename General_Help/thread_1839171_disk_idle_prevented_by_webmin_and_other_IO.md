---
title: "disk idle prevented by webmin and other I/O"
date: 2011-09-05
forum: General Help
---

### Post by Bradburts on 2011-09-05
Hi,
I am trying to get my disks to spin down when idle.
I have managed to get hdparams.conf to work and can also configure spin down from the command line using[FONT=Courier New] sudo hdparam -S 120[/FONT]
[FONT=Courier New][FONT=Verdana]The drives spin up every hour or so. [/FONT][/FONT]
[FONT=Courier New][FONT=Verdana]Q) Is there a command which shows total accumulated I/O such that I can leave the system running and then find who has written? Something like top but showing accumulated I/O rather than snapshot.[/FONT][/FONT]
 
[FONT=Courier New][FONT=Verdana]The second problem is that I have now installed webmin (yes I know that I shouldn't & there may be issues!) and samba. Since that install the hard drives will not spin down.[/FONT][/FONT]
Using iotop I find that that webmin updates [FONT=Courier New][SIZE=2]/etc/webmin/miniserv.conf [/SIZE][/FONT][FONT=Courier New][FONT=Verdana]every 20 seconds or so. I also see updates from [FONT=Courier New][SIZE=2]jbd2/dm-0-8[/SIZE][/FONT][/FONT][/FONT][FONT=Courier New][FONT=Verdana]. [/FONT][/FONT]
 
[FONT=Courier New][FONT=Verdana]I have tried to mount root with noatime guessing that webmin periodically reloads configuration and that without noatime I would also get a disk write from the access time update. However changed root to noatime and the writes still happen.[/FONT][/FONT]
Q) Can I configure webmin to stop doing whatever its doing to the configuration (or reduce the rate)?
Could I move the configuration file to a RAM disk on startup? I would then need a way of saving the file when the contents of the file really do change. I imagine I could do that with a cron task.
 
I don't think that the samba file needs to be persisted between boots. That so I could simply move the samba file to a RAM disk but again would appreciate some help there. 
Finally what is the [FONT=Courier New][SIZE=2]jbd2/dm-0-8[/SIZE][/FONT] process doing?

---

