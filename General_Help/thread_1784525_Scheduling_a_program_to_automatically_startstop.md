---
title: "Scheduling a program to automatically start/stop"
date: 2011-06-17
forum: General Help
---

### Post by pzaw on 2011-06-17
hi
 
I am looking for a way to stop torrent programs automatically. In particular to stop a program nicely.

All torrent programs the I have tried are either good at dl or good at scheduling but not both in my experience. I did have luck for a week with one but I suspect my isp is filtering this particular torrent because now I cant get any connection but when I use other torrents it seem to work. Thus my query...

I have tried using schedule task. It runs the program but it does not stop it. 
However, I can kill the process.

I have Ubuntu 10.04 LTS Lucid Linux
I use scheduled task with these commands
Start:
fatrat
stop:
killall -9 fatrat

****WARNING*****
care must be taken when using kill all it could accidentally kill all essential processes!!!!
****WARNING*****

Now I don't know if it will corrupt the download or not. If one of you  experts can tell me I would appreciate it. Or if you have a better  solution I would be glad to take it on board.

This seems to start and stop fatrat ok but I have seen the following problem which may or may not be related.

With killing the process, I have been getting a lot of ISOs with empty data. ie it would report 4G  ISO but when you look at it, it is empty. I am not sure why this is. May  be because of dummy files, you do hear of these from time to time or because of the Kill command may be?

I assumed if the last packet was corrupt due to the kill command, torrent would have enough sense  to re-download that packet when the DL program is run the next time.

pzaw

---

### Post by Lars Noodén on 2011-06-17
btpd has good controls that are easily scriptable.  Then you can use cron to start or stop the torrents using btpd's own utilities.  

Probably the same goes for transmission-cli.

Either way, you'll want to use the torrent's own controls to stop the activity.  Kill -9 won't allow it to shutdown gracefully or cleanly.

---

