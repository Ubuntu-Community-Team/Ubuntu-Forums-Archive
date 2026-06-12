---
title: "virtualbox/vmware owns my LAN connection?"
date: 2012-01-19
forum: General Help
---

### Post by Ms. Daisy on 2012-01-19
Earlier today I installed VMWare Player. I was planning on installing a few VMs to test on.  So I opened my first VM and chose to keep it confined to the local LAN- I didn't want it to connect to the internet. During the installation of the guest OS, it hung and I had to force quit. So that guest machine was completely lost.

Fast forward to right now. I restarted the host computer and now I can't connect to the internet at all. I'm stuck in loopback in (host) Ubuntu. I opened devices-network tools and changed my network device to wifi, but it won't stay persistent. It keeps reverting to loopback interface whenever I close network tools. The most confounding thing is that I'm stuck in loopback on the Windows 7 partition, too (It's a dual boot computer). Windows network and sharing center tells me that my connection is "virtualbox box only network".  But how could Virtual Box break my network connection on the host?  Doesn't it only control the guest? Google has only yielded me information about networking a guest.



I completely uninstalled VMware Player. Still stuck in loopback.  I've got other computers on this LAN and all is well with them.

WHAT HAVE I DONE????  How do I undo this?


 

 Summary:
Dual boot laptop: Windows 7 and Ubuntu 11.10
 
[LIST]
[*]Virtual Box installed on Ubuntu
[*]VMWare Player was installed on Ubuntu but I removed it.
[*]Virtual Box installed on Windows
[*]Virtual Box owns my laptop???
[/LIST]

---

### Post by Dangertux on 2012-01-19
I'm going to take a wild guess and say that you bridged your network for one of the VMs right?

This happens every so often to me and I havent quite figured out why. Open the VM that you did this in set it to NAT or host only. Then close out vbox. 

Then restate your network. 

```

sudo /etc/init.d/networking restart

```

You may need to reboot for good measure. If THAT doesn't work just uninstall virtual box and reboot. 

Not sure why it's affecting windows at all that maybe a different issue or magic but let me know when you get the ubuntu network back up c

---

### Post by Ms. Daisy on 2012-01-19
All the VMs are set to NAT. I ran the command but got an error:
```
running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
*reconfiguring network interfaces...      [OK]
```No joy.
I uninstalled virtual box in both partitions.

No joy.

I found this command & ran it:
 ```
sudo ifdown eth0 && ifup eth0
```but I get an error
```
ifdown: interface eth0 not configured
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
``` Grr... why is permission denied? I'm the sudo user.

---

### Post by Dangertux on 2012-01-19
The deprecated error ignore it's just an upstart error. 

The second error is because you need to prepand sudo to both commands as such 

```

sudo ifconfig eth0 down && sudo ifconfig eth0 up

```

&& is just a shell convention that says wait until the first command is successful then executes the second

---

### Post by Ms. Daisy on 2012-01-19
Aha, thanks. I added the second sudo but I'm still stuck in loopback.  
Then it occurred to me- I don't have an ethernet cable on this bad boy, so I substituted wlan0. Got this:
```
Ignoring unknown interface wlan0=wlan0
``` 
Any other ideas?  I think I might hate virtual box.

---

### Post by Dangertux on 2012-01-19
You can't bring down an wifi interface like that. Try br0 see my PM for more details.

---

### Post by Ms. Daisy on 2012-01-19
No joy on br0 either.

I looked for the eth0.conf file in  the file system (including in /etc) & found nothing. That seems strange. I ran System Testing for  network. It found my nic but it couldn't find any way to connect to the  internet, and it generated a report for launchpad (which I couldn't  submit because there's no internet connection... LOL). 

I tried to restore to a previous point in windows but I'm still on the virtual  box network. It doesn't even see a wireless or ethernet option.

Is this a hardware problem?

---

### Post by haqking on 2012-01-20
Restore from backup (I know you have one as you were a major contributor to the basic security wiki ;-)

Then start again ;-)

I will await the infuriated PM LOL

---

### Post by Ms. Daisy on 2012-01-20
Hey- nice hat ;)

I DID restore on the Windows side. The restore was successful but the network connection is still owned by virtual box.  I didn't bother with a restore on the Ubuntu partition because it didn't work on the Windows partition.

Maybe I need to reinstall.

---

### Post by haqking on 2012-01-20
> **Ms. Daisy said:**
> Hey- nice hat ;)

I DID restore on the Windows side. The restore was successful but the network connection is still owned by virtual box.  I didn't bother with a restore on the Ubuntu partition because it didn't work on the Windows partition.

Maybe I need to reinstall.

I meant restore a point before you installed and played and trashed things.

If that includes the Ubuntu side then........

My hat is white really, it was dark in my room ;-)

---

### Post by Dangertux on 2012-01-20
That is a smexy fedora sir...

Yeah but did you try bringing up br0 yet, because that's the interface that is trying to get an IP right now. Not eth0 / wlan0 they are likely bridged to br0... It's kind of hard to explain but long story short fiddling with either of those two will be pointless until you fix the bridge.

I'm all for restoring from backups in this case if you can't figure it out. THough you might be right it may be hardware.

---

### Post by haqking on 2012-01-20
> **Dangertux said:**
> That is a smexy fedora sir...

Yeah but did you try bringing up br0 yet, because that's the interface that is trying to get an IP right now. Not eth0 / wlan0 they are likely bridged to br0... It's kind of hard to explain but long story short fiddling with either of those two will be pointless until you fix the bridge.

I'm all for restoring from backups in this case if you can't figure it out. THough you might be right it may be hardware.

why thankyou, it brings out the professional in me LOL

yeah br0 is likely the issue if software related.

if all else fails restore your clone or backup or whatever you have, if not i charge cheap rates for support but you will have to include the flight, accomodation and wait on me hand and foot ;-)

---

### Post by Ms. Daisy on 2012-01-20
smexy... I'm gonna try to work that word into a conversation today!

haqking- that's what I did. I restored Windows last night to a point about a week ago, long before I started breaking stuff (well... that I know about LOL). So you're saying I won't see results unless I restore both sides?

DT- yes I tried to bring up br0 by doing this
```
sudo ifconfig br0 down && sudo ifconfig br0 up
```
then terminal told me
```
Ignoring unknown interface br0=br0
```

Right now I'm searching for how one edits the config files, which is something I currently know nothing about.  Is this the right direction?

---

### Post by haqking on 2012-01-20
> **Ms. Daisy said:**
> smexy... I'm gonna try to work that word into a conversation today!

haqking- that's what I did. I restored Windows last night to a point about a week ago, long before I started breaking stuff (well... that I know about LOL). So you're saying I won't see results unless I restore both sides?

DT- yes I tried to bring up br0 by doing this
```
sudo ifconfig br0 down && sudo ifconfig br0 up
```
then terminal told me
```
Ignoring unknown interface br0=br0
```

Right now I'm searching for how one edits the config files, which is something I currently know nothing about.  Is this the right direction?

Well your original post said the problam occured today/yesterday after installing vmware and attempting an install of a OS, and Ubuntu being the host with the loopback issue ?

So why restore windows and not the host with the issue ?

or am i not understanding you ?

also what is the output of your ifconfig then in terms of avialable interfaces ?

So do you have virtual box installed on windows and vmware installed on Ubuntu and it is after installing vmware player that your system broke ?

This is way too confusing for me, i would of done a complete system restore by now and if still an issue it is hardware but im guessing a loose screw somewhere between the system and the owner...LOL

(MODS/ADMIN dont give me an infraction, MS Daisy can take it ;-)

---

### Post by Ms. Daisy on 2012-01-20
Loose screws withstanding, I think you're misunderstanding. ;) All of that is true except that Ubuntu networking is broken and so is Windows networking.  That's what I find strange- how did vmware, which lived on the ubuntu partition, affect the windows partition?  

Synopsis:
Dual boot Ubuntu 11.10 & Windows 7
Ubuntu had vmware player & virtual box.
Windows had virtual box.
All was happy until one of the vms (metasploitable) in Ubuntu bridged by default.
I have removed all virtualizing programs from both sides.
I'm still stuck in loopback on Ubuntu & no network on Windows.
I restored Windows, but virtual box still owns the network connection. Restore didn't fix the problem.

Thus leading me towards a hardware problem. 

the output of ifconfig is
```
eth0      Link encap:Ethernet  HWaddr 69:eb:69:e6:6a:69   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:43  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:140 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:140 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:11514 (11.5 KB)  TX bytes:11514 (11.5 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 69:a6:c9:69:a9:9a   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  

```

---

### Post by Dangertux on 2012-01-20
> **Ms. Daisy said:**
> Loose screws withstanding, I think you're misunderstanding. ;) All of that is true except that Ubuntu networking is broken and so is Windows networking.  That's what I find strange- how did vmware, which lived on the ubuntu partition, affect the windows partition?  

Synopsis:
Dual boot Ubuntu 11.10 & Windows 7
Ubuntu had vmware player & virtual box.
Windows had virtual box.
All was happy until one of the vms (metasploitable) in Ubuntu bridged by default.
I have removed all virtualizing programs from both sides.
I'm still stuck in loopback on Ubuntu & no network on Windows.
I restored Windows, but virtual box still owns the network connection. Restore didn't fix the problem.

Thus leading me towards a hardware problem. 

the output of ifconfig is
```
eth0      Link encap:Ethernet  HWaddr 69:eb:69:e6:6a:69   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:43  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:140 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:140 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:11514 (11.5 KB)  TX bytes:11514 (11.5 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 69:a6:c9:69:a9:9a   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  

```

It's not a hardware problem. 

Can you post the output of the following

```

lsmod | grep -i 'vboxdrv'

```Thanks

---

### Post by Ms. Daisy on 2012-01-20
> **Dangertux said:**
> It's not a hardware problem. 

Can you post the output of the following

```

lspci | grep -i 'vboxdrv'

```Thanks
There was no output.  I ran that twice and I just got a new prompt both times.

---

### Post by Dangertux on 2012-01-20
Hmm... Okay. In my opinion try reinstalling virtualbox, though I'm fairly certain it's actually VMware that hosed the config.

---

### Post by haqking on 2012-01-20
> **Dangertux said:**
> Hmm... Okay. In my opinion try reinstalling virtualbox, though I'm fairly certain it's actually VMware that hosed the config.

i agree, i hate vmware, well the desktop stuff anyways, esx and gsx is good stuff.

reinstall or a complete system restore if you have it, if you dont then tut tut and i will see you after class.

---

### Post by Dangertux on 2012-01-20
Oh hey you know what... The command I told yo ushould be 

```

lsmod | grep - i 'vboxdrv'

```

NOT lspci. Sorry tired... :-(

---

### Post by Ms. Daisy on 2012-01-20
> **Dangertux said:**
> Oh hey you know what... The command I told yo ushould be 

```

lsmod | grep - i 'vboxdrv'

```NOT lspci. Sorry tired... :-(
No worries, I don't know how you're not asleep on your feet.

I think you're right that it was vmware that hosed the cofig. Should I amend that command for vmware & run that, too?

---

### Post by Ms. Daisy on 2012-01-20
It's fixed!  Vmware is going on the windows side from now on.

Thanks guys!

---

### Post by haqking on 2012-01-21
> **Ms. Daisy said:**
> It's fixed!  Vmware is going on the windows side from now on.

Thanks guys!

What was the solution ?

oh and the solved option is on the thread tools menu ;-)
Peace

---

### Post by Ms. Daisy on 2012-01-21
Umm... I can't say I know.  It kinda magically was fixed when I rebooted the 5th time. But clearly it was a result of the excellent advice in this thread ;)

Yeah, and it's solved now for you too :P

---

### Post by haqking on 2012-01-21
> **Ms. Daisy said:**
> Umm... I can't say I know.  It kinda magically was fixed when I rebooted the 5th time. But clearly it was a result of the excellent advice in this thread ;)

Yeah, and it's solved now for you too :P

I think all it needed was our presence and awe LOL

---

