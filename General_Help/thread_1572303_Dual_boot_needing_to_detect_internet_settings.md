---
title: "Dual boot needing to detect internet settings"
date: 2010-09-10
forum: General Help
---

### Post by tomasterisk on 2010-09-10
I have a problem. I have a dual boot that has 10.04 and 9.04. Long story short: The 9.04 has internet connectivity. I had no problem (this time) getting the computer to find the right setting.

The problem is that I want 10.04 to have Internet.** Is there a way for 9.04 to "tell" 10.04 what the settings are?**

I have very limited space on the 9.04 (partly because I screwed up the Gparted, which is a separate, but not as important, problem).

Thanks in advance.
Tom RIggle

---

### Post by uRock on 2010-09-10
What wireless NIC do you have, if wireless is the problem?

---

### Post by tomasterisk on 2010-09-11
I have auto Ethernet. I forget what it is called. DSL. I have a flat dish on the roof with a wire running down to my computer.

Did I get an incomplete version of Lucid when I downloaded it? Shouldn't have a connection icon in the top right corner?

---

### Post by rory526 on 2010-09-11
so there is no icon at the top in 10.04?

---

### Post by rory526 on 2010-09-11
some ideas...

If you have no icon in the corner, try refreshing the panel:

```
killall gnome-panel
```


Maybe you removed the panel icon? right click at the top, "Add to Panel", "Indicator Applet".


NetworkManager is the program responsible for the connection icon in the top corner. To see if it's running:

```
ps ajfx | grep 'NetworkManager'
```

If it shows up, it's running. You might want to try killing it and starting it again. 

If so, get the numbers in the second column from the output of the last command and put them in place of <PIDS> in the following command. Exclude the number on the line containing 'grep'.

```
sudo kill <PIDS>
```

Then start NetworkManager again:

```
sudo NetworkManager
```

---

### Post by tomasterisk on 2010-09-11
> **rory526 said:**
> some ideas...

If you have no icon in the corner, try refreshing the panel:

```
killall gnome-panel
```
Maybe you removed the panel icon? right click at the top, "Add to Panel", "Indicator Applet".


Thank you for the help. SO far, no success. In answer to your first question: I don't seem to have the network icon. I tried the killall command, so I guess I will just go down the list.

Because I have so little space on my 9.04 partition I can't even print. So I am writing these commands out.

By "indicator applet" you don't mean that small white square, do you? I tried all the icons I have up there and found nothing that seems to have an answer to my problem.

I will move on to the next commands.

---

### Post by tomasterisk on 2010-09-11
> **uRock said:**
> What wireless NIC do you have, if wireless is the problem?

Thank you, uRock. I have wired.

---

### Post by uRock on 2010-09-11
> **tomasterisk said:**
> Thank you, uRock. I have wired.
 What are the specs for your NIC(wired)?

---

### Post by tomasterisk on 2010-09-11
> **uRock said:**
> What are the specs for your NIC(wired)?

Ethernet is all I can tell you. Is there a terminal command to run to get the specs you want to know about?

---

### Post by tomasterisk on 2010-09-11
> **uRock said:**
> What are the specs for your NIC(wired)?

Ethernet is what I have. Beyond that, I am not sure what to say.

Is there a terminal command that would give you the answer?

---

### Post by tomasterisk on 2010-09-11
> **rory526 said:**
> some ideas...

If you have no icon in the corner, try refreshing the panel:

```
killall gnome-panel
```Maybe you removed the panel icon? right click at the top, "Add to Panel", "Indicator Applet".


NetworkManager is the program responsible for the connection icon in the top corner. To see if it's running:

```
ps ajfx | grep 'NetworkManager'
```If it shows up, it's running. You might want to try killing it and starting it again. 

If so, get the numbers in the second column from the output of the last command and put them in place of <PIDS> in the following command. Exclude the number on the line containing 'grep'.

```
sudo kill <PIDS>
```Then start NetworkManager again:

```
sudo NetworkManager
```

OK, I did all these and was told "Warning" and that NetworkManager was already running.

There were two lines of info and with numbers. I took the number that was on the next to last line, 2nd column.

---

### Post by uRock on 2010-09-11
Is network manager listed in your System Administration menu?

---

### Post by tomasterisk on 2010-09-11
> **uRock said:**
> Is network manager listed in your System Administration menu?

Network Tools is listed there. Network Connections is in Preferences.

I wonder, if I just transfer the settings from my 9.04 Network Connections to that of 10.04, would that do the trick? Referring just to the first window: Devices.

---

### Post by tomasterisk on 2010-09-11
> **tomasterisk said:**
> Network Tools is listed there. Network Connections is in Preferences.

I wonder, if I just transfer the settings from my 9.04 Network Connections to that of 10.04, would that do the trick? Referring just to the first window: Devices.

I've noticed something in my Network Connection that looks strange, at least to me. It shows me receiving packets

The second column has this:
Interface Statistics
Transmitted bytes 108.4 KiB
Transmitted Packets 730
...
Received Bytes 108.4 KiB
Received Packets 730


Is this normal if I can't get online? 
Where are the packets being received *from*?
Is it possible that *this* is what is keeping me from being online? I noticed that the packets in the 9.04 were just 4.

Anyone?

---

### Post by tomasterisk on 2010-09-12
I "solved" my problem by just making it go away. I loaded 9.04 on a fairly large unapportioned section of my drive. It works fine, except for having to load 200+ updates!

I just don't have the time and inclination and monkey around in a problem that apparently is hard to solve. Perhaps - at least when it comes to connectivity - Lucid is not quite ready for prime time.

---

