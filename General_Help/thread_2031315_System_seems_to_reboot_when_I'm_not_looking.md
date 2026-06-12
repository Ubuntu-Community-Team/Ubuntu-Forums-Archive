---
title: "System seems to reboot when I'm not looking"
date: 2012-07-21
forum: General Help
---

### Post by OxentroT on 2012-07-21
Hello, 

         I have seemed to notice some strange things happening lately. I on occasion like to allow some processes to run for days at a time, however, the last couple days I have awaken to my system awaiting authentication. this is strange because I have it to where the system does not lock after going to sleep. The only reason I can think of is that the sys had been rebooted. This has occurred a few times already. Three times after waking up from a nap and twice after coming home from a walk.  

So I had decided to take a look at the system logs. I looked for the most recent messages in /var/log/boot.log but this is what I was shown. 

```
**There was nothing to log yet!**
```

Strange, so I decided to take a look at /var/log/messages.log and I looked for the latest set of messages. and aha
```
Jul 21 15:35:16 Novos kernel: [   39.119747] cfg80211: Regulatory domain: 98
Jul 21 15:35:16 Novos kernel: [   39.119749] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 21 15:35:16 Novos kernel: [   39.119752] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jul 21 15:35:16 Novos kernel: [   39.119769] cfg80211: Current regulatory domain updated by AP to: US
Jul 21 15:35:16 Novos kernel: [   39.119771] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 21 15:35:16 Novos kernel: [   39.119775] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jul 21 16:36:40 Novos bonobo-activation-server (band0r-1468): could not associate with desktop session: Failed to connect to socket /tmp/dbus-opj7qRC3OR: Connection refused
Jul 21 18:02:25 Novos pulseaudio[1594]: pid.c: Stale PID file, overwriting.
Jul 21 18:03:58 Novos pulseaudio[1594]: ratelimit.c: 2 events suppressed
```
I grabbed a snippet from the bottom of the log, here is the part that I am concerned with.
```
Jul 21 16:36:40 Novos bonobo-activation-server (band0r-1468): could not associate with desktop session: Failed to connect to socket /tmp/dbus-opj7qRC3OR: Connection refused

```

Now I think I may have found what may be causing these mysterious restarts. Could there be some error that has caused the desktop session to be disassociated from? I noted how things seemingly went normal until 16:36:40. I had left my workstation at around 15:35 to go read. I had ended up k0nking out for about 45 mins until I awoke around 18:00. I got up and got some of my favourite snapple and went over to my workstation to poke at it and check some progress. BAM! I was prompted for Auth again! So I had logged in and here we are. I am asking this question because I could not find an answer.

I had also noticed these same session disassociations around the times they have occurred through the past couple of days. I can post them ALL if you'd like. 

Any ideas?

---

