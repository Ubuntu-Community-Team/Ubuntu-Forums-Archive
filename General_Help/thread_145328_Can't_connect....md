---
title: "Can't connect..."
date: 2006-03-16
forum: General Help
---

### Post by 14.1 on 2006-03-16
Hello everyone 1st time linux user here, I just installed 5.10 on an old TP 600E. and I have run into a couple of problems hope you can help  me out here.
Before I installed I did a little reading on this forums looking for any problems I may encounter during and after install, mostly setting up a wireless card.
  It seem do-able so I took the plunge everything seems to be working well except the sound and of course connecting to the Internet. I'm using a DWL-G650 card (B3 rev 2.54)  and a linksys WRT54G router. After installed I found that the card was detected so I preceded to connect to the router. I had setup the IP and WEP key and enabled the connection... however when I use the browser or even try to ping a server the only response i get is this alert " [www.cnn.com](www.cnn.com) could not be found. please check the name and try again" 

When i click on "connection properties" I see the status line jump back and forth from "sending to idle"
It shows "activity" received and sent packets and a strong signal strength, but still no web page. :(

when i run "ifconfig" i get....

anth0   Link encap:Ethernet HWadder 00:11:95:50:e3:c3
           inet addr:192.168.1.9 Bcast:192.168.1.255 Mask:255.255.255.0
           inet6 addr: fe80::211:95ff:fe50:e3c3/64 scope:link
           UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
           RX packets:254 errors:215064  dropped:0 overruns:0 frame:215064
           TX  packets:1814 errors :0 dropped:0 overruns:0 carriers:0
           collisions:0 txqueuelen:200
           RX bytes:41053 (40.0kib)
           Interupt:11 Memory:d2aa0000-d2a0000

lo         Link encap:local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:host
           UP BROADCAST RUNNING MULTICAST  MTU:16436 Metric:1
           RX packets:55894 errors :0 dropped:0 overruns:0 frames:0
           TX packets:55894 errors :0 dropped:0 overruns:0 carriers:0
            RX bytes:4837542 (4.6 Mib)  TX bytes:4837542 (4.6MiB)

I'm not sure if any of that info will  help you help me :) but if it does thanks in advance. 

I'll deal with the sound issues when or if I ever get the network up and running.

---

### Post by 14.1 on 2006-03-16
Bump...

---

### Post by 14.1 on 2006-03-16
Bumped again...

---

### Post by dpaint4 on 2006-03-16
Are you running from the LiveCD or the installed version? I know you said you 'took the plunge' but I'm not sure exactly what that means to you, and here's why I ask:

When I was running from the LiveCD I had spotty Wi-Fi and had to manually configure everything before it came up. 

But I, too, took the plunge and installed Ubuntu 5.10 as the exclusive OS to my hard drive and when it was installing it sensed my Wi-Fi Network, asked me for the netword name, and the WEP Key. I typed them in and by the time the desktop hit the screen I was already online.

Here are some other simple things to check (this is the sort of thing that can make you really mad because they sound stupid, but I'm not saying that at all. I miss these kinds of things all the time) : 

When it asked you for the network name durring setup, did you type the actual name of the network, or did you type some email address or username that you're used to typing? When you typed the network name, did you do it with proper capitalization?

Same for your WEP Key?

If it never asked you for those things I'd say that meant it never saw the network, and you'll have to dig with a bigger shovell than I can give you. I'm only 2 weeks into this myself.

If nothing else, my reply serves to bump you again, and maybe it'll be so wrong that it'll enrage someone smart and they'll help you.

---

### Post by jogege on 2006-03-17
Try passing "acpi=off pnpbios=off" to the kernel when booting. FWIW, seems there are some issues in this particular laptop that doesnt allow wireless cards to be activated unless you do this.

Had to do that for two different wireless cards on this laptop. Once this is done, sweet wireless.

---

### Post by 14.1 on 2006-03-20
[QUOTE=dpaint4]Are you running from the LiveCD or the installed version? I know you said you 'took the plunge' but I'm not sure exactly what that means to you, and here's why I ask:

When I was running from the LiveCD I had spotty Wi-Fi and had to manually configure everything before it came up. 

But I, too, took the plunge and installed Ubuntu 5.10 as the exclusive OS to my hard drive and when it was installing it sensed my Wi-Fi Network, asked me for the netword name, and the WEP Key. I typed them in and by the time the desktop hit the screen I was already online.

Here are some other simple things to check (this is the sort of thing that can make you really mad because they sound stupid, but I'm not saying that at all. I miss these kinds of things all the time) : 

When it asked you for the network name durring setup, did you type the actual name of the network, or did you type some email address or username that you're used to typing? When you typed the network name, did you do it with proper capitalization?

Same for your WEP Key?

If it never asked you for those things I'd say that meant it never saw the network, and you'll have to dig with a bigger shovell than I can give you. I'm only 2 weeks into this myself.

If nothing else, my reply serves to bump you again, and maybe it'll be so wrong that it'll enrage someone smart and they'll help you.[/QUOTE]


Ya thanks for the Bump.:) 

I been away for the weekend and so far i ahve not been able to get on-line.
  I still have the same problems, all your suggestions.. no go.
It does find the Network but no web access.
I will keep pouring through the old threads and see what i can come up with.... I like doing some detective work  but man this is a real pain in the Arse! Hope someone out there can help get me through this.

---

### Post by 14.1 on 2006-03-20
[QUOTE=jogege]Try passing "acpi=off pnpbios=off" to the kernel when booting. FWIW, seems there are some issues in this particular laptop that doesnt allow wireless cards to be activated unless you do this.

Had to do that for two different wireless cards on this laptop. Once this is done, sweet wireless.[/QUOTE]


I added these line before i Installed 5.10, I will try this again thanks.

---

### Post by Jason_25 on 2006-03-20
iwconfig is your friend.  The problem is most likely with your wep key being set incorrectly.
```

sudo iwconfig

```
Will list your wireless stats and wep key, and...
```

iwconfig youradaptername key yourwepkey

```
Should properly set your key.

---

### Post by 14.1 on 2006-03-20
Jason25  thanks I have tried but I get this error message...

 " Error for wireless request  "set encode" (8B2A) : SET failed on  device ath0 ; Operation  not permitted. "  any ideas sir?  :)

---

### Post by Jason_25 on 2006-03-20
Stick sudo in front of that.  My mistake.

---

### Post by 14.1 on 2006-03-20
Many many thanks to you, that did the trick.  :)

Now to tackle the sound issues...  hopefully that wont be to deficult.

---

