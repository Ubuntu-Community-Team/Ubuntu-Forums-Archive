---
title: "automated server project - some questions"
date: 2006-02-21
forum: General Help
---

### Post by Chris Tucker on 2006-02-21
ok well ive been working on a project for the local school. heres the details:
old principal used cheated trial version windows software (setting date back) to play a bell sound over the PA for the classes. recently that systems clock chip (NOT battery) died, so i went and scrounged together a 233mhz system to replace it from their spare parts. installed ubuntu 5.10 and used cron to run the bell with mpg123. so far its working fine and dandy. but theres improvements yet to be made.

i dont have time to post all my questions right now, but just this one. 
what is the command for the system to update its time with NTP? i intend to use this so even if the chip or battery fails, it wont cause problems untill its severely bad. i need to have cron run this command.

---

### Post by KnottyMan on 2006-02-21
/etc/init.d/ntpdate restart

---

### Post by christhemonkey on 2006-02-21
dont forget to use root!
```
sudo /etc/init.d/ntpdate restart 
```
(sorry to point out the obvious!)

---

### Post by Chris Tucker on 2006-02-22
[QUOTE=christhemonkey]dont forget to use root!
```
sudo /etc/init.d/ntpdate restart 
```
(sorry to point out the obvious!)[/QUOTE]
it'll be running as a root cron job. so sudo isnt needed. cant exactly type a password when i want it automated :/

is restarting ntpdate the only way?

-edit- 
nvm, found it, /etc/init.d/ntpdate reload

---

### Post by nocturn on 2006-02-22
Install ntp-server to keep it synchronised automaticly.

---

### Post by Chris Tucker on 2006-02-22
is there anything to configureing ntp-server? or will it update automatically? i want it to update every 15min to help in the event of a clock chip failure. i know with the ntp-server package installed however i can have every other ntp equipped computer in the building update off of that system, so if anyone wonders what time it is, they really know what time it is.. this clock here says 6:13 am >.< its too much to manually update them all by entering in the time! so this is great, never thought of it. (its 9:45am btw)

---

### Post by nocturn on 2006-02-22
[QUOTE=Chris Tucker]is there anything to configureing ntp-server? or will it update automatically? i want it to update every 15min to help in the event of a clock chip failure. i know with the ntp-server package installed however i can have every other ntp equipped computer in the building update off of that system, so if anyone wonders what time it is, they really know what time it is.. this clock here says 6:13 am >.< its too much to manually update them all by entering in the time! so this is great, never thought of it. (its 9:45am btw)[/QUOTE]

Ntp-server just needs a list of servers to use.  It doesn't require an interval.

Do you have Gnome installed on it?  If so, setting it up is very easy.  Otherwise, just edit ntp.conf.

---

### Post by Chris Tucker on 2006-02-22
ok, thanks to everyone that helped with that, time now updates perfectly! obviously a necessity for a system that everyone in a workplace relies on to know what time it is...

my next question will proabably come tonight.. if i remember it :/ cant even remember what aspect of the system it concerned right now :O

---

### Post by Chris Tucker on 2006-02-22
well its not night, but i remembered the next question, and ended up figureing out the answer myself :X look ma! im learning! lol. i used amixer to find out the current volume level, then created a few bash scripts to set the volume to normal, and shorten the command for modifying the volume. for anyone else that should ever need this, its amixer sset 'y' xx%  where y is PCM or Master or as such, the device name. and xx is the percentage. ex for me, the good normal volume is for both devices 81%
amixer sset 'PCM' 81%
amixer sset 'Master' 81%
i found these settings are best for avoiding too much static but still letting it be good and loud...

---

### Post by Chris Tucker on 2006-04-25
Ok, next idea...  i know i can do this with shoutcast, but its not LIVE, so here it goes..

Is there a way to send audio to the server over the network, live, from a multiplatform application on the end sending the audio, and a low resource using system being running on the server, spitting the audio out in real time (tollerance of about 0.5s, the network can handel it no problem) 
I know that TeamSpeak can do EXACTLY all of that without haste, but its a gui application, and i would need the TS client on the server to be completely command line. (if you know how to do this, let me know! this would be the ideal option!)
But other than that, is there a way to do this?

---

### Post by iball on 2006-04-25
Just an alternative to using /etc/init.d/ntpdate:

If you have the "ntpdate" command installed, you can add the following line to /etc/crontab: ```
*15 *    * * *   root   ntpdate pool.ntp.org

```

This command can also be run whenever, using "sudo ntpdate pool.ntp.org"

I hope this helps
--Ian

---

