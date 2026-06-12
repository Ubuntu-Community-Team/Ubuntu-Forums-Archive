---
title: "Script"
date: 2011-06-19
forum: General Help
---

### Post by koperry on 2011-06-19
I've been searching for this and hope there is a fairly simple fix. I have a pc that resides in a small bldg. at the base of a radio tower in Central America. It receives a stream from the main studio, it then broadcasts through our tower via the stream, on occasion it will lose the stream (foul weather, etc.) Often times it will fail to reconnect, I have used various players, VLC, rhythmbox, mplayer. 

Is it possible to have a cron script that will check the stream, if all is true, then carry on and if false, reconnect to the stream? If so any pointers or directions?

Thanks in advance

---

### Post by jal on 2011-06-19
> **koperry said:**
> 
Is it possible to have a cron script that will check the stream, if all is true, then carry on and if false, reconnect to the stream? If so any pointers or directions?

Thanks in advance

Just for clarity, the issue isn't with cron, it is rather how to determine that the feed has failed.

cron is simply a way of executing jobs at specified intervals.

For instance, if you had a bash script able check the health of the 'stream' then cron could be configured to run that script at specified intervals.

I'm guessing (wildly, based on your weather reference) that the feed is via a wireless tcp/ip connection. netstat is a way of examining network connection status; it might pay to run this at regular intervals to see if you are able to find a useful diagnostic. Given that, then a script could be created to re-start applications.

---

### Post by koperry on 2011-06-20
Thanks for the quick response. It is a wireless link between the main studio and the remote tower. I have the machine set to auto login on boot and automatically connect to the stream, example % vlc [http://192.168.2.40:8000](http://192.168.2.40:8000), this is in the event the power goes off and the UPS eventually powers down., typically the UPS stays on long enough if there is a power outage. I do have someone to go and physically start the machine if need be but they are not always close. 
This tower is in the rainforest near the Golfo Dulce off the Pacific Ocean.

During the afternoons typically there will be storms, and the stream becomes choppy, stopping and starting and eventually drops long enough that the player gives up. I can remote login and see the player is idle, or in continual buffer mode, I can clear the problem by clicking the stop button and then clicking play, it buffers up and resumes play until the next storm which happens quite often in Costa Rica. 

I don't have a lot of experience with scripts, have ran netstat -s and can see quite a few drops, failed restarts and give-ups. 

I do feel your netstat suggestion combined with cron would be a good solution, any tips, tricks or pointers?

---

### Post by smurphy_it on 2011-06-20
you could edit the /etc/services file and add an entry for 8000, giving it a Unique name.  Then with your script have it do a netstat -an | grep "unique_name"

If the $? -ne 0, then you know the port is down, and within your if statement force the daemon to restart.

---

### Post by koperry on 2011-06-21
Thanks! I can run in a terminal $mplayer [http://192.168.2.40:8000](http://192.168.2.40:8000), it will connect and stream. The problem I have is not enough script knowledge, I know if your pipe command and the above were added to a script for cron to run every few minutes it would solve the problem. The pc is used for nothing other than streaming.

---

