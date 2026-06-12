---
title: "VNC over SSH?"
date: 2009-09-20
forum: General Help
---

### Post by PerfectReign on 2009-09-20
I did google this and found a bunch of answers, but not exactly what I was looking for.


I often connect to my home network from work over ssh. I just finished up figuring how to proxy Firefox to my home net from work: [http://ubuntuforums.org/showthread.php?t=1268468](http://ubuntuforums.org/showthread.php?t=1268468)

Now, I want to get to my wife's Vista deskop when needed to help her out. I generally use KRDP to connect and her machine is at 192.168.0.104 on the network:  [http://www.perfectreign.com/stuff/2009/20090920_vnc_lilly.jpg](http://www.perfectreign.com/stuff/2009/20090920_vnc_lilly.jpg)

How would I use KRDP to tunnel through the ssh connection to get to her desktop. (This will be the same quesiton for me to get to my son's laptop, which runs Ubuntu 9.04 like mine does.)

---

### Post by The Cog on 2009-09-20
I guess the ssh command would look something like this:
```
ssh -L 127.0.0.1:5900:192.168.0.104:5900 home
```
then just vnc to 127.0.0.1.

---

### Post by PerfectReign on 2009-09-20
Hmm - okay. I'll try that.

Now for the $64,000 question - Since the machine on which the SSL is located is 192.168.0.103 and the machine on which I want to run VNC is .104, is that an issue?

I have SSLD running on the .103 machine and my router is set to forward port 22 requests over to .103.

---

### Post by HiFlyA02 on 2009-09-21
It should not be an issue however for the easiest (and best cross-platform) setup you could try [FreeNX ]("http://freenx.berlios.de/")(installation docs [here]("https://help.ubuntu.com/community/FreeNX")).  It basically does everything that you are trying to do except in a more structured environment.

---

### Post by PerfectReign on 2009-09-21
Okay, The Cog nailed it.  I can remote in no problem.

I have the command

[FONT=Courier New][COLOR=Blue]kai@r2d2:~$ ssh -L 127.0.0.1:5900:192.168.0.104:5900 daniel@256.25.45.1[/COLOR][/FONT]

That gets me in and able to launch KRDC locally, from which I just VNC into 127.0.0.1

[IMG]http://www.perfectreign.com/stuff/2009/20090921_remote_vnc_1024.jpg[/IMG]

---

