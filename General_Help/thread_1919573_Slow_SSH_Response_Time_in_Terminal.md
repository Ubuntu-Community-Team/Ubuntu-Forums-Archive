---
title: "Slow SSH Response Time in Terminal"
date: 2012-02-03
forum: General Help
---

### Post by outrageousgriot on 2012-02-03
Hey guys.  Any help would be appreciated.  I don't seem to have this problem on any other box.

Right now I'm running Ubuntu 11.04 and I'm having issues with the SSH connection with the few SSH connections I make.  I'm thinking it's SSH in general on my box.  When typing anything into the console the keyboard response time can be as slow as 30 seconds per character.  It's on/off, considering I can type a whole statement in, and then experience the slow response for the next statement or two.  

I'm using a GA-Z68X-UD3H-B3 rev 1.3 mobo if that's at all relevant.

Please and thank you.

PS:  When looking in my /etc/ssh directory I can only see a file called moduli and ssh_config.  When trying to add a suggested UseDNS no option to my config file, I get an error.  Additionally, the ssh_config.d file or whatever it's called doesn't appear to exist in that directory.  Maybe there's an other fix for this.  I can compare with Windows and Mac OS X Lion to state that I don't get SSH problems.

---

### Post by Repus on 2012-02-03
I cant tell from your post but when does it get slow? Is it slow connecting or only after you connect via ssh? 

eg. you type ssh my.awesome.machine and what happens? slow to connect? slow to login? or is it just slow on the term after you login?


Random ideas;
[list]
[*]How is the network reliability and speed on that system normally? 
[*]Could you have bad hardware on that system or your router/switch/hub/port etc?
[*]dns resolv issues?
[*]key handling issues? like constant key exchanges?
[*]fun ip6 issues?
[/list]

---

### Post by outrageousgriot on 2012-02-03
> **Repus said:**
> I cant tell from your post but when does it get slow? Is it slow connecting or only after you connect via ssh? 

eg. you type ssh my.awesome.machine and what happens? slow to connect? slow to login? or is it just slow on the term after you login?


Random ideas;
[list]
[*]How is the network reliability and speed on that system normally? 
[*]Could you have bad hardware on that system or your router/switch/hub/port etc?
[*]dns resolv issues?
[*]key handling issues? like constant key exchanges?
[*]fun ip6 issues?
[/list]

It takes a few seconds longer to login, and with that stated, when typing in something like chmod 755 file it would type in increments - like chm---------5 seconds later-----od---------20seconds----755-----1/2 of file name----10 seconds later---last letter of file name-----.  It's very strange.  Commands that take 2 seconds to type in normally take FOREVER to type.  It's no the server.  I doubt it's a hardware issue, because I did not, I do not have this problem in other OS's.

It's very strange because I do not have this problem in other OS's.  But - I want to use UBUNTU, not OTHER OS's.

---

### Post by beulahcambell on 2012-02-03
I also like and using ubuntu, but 10.04 right now. I can give you some ideas if possible. Plz let me know the machines for which you are creating ssh connection using the  internet or LAN or some other connection. It depend upon various factors.

---

### Post by outrageousgriot on 2012-02-03
This problem persists in Ubuntu 11.04 - I also rebooted my router just to see if that could be a potential fix.

---

### Post by lordievader on 2012-02-03
Is the terminal response in a tty also slow? Perhaps you can try running "top" to see if something is taking all of your cpu causing the ssh to slow down. Hopefully you can get it fixed, this sounds very annoying.

---

### Post by Khayyam on 2012-02-04
outragiousgriot ...

When you say "I do not have this problem with other OS's" you mean concurrently? A ssh connection from "other OS" at the same time doesn't show the same unresponsiveness? If the answer to that question is yes, then we can isolate it to the that specific machine/install, if no then it may not be the machine/install but some external factor.

The symptoms you describe sound exactly like TCP/IP packet loss.
 
The first thing to consider is the network link between you and the remote host. It may have absolutely nothing to do with your install or ssh, but packet loss on the underlying TCP/IP layer.

To check for packet loss install '[mtr](http://www.bitwizard.nl/mtr/)'

```
sudo apt-get install mtr-tiny
```

Once its installed you can then run the following from the command line

```
mtr <ip address or hostname>
```

Every 'hop' between you and the remote host will be shown, and "packet loss" will show you if there are bottlenecks. The greater the packet loss the worse the connection will be (as TCP/IP has to do error correction for lost packets).

If the the network connection seems fine, work up from there, check what kind of load the remote host is under (using 'top' ). If the remote server is under heavy load then the responsiveness of the ssh session will degraded.

So, try to isolate the problem better ...

HTH ...

---

### Post by outrageousgriot on 2012-02-05
> **Khayyam said:**
> outragiousgriot ...

When you say "I do not have this problem with other OS's" you mean concurrently? A ssh connection from "other OS" at the same time doesn't show the same unresponsiveness? If the answer to that question is yes, then we can isolate it to the that specific machine/install, if no then it may not be the machine/install but some external factor.

The symptoms you describe sound exactly like TCP/IP packet loss.
 
The first thing to consider is the network link between you and the remote host. It may have absolutely nothing to do with your install or ssh, but packet loss on the underlying TCP/IP layer.

To check for packet loss install '[mtr](http://www.bitwizard.nl/mtr/)'

```
sudo apt-get install mtr-tiny
```

Once its installed you can then run the following from the command line

```
mtr <ip address or hostname>
```

Every 'hop' between you and the remote host will be shown, and "packet loss" will show you if there are bottlenecks. The greater the packet loss the worse the connection will be (as TCP/IP has to do error correction for lost packets).

If the the network connection seems fine, work up from there, check what kind of load the remote host is under (using 'top' ). If the remote server is under heavy load then the responsiveness of the ssh session will degraded.

So, try to isolate the problem better ...

HTH ...

Thank you very much for your detailed response.  Learn something new everyday.  To make sure I made myself clear, I'll state again that I have a computer running 3 different operating systems on 3 different partitions.

It appears that the problem may have temporarily disappeared, or editing the files I mentioned before and restarting my router at home might have done something, but it didn't appear to have fixed anything at first.  

I'll post back here if any further problems persist.

---

### Post by Khayyam on 2012-02-05
outragiousgriot .. you welcome

As the problem disapeared we can assume its not your Ubuntu install.

The 'useDNS no' option is only for sshd (the ssh daemon used for connections **to** the machine) and has no effect on the client (ssh connections **from** the machine). So, setting this had nothing to do with it now working. Probably restarting the router was enough to cause the problem to go away.

best ...

---

