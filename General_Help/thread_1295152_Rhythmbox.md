---
title: "Rhythmbox"
date: 2009-10-19
forum: General Help
---

### Post by Merovius on 2009-10-19
Does anybody have a problem with Rhythmbox greying out whenever you transfer music / podcasts to an MP3 player?

My Sansa e250 is seen and identified correctly. I can put files on and take them off fine. BUT, it's always greying out and I have to wait a minute or more for it to come back around. Files seem to transfer to about 86% then it hangs (grey) for a minute then bang, it's done and back.

What gives?? :confused:

---

### Post by Merovius on 2009-10-22
So, I guess it's just me? 

I really wish I could get this behavior to stop. Tried Banshee, itunes etc. and Rhythmbox works best with my Sansa. It just has this greying out thing.

Guess I'll be getting used to it..:(

---

### Post by Shpongle on 2009-10-22
whats your system specs and whats the volume of the files your moving.


the greying out usually happens when a program becomes unresponsive , but if its happening everytime you do it then it could be a bug with the compatibility of the player or something , have you tried to do it with another make of player (mabye a friend has an ipod you could borrow?)

---

### Post by Merovius on 2009-10-23
My system is an AMD Athlon 64 3200+ with 1 Gigabyte of PC3200 ram, Geforce 7300gt with 512 mb memory. About 55 Gigabytes free on the Ubuntu partition.

I'm usually transfering about 100 mb or maybe a little more. Ram usage never goes beyond 38%.

Have not tried another player. Will have to try my wifes generic (GPX?) player and see what happens.

Rhythmbox is about the only thing that greys out. Could be my player I guess..

Thanks

---

### Post by P4man on 2009-10-23
sounds like Rhythmbox doesnt create a separate thread to handle the file transfer. Just like in the old days word 2.0 would freeze until it finished printing. Or all of windows froze while formatting a floppy :)

Compiz greys out apps that appear unresponsive. In this case, its unresponsive not because it crashed, but because its not accepting any commands while its transferring. Its more a lacking feature than a bug, I guess you can live with it.. I also guess it will be solved at some point.

---

### Post by Merovius on 2009-10-23
Thats sort of what I thought. Guess I could tell Compiz to not "grey" out. Maybe that will make it less notiable / annoying..

Like I said guess I'll be getting used to it...

Thanks for the ideas.

---

### Post by sigixv on 2009-10-23
same here. Music keeps playing & file transfer is succesful but unresponsive between each transferred track

---

### Post by x C0MMAND0 x on 2009-10-23
I wasn't a big fan of Rhythmbox actually, I would recommend Banshee.

---

### Post by blur xc on 2009-10-23
> **Merovius said:**
> Thats sort of what I thought. Guess I could tell Compiz to not "grey" out. Maybe that will make it less notiable / annoying..

Like I said guess I'll be getting used to it...

Thanks for the ideas.

refer to Ubuntu Kung Fu- there's a tip in there on how to increase the delay before compiz grays out a window that it thinks is inactive-

Here it is- tip # 176

> If you have desktop effects enabled, Ubuntu will &#8220;grey out&#8221; program
windows that it thinks have either crashed or stalled. This can be a
useful visual indication that something has gone wrong but the delay
before it happens&#8212;five seconds&#8212;is just too quick. Programs like Synaptic
have a habit of pondering their next action for slightly longer than
that, and that can cause them to &#8220;grey out&#8221;.
You can alter the time-out by editing a setting using gconf-editor. Navigate
to /apps/compiz/general/allscreens/options and change the ping_delay
key to 10000. This will change the &#8220;greying out&#8221; delay to 10 seconds
(10,000ms). For 15 seconds, change the setting to 15000.

BM


edit- I also switched to Banshee

---

### Post by Merovius on 2009-10-24
Thanks for the ping delay trick I have set it to 10000 and will see the next time I transfer files. 

tried Banshee and I don't remember why but I didn't like it for some reason. Might have been how it handled the Sansa. Might try it again after the latest release.. 

Wish I could Rockbox this thing that might help it work with players a little better. Wrong version though..

Thanks again for the tips.

---

### Post by DeMus on 2009-10-24
> **Merovius said:**
> Does anybody have a problem with Rhythmbox greying out whenever you transfer music / podcasts to an MP3 player?

My Sansa e250 is seen and identified correctly. I can put files on and take them off fine. BUT, it's always greying out and I have to wait a minute or more for it to come back around. Files seem to transfer to about 86% then it hangs (grey) for a minute then bang, it's done and back.

What gives?? :confused:

I suspect it is because your disk is very busy with moving the large blocks of data. It is not the CPU which is overloaded.
Rhytmbox does not get any new data because the disk is busy and therefore it is greying out.
I had the same when extracting a long list of rar files. Now I have installed Jaunty on 2 disks in a RAID 0 configuration which gives me double read- and write speed and those problems are gone. Now the computer still responds to what I want to do in the same time.

---

### Post by P4man on 2009-10-24
> **DeMus said:**
> I suspect it is because your disk is very busy with moving the large blocks of data. It is not the CPU which is overloaded.
Rhytmbox does not get any new data because the disk is busy and therefore it is greying out.
I had the same when extracting a long list of rar files. Now I have installed Jaunty on 2 disks in a RAID 0 configuration which gives me double read- and write speed and those problems are gone. Now the computer still responds to what I want to do in the same time.

To be clear, its *highly* unlikely an MP3 player would achieve a higher write speed than even a single harddisk can read. So RAID 0 or anything else would change nothing here. Even with an uberfast MP3 player, Rhythmbox or the system as a whole wouldnt become unresponsive if it handled I/O in a separate thread or asynchronously. That seems not to be the case however, and I suspect its a limitation of the plugin architecture.

---

### Post by Merovius on 2009-10-25
I set the ping delay in Compiz to 10000 and it was definitely an improvement I think I will go to 15000 though and try that. I don't mind the graying out but I want it to be when the program is truly "Not responding". I'm fairly patient so I don't think I'll have a problem with it not responding because I didn't let it finish what it was doing.

Thanks again.

---

