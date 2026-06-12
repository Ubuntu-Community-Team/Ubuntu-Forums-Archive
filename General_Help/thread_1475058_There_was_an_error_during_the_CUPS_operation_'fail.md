---
title: "There was an error during the CUPS operation: 'failed to connect to server'"
date: 2010-05-06
forum: General Help
---

### Post by crjackson on 2010-05-06
I get this error ALL THE TIME after a reboot if I try to print.  Going to the printing applet to add the printer does no good because Lucid is not connected to the CUPS server.  I found that the work-around below fixes the issue for the current session.

```
sudo aa-complain cupsd
sudo /etc/init.d/cups restart
```

I'm not sure why this works and rebooting doesn't restart it properly, but I'm getting kind of tired of it.

Is there a permanent way to fix this issue?  I've checked and found it's been a problem since AT LEAST 8.04.

Any advice would be appreciated.

Thanks

---

### Post by dvfreelancer on 2010-05-13
I'm having the same problem but it just started in 10.04.  Put CUPS in complain mode and restart clears it up, but yeah it's kind of a pain.

---

### Post by crjackson on 2010-05-13
> **dvfreelancer said:**
> I'm having the same problem but it just started in 10.04.  Put CUPS in complain mode and restart clears it up, but yeah it's kind of a pain.

I've had the problem with several version of Ubuntu, but none so bothersome as with Lucid.  Hopefully it will become more stable in the weeks to come.  I'm also having other problems with Lucid regarding video + plymouth + fsck taking 30-45 minutes.

If these bugs don't get worked out fairly soon, I'll be reverting back to Karmic (and even Intrepid Ibex on one machine possibly).

---

### Post by myk02k on 2010-05-13
+1

---

### Post by sir_nasty on 2010-05-13
I had this same issue when I was using a printer that was mapped to a mac.  The mac was setup on static ip and if it was in a sleep mode or something similar it was an issue.  However, if I mapped the same printer using only the IP address and not the name then this issue went away and I haven't had any problems since then... I don't know if that will work but it's a thought...

---

### Post by crjackson on 2010-05-13
> **sir_nasty said:**
> I had this same issue when I was using a printer that was mapped to a mac.  The mac was setup on static ip and if it was in a sleep mode or something similar it was an issue.  However, if I mapped the same printer using only the IP address and not the name then this issue went away and I haven't had any problems since then... I don't know if that will work but it's a thought...

The printer is connected via USB port not networked with the computer having the problem.

---

### Post by resthavener on 2010-05-14
Me too with a networked hp 4550 - new problem in 10.04.  

Stupid problems too with duplex printing but that's another issue.  Why I STILL dont dare recommend Ubuntu to friends and relatives.

---

### Post by crjackson on 2010-05-14
> **resthavener said:**
> Why I STILL dont dare recommend Ubuntu to friends and relatives.

I made that mistake too.  It cost me the friendship of a 30 year friend.  He was just too stupid to catch on to anything outside of windows (after 2 years!).

BACK ON TOPIC:

Have you found a solution?

---

### Post by sir_nasty on 2010-05-17
Just a thought (for those with a network setup) Try setting your computer to a static IP and set the printer to a static IP and see if it helps at all.  That's the setup I'm running and it's been just fine (except for my printer disappearing every once in a while, then I unplug the ethernet cable for a few seconds and then plug it back in....)  Just some thoughts....

---

### Post by crjackson on 2010-05-17
> **sir_nasty said:**
> Just a thought (for those with a network setup) Try setting your computer to a static IP and set the printer to a static IP and see if it helps at all.  That's the setup I'm running and it's been just fine (except for my printer disappearing every once in a while, then I unplug the ethernet cable for a few seconds and then plug it back in....)  Just some thoughts....

Thanks for the input.  I wish I could figure out how to set my printer to a static IP.  I've been trying to figure that one out for a while.

---

### Post by myk02k on 2010-05-18
same issue here

---

### Post by cafeschintze on 2010-05-23
I guess a fix for the moment would be to set cupsd in complain mode during startup until we get a real fix.

Does anyone have a clue how to do that?

---

### Post by garethfoxwilliams on 2010-06-10
can any code/script writers out there suggest a way to automate: ( in a script??) 

sudo aa-complain cupsd
sudo /etc/init.d/cups restart


Running these two commands in a terminal fixes the problem fine, but I need to be able to launch a script or something with an icon (which I know how to do ) so that the other members of my family can re-activate printing when this happens.

thanks.

---

### Post by garethfoxwilliams on 2010-06-10
update :

sudo service cups restart

..............worked a treat.

I just need to find an easy, safe graphical way to do this.

Thanks

---

### Post by rogerdean on 2010-06-24
Wow, I just upgraded my parents' computers to Lucid and am really stuck with this issue. Does anyone have any ideas how I can leave it so they'll manage?
Cheers

---

### Post by lenn-art on 2010-07-17
+1

Tnx for the workaround. I ran into the same problem after installing 10.04. Sometimes, CUPS could not be found :-(

---

### Post by Morbius1 on 2010-07-17
If the problem is that CUPS is not starting on a boot or reboot then this might be the automated workaround you're looking for:

Create a small script and add it to /etc/network/if-up.d. Any executable in if-up.d will run only after the network is up.

Create a script:
```
gksu gedit /etc/network/if-up.d/cups
```With this content:
```
#!/bin/sh
service cups restart
```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups
```Reboot

I think the new upstart process that's being used to start services in 10.04 is discombobulating a number of services and either not starting some services or more likely starting them in the wrong sequence. Just a guess on my part.

---

### Post by ibates on 2010-07-18
I'm a bit more than 30 y-o and have been doing my damndest to come to grips with Ubuntu for over two years now.

75% of the time it is wonderful; the other 25% I could throw the box with Ubuntu out of the 64th floor window, but I would probably be in trouble because it would fall on someone's head.

I have run plenty of popsts seeking support on this site, and most have not had any useful responses.  Of those serious responsess, they probably would have been great for anyone with 10 years or so experience with either Linux or Unix.

But for we "stooppid" folk, we obviously fail the prerequisites of Linux expereience to catch up, despite serious effort to do so.

If you can't explain it at the level of the enquirer, then you fail completely in the role of advisor.

---

### Post by crjackson on 2010-07-18
> **ibates said:**
> I'm a bit more than 30 y-o and have been doing my damndest to come to grips with Ubuntu for over two years now.

75% of the time it is wonderful; the other 25% I could throw the box with Ubuntu out of the 64th floor window, but I would probably be in trouble because it would fall on someone's head.

I have run plenty of popsts seeking support on this site, and most have not had any useful responses.  Of those serious responsess, they probably would have been great for anyone with 10 years or so experience with either Linux or Unix.

But for we "stooppid" folk, we obviously fail the prerequisites of Linux expereience to catch up, despite serious effort to do so.

If you can't explain it at the level of the enquirer, then you fail completely in the role of advisor.

I can tell you are very frustrated but the 25% of wanting to throw the box out the window is a bit high.  For me it's like 1% of the time.  Since I want to throw anything with MS-Win out to the curb 10% of the time I find it a good trade off.

---

### Post by geronimo12 on 2010-07-28
Morbius1 - Thank you. it works now :)

---

### Post by uglowp on 2010-10-17
I tried the following and it worked.

sudo apt-get install --reinstall cups

After the re-install I had to delete the existing printer and re-install it for everything to work.

---

### Post by venik212 on 2010-10-17
I also am unable to use CUPS in 10.10 on my 64 bit machine.  I keep getting the message: cannot connect to localhost 631.

---

### Post by uriel1998 on 2010-10-27
I tried restarting the service multiple times (and multiple ways) to no avail, but the reinstall method worked.  It turned out that I had installed XPDF, which had borked the whole thing somehow.

---

### Post by uriel1998 on 2010-10-27
It's worth noting that after the reinstall, I then had to delete and re-install the printer as well (a matter of moments).  Until I did that, I had the dreaded "CUPS: there is a missing print filter for MYPRINTERMODEL".

---

### Post by tharpa on 2011-03-06
> **uglowp said:**
> I tried the following and it worked.

sudo apt-get install --reinstall cups



Thanks, this worked for me.

---

### Post by afrodeity on 2011-06-16
> **uglowp said:**
> I tried the following and it worked.

sudo apt-get install --reinstall cups

After the re-install I had to delete the existing printer and re-install it for everything to work.

how to delete existing printer, please.

If I try to cancel a job, I get

```

There was an error during the CUPS operation: 'service-error-service-unavailable'

```

---

