---
title: "Bluetooth is disabled and won't re-enable"
date: 2010-08-04
forum: General Help
---

### Post by cj13579 on 2010-08-04
So I have been trying to connect my Wiimote up to my PC using the following HOWTO: [https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD)

I had it working last week and for some reason it has now stopped working. I am using a USB Bluetooth dongle and I am sure that it is still working because I can connect the Wiimote up to my laptop no problem.

What I have noticed is that on my Laptop the bluetooth icon is highlighted and on my PC although the Icon is there it is greyed out. When I go to preferences and click on turn on Bluetooth the button greys out for a while and then comes back saying "Turn Bluetooth on" again.

Any help with this would be greatly appreciated.

---

### Post by cj13579 on 2010-08-05
bump!

---

### Post by cj13579 on 2010-08-05
bump!

---

### Post by varunendra on 2010-08-05
Sorry for unsolicited advice, but bumping before 24 hours actually causes harm to your thread. In my search result, your thread looked as if it already got 2 answers.

Now about your problem. Open terminal (Applications>Accessories>Terminal), enter and post output of :
```
ifconfig -a
```

I've very limited knowledge about bluetooth settings but I'll try to help as much as I can.
Let's hope some right person picks up your thread. :)

---

### Post by fragos on 2010-08-05
I've seen that same symptom. In my case removing and reinserting the Bluetooth dongle gave a better connection which was instantly recognized.

---

### Post by cj13579 on 2010-08-06
> **varunendra said:**
> Sorry for unsolicited advice, but bumping before 24 hours actually causes harm to your thread. In my search result, your thread looked as if it already got 2 answers.

Now about your problem. Open terminal (Applications>Accessories>Terminal), enter and post output of :
```
ifconfig -a
```

I've very limited knowledge about bluetooth settings but I'll try to help as much as I can.
Let's hope some right person picks up your thread. :)

Apoligies about the bumps!

The results of ifconfig. Doesn't look like any bluetooth things are recognised:

```
chris@chris:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:fb:87:8c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fefb:878c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6324487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7506221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3534825384 (3.5 GB)  TX bytes:1747840834 (1.7 GB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44124443 (44.1 MB)  TX bytes:44124443 (44.1 MB)

```

---

### Post by cj13579 on 2010-08-06
> **fragos said:**
> I've seen that same symptom. In my case removing and reinserting the Bluetooth dongle gave a better connection which was instantly recognized.

Thanks for the reply, I have tried doing this a number of times but alas to no avail!

---

### Post by varunendra on 2010-08-06
> **cj13579 said:**
> Apoligies about the bumps!

The results of ifconfig. Doesn't look like any bluetooth things are recognised:

```
chris@chris:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:fb:87:8c  ..................
..................
..................

```

It should be with **-a** parameter. Entering 'ifconfig' alone will display only active interfaces, while using '-a' option will display all the detected ones - regardless of whether they are active or not.

---

### Post by cj13579 on 2010-08-06
Whoops! It's Friday (if that's an excuse)!

```
eth0      Link encap:Ethernet  HWaddr 00:13:d4:fb:87:8c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fefb:878c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6327670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7509624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3535262456 (3.5 GB)  TX bytes:1749438644 (1.7 GB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45631661 (45.6 MB)  TX bytes:45631661 (45.6 MB)

pan0      Link encap:Ethernet  HWaddr 6e:b2:61:69:3a:a1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Thnaks for the help :D

---

### Post by varunendra on 2010-08-06
Since I don't have a precise idea about what to do next nor do I have access to any laptop or PC with a bluetooth interface here (to do experiments before suggesting), could you please run a live session (I assume bt works in it) from a live cd and post the output of the same command from there while the bluetooth is working?

Generally one has to use ifconfig command with 'up' parameter to activate an interface, and once I had to disable the wlan0 interface (using 'down' parameter) to successfully 'up' the eth0 interface. But I can't say if the same logic should go with bluetooth.

So the best option in my (immature) opinion would be to collect the info while bt is active, & then try to change the current situation to that status.

For now, you may try:
```
sudo ifconfig pan0 up
```
If it doesn't work (which I'm already afraid of), you may try **sudo ifconfig eth0 down** first, then the above command. *Note that the 'down' parameter will disable the ethernet interface until next reboot or until re-enabling it with 'up' parameter.*

The info from ifconfig -a while bt is active (in the live session) should be helpful. In the meanwhile I'll try to recall commands to gather more relevant info.

---

### Post by fragos on 2010-08-06
Connecting Bluetooth has an extra configuration dimension "visibility". On Ubuntu, click the Bluetooth icon and insure Visible is checked. Visibility must be established to pair a new device. Once paired visibility  isn't necessary to connect. How visibility is handled in the devices you connect to varies by device. Phones for example limit how long visibility stay on. You must complete pairing within that window of time.

---

### Post by varunendra on 2010-08-06
> **fragos said:**
> Connecting Bluetooth has an extra configuration dimension "visibility". On Ubuntu, click the Bluetooth icon and insure Visible is checked. Visibility must be established to pair a new device. Once paired visibility  isn't necessary to connect. How visibility is handled in the devices you connect to varies by device. Phones for example limit how long visibility stay on. You must complete pairing within that window of time.

Yes, that's a necessary part of bluetooth connectivity. But I don't think it should be a problem for him since he has done it before. Besides, the grayed-out thing he mentioned earlier makes me believe that his bt adapter isn't active at all- not even powered on!

However, cross-checking doesn't hurt. :)



[B]_EDIT_:
[/B]@ Fragos,
How about reinstalling updated (or downgraded) [BlueZ]("http://www.bluez.org/")? You seem to have experience with it ([an old thread]("http://ubuntuforums.org/showthread.php?p=8014006#post8014006")).


@cj13579,

Official page for [BlueZ]("http://www.bluez.org/")
The Ubuntu [official guide]("https://help.ubuntu.com/community/BluetoothSetup").
Another similar [thread]("http://ubuntuforums.org/showthread.php?t=1464302") with possible solutions.

---

### Post by cj13579 on 2010-08-12
> **varunendra said:**
> 

For now, you may try:
```
sudo ifconfig pan0 up
```
If it doesn't work (which I'm already afraid of), you may try **sudo ifconfig eth0 down** first, then the above command. *Note that the 'down' parameter will disable the ethernet interface until next reboot or until re-enabling it with 'up' parameter.*

The info from ifconfig -a while bt is active (in the live session) should be helpful. In the meanwhile I'll try to recall commands to gather more relevant info.

Hi all, sorry for slow replies, I really appreciate the help. I tried the pan0 up (doing it with both eth0 up and down) and it remains greyed out.

@fragos Bluetooth is set to visible.

---

### Post by cj13579 on 2010-08-12
@varunendra Thanks for the link to thread. I will try reinstalling the bluetooth packages.

---

### Post by Geremia on 2011-05-26
Run:```
hciconfig
```Note the interface name, and run:```
sudo hciconfig hci0 up
```, where hci0 is the name of the Bluetooth interface returned from your hciconfig command. It worked for me!

---

### Post by JamesSmith on 2011-06-06
This is happening to me now having just upgraded from Jaunty to Natty, bit annoying having to enable bluetooth manually on every reboot. Also, if I unplug the blutooth dongle at any point and plug it back in, it won't enable at all. 

Any tips on fixing this behaviour? Cheers

---

### Post by fragos on 2011-06-06
My TRENDnet Bluetooth dongle starts every time with the Bluetooth Manager included in "Startup Applications".

---

### Post by JamesSmith on 2011-06-10
> **fragos said:**
> My TRENDnet Bluetooth dongle starts every time with the Bluetooth Manager included in "Startup Applications".

Hmm.  I have both the standard Bluetooth applet AND Bluetooth Manager running (interestingly, Blueman won't dock into the tray, I have to start it from the launcher to use it), but the bluetooth service is still won't switch on using the GUI controls.

If it's down when I boot, I need to do

```
sudo hciconfig hci0 down

sudo hciconfig hci0 up
```

in order to get it to enable. Just 'hci0 up' on it's own doesn't work.

If bluetooth was enabled at shut down, it will be enabled at startup (I think).

Still pretty annoying behaviour, any ideas how to put it right?

Cheers

---

### Post by fragos on 2011-06-10
I used Blueman a ways back and it was a replacement for the default Bluetooth management. Running both may cause you problems since they both think they're in control.

---

### Post by JamesSmith on 2011-06-14
I can confirm that the problem still exists with only the default Gnome Bluetooth Manager installed - still have to hciconfig hci0 down / up.

Can I add these lines to a startup script or something to get this to happen automatically?

Cheers, James

---

### Post by Boggins on 2012-10-20
Seconded. Seriously, if you haven't tried taking the dongle out and putting it back in, try it first!

---

