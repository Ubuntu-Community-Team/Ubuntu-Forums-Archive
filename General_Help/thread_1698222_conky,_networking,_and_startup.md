---
title: "conky, networking, and startup"
date: 2011-03-02
forum: General Help
---

### Post by knowledge_is_power on 2011-03-02
OK so after upgrading from 7.10 to 10.10 Ive gotten everything pretty much back the way I want it, but my conkyrc wont work like it used to.  My old wireless card was called wlan0 so I changed that to the new name, which is eth1, but it wont display essid or link quality or connect speed.  heres where my issue stems from:

```
d00d@Linux-Inside:~$ iwconfig eth1
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:234  Noise level:199
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

d00d@Linux-Inside:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:1c:26:31:42:3e  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe31:423e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21143 errors:0 dropped:0 overruns:0 frame:9056
          TX packets:14943 errors:15 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27104788 (27.1 MB)  TX bytes:1753094 (1.7 MB)
          Interrupt:18 

d00d@Linux-Inside:~$ sudo iwconfig eth1
eth1      IEEE 802.11bg  ESSID:"theplantershack"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:1B:55:EF   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-42 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:48  Invalid misc:0   Missed beacon:0


```

so from what ive found, other people have this problem too.  I can grab link quality, essid and rate only when I run iwconfig as root.

So, when I run conky as root, it all works great.

however, ive got a little script to wait 3 seconds after login to boot conky, because otherwise it doesnt work, so I cant make a boot script or anything. 

HOW CAN I MAKE CONKY WORK RIGHT ARG.

---

### Post by aaryansh on 2011-03-02
Hey there,
You can try changing eth1 to wlan0 instead of trying to change things in conky.

```
sudo nano /etc/iftab
```

Change eth1 to wlan0.

Hope that solves your problem.

---

### Post by knowledge_is_power on 2011-03-02
hmmm, well apparently there hasnt been a iftab table in ubuntu for a while as ifrename is no longer used :(

any other ideas?  conky works awesome if I can run it as root, so if i could just give the script su permissions, my problem would be fixed.

---

### Post by knowledge_is_power on 2011-03-02
ok heres what I did, its probably a little insecure, but whatever.
I wrote a tinyscript to start conky
```
#!/bin/bash
sleep 5;
sudo /usr/bin/conky;

```

then added that to the startup programs list.
then I edited sudoers:
```
sudo visudo

##THEN ADDED THIS LINE TO USER PRIV. SPEC.

d00d       ALL = NOPASSWD: /usr/bin/conky

```


eedit: ok I found out the sudo -K forces the timeout.  and also this still doesnt work :(  can someone tell me if i screwed up in my sudoers?
if i run sudo /usr/bin/conky it still asks for PW..

edit2: ARG ok, so i think this is the wrong approach.  On a reboot, my NIC got renamed to eth0 for whatever reason.  Is there a way to force ubuntu to make a name stick for my wlan card?  Ive looked around and everyone seems to use /etc/iftab

also, i think i DID screw up my sudoers. im gonna go read the manpage again.

---

### Post by aaryansh on 2011-03-02
you're right, 
My bad bout the iftab.
Try this

```
sudo nano /etc/udev/rules.d/70-persistent-net.rules
```

And to start the script as root, you can start it by adding it to your /etc/rc.local

---

### Post by akernan on 2011-03-23
Was this problem solved?

---

### Post by knowledge_is_power on 2011-03-24
nope. still having trouble.  I'm going to look into the rules file, but I gotta figure out the syntax. I havent really had time.  I'm willing to bet all my issues stem from the fact that my wireless card is called eth0 instead of wlan0.  It seems that this is for some reason preventing iwconfig from reading the wireless extension values unless it has su privs.
The first approach I'm going to try tomorrow (my laptop's sitting at school right now) is to add the script to rc.local and see if it works.  If not ill look into changing the name of the card, but im a little nervous its going to screw some component over when it looks for trusty old eth0 and cant find it.
Ill report back if i figure it out and mark this thread.

EDIT: ok, tried both things aaryansh suggested.  adding the following line to rc.local made nothing happen.  maybe im doing it wrong?
```
sleep 15;
/usr/bin/conky;
```

I set rc.local to execute at the end of rl5 only.
I then successfully changed eth1 to wlan1 and the problem persists:
```
d00d@Linux-Inside:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:217  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

d00d@Linux-Inside:~$ sudo iwconfig
[sudo] password for d00d: 
lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"ubc"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:F1:AC:8F:93   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-39 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```
I also checked and conky still cannot grab link quality, ESSID, connect speed or local IP unless its executed as su.
anyone got another suggestion? :(

---

### Post by akernan on 2011-03-25
I'm having the same problem.  My wireless was eth1, but with  aaryansh suggestion I was able to make it wlan0.  I can get upspeed/downspeed info but none of the wireless variables work unless conky is run as sudo.  I have conky working with other variables just want to add wireless.

If you're interested here's my [working conky]("http://ubuntuforums.org/showthread.php?t=281865&page=1655"), #16550 at the bottom of the page.

---

### Post by akernan on 2011-03-27
Sombody sent this code to me, it's not conky wireless variables but it works...

**quality.sh**
> #!/bin/bash

# Find device used for wifi.
devlist=$(cat /proc/net/wireless | tail --lines=1) 2>/dev/null
devleft=${devlist#' '*}
devright=${devlist%%':'*}
echo $devright | grep "" > /tmp/dev_pure
device=$(cat /tmp/dev_pure)

# Get Quality
iwconfig $device | grep Link > /tmp/link
quality=$(cat /tmp/link | grep "Link")
echo $quality

Add this to conkrc
> Signal: ${execi 60 ~/.Conky/quality.sh}

---

### Post by akernan on 2011-04-02
I changed the above script and created 3 separate scripts to output the link, signal, & noise for the conky exec, execgraph, & execbar variables.  It's not pretty but it's functional.

I add these lines to conkyrc, TEXT area.
> Link: ${exec .Conky/link.sh} ${execbar .Conky/link.sh}
Noise: ${exec .Conky/noise.sh} ${execgraph .Conky/noise.sh}
Signal: ${exec .Conky/signal.sh} ${execbar .Conky/signal.sh}



Here are the 3 scripts.

---

### Post by akernan on 2011-04-02
> **akernan said:**
> I changed the above script and created 3 separate scripts to output the link, signal, & noise for the conky exec, execgraph, & execbar variables.  It's not pretty but it's functional.

I add these lines to conkyrc, TEXT area.


Here are the 3 scripts.

Ok, the previous scripts had errors.  I removed the lines that made problems and got the bargraph.lua to work.  I've attached my conkyrc, the bash scipts, & the modified bargraph.lua file.  Not 100% sure of the max settings in the lua script.

---

