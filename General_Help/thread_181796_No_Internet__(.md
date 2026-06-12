---
title: "No Internet : ("
date: 2006-05-24
forum: General Help
---

### Post by That Guy X on 2006-05-24
Hi , I had a thread with this problem before but no one could help me so i just gave up. But i installed the new version of dapper drake (flight 7) and im getting the same problem but maybe someone could provide a solution cence this one has less bugs. The problem is you geussed it no internet , here are some screen shots. I was able to get these by putting them on my flash drive and useing this forum on windows.

[ATTACH]9987[/ATTACH]

[ATTACH]9988[/ATTACH]

[ATTACH]9989[/ATTACH]

[ATTACH]9990[/ATTACH]

[ATTACH]9991[/ATTACH]

---

### Post by an.echte.trilingue on 2006-05-24
So how do you normally connect to the internet with windows?  DSL? Cable?  Do you have a router?

---

### Post by That Guy X on 2006-05-24
I have a DSL/ROUTER  westell model 327w

---

### Post by That Guy X on 2006-05-24
Ive also had this same problem with other linux distros ive tried such as mepis.

---

### Post by ifokkema on 2006-05-25
Hi,

Looking at your second screenshot, you don't have a default gateway. Your computer doesn't know which device to use to talk to the outside. Can you select your eth0 device there?

If that doesn't work, could you send the output of
```
netstat -ie
```

Ivo

---

### Post by dmizer on 2006-05-25
remove ipv6:
```
sudo gedit /etc/modprobe.d/bad_list 
```
Add this line:  ```
alias net-pf-10 off 
```
Save the file and restart your computer.

i believe the modem/router you have can connect to your pc via ethernet cable or usb, which are you using?

also ... paste the output of ifconfig please.

---

### Post by That Guy X on 2006-05-25
[ATTACH]10034[/ATTACH]

Is that file suppose to be blank?:confused:

---

### Post by tommcd on 2006-05-25
That Guy X, does your DSL modem use PPPoE protocol? If it does, did you try running sudo pppoeconf in terminal? The pppoe plugin needs to be configured if your DSL uses ppoe.

---

### Post by jvictor on 2006-05-26
if u know ur default gateways Ip , u can use the cmd

$route add -n gw<your dsl-routers-ip-add>

If it doesnt work , post the o/p of


$ less /etc/resolv.conf

$ifconfig eth0

$ route

---

### Post by dmizer on 2006-05-26
[QUOTE=That Guy X][ATTACH]10034[/ATTACH]

Is that file suppose to be blank?:confused:[/QUOTE]
yes ... you are creating it.  just add the line and save it.  then reboot.

if that doesn't work, do what jvictor says above.

---

### Post by handy on 2006-05-26
I have to turn off ipv6 in Firefox, or NO internet for me!

To do this:

Enter **about:config** in the address field.

Then enter **ipv6** in the **Filter:** field.

Then double click on the line showing, to change the boolean value to **TRUE**.

Then close the tab.  I forget if I had to reboot or not?  Try just restarting Firefox first.

If I don't do the above I can not browse the net at all.

I hope this helps you!? :KS

---

### Post by daveg2 on 2006-05-26
I'm having the same problem with a clean Flight 7 install.  The only difference so far is that I'm using a Netgear FVS318 router connected to an Ambit cable modem.  My NIC is a CNET PRO200WL PCI Fast Ethernet Adapter.  

It's a dual-boot system with WinXP.  XP doesn't have any problems.  Other systems on the network using DHCP are having no problems.  The primary issue seems to be that after dhclient runs, the route table is empty.

P.S.  Sorry to butt into an existing thread if it's going to cause confusion.  Please let me know....  Seems appropriate since it seems to be the identical problem.  If appropriate, please let me know if there is any additional info I can offer.

---

### Post by jvictor on 2006-05-26
daveg2, 
in your case did u try 

routeadd -n gw <your_gateways_ip> ?

---

### Post by daveg2 on 2006-05-26
Sorry, my mistake.  Cold boot and now route returns:
Destination  Gateway     Genmask         Flags Metric Ref Use Iface
192.168.0.0 *               255.255.255.0 U       0       0    0    eth0
default        192.168.0.1 0.0.0.0          UG     0       0     0   eth0

As 192.168.0.1 is my router, DHCP server and DNS, this may be AOK.  route add -n gw 192.168.0.1 reports "Host name lookup failure".  Is this due to route already exists in the table?

P.S.  I forgot to note that ping 192.168.0.1 fails, as does pinging other boxes on the network.

---

### Post by handy on 2006-05-26
[QUOTE=daveg2]I'm having the same problem with a clean Flight 7 install.  The only difference so far is that I'm using a Netgear FVS318 router connected to an Ambit cable modem.  My NIC is a CNET PRO200WL PCI Fast Ethernet Adapter.  

It's a dual-boot system with WinXP.  XP doesn't have any problems.  Other systems on the network using DHCP are having no problems.  The primary issue seems to be that after dhclient runs, the route table is empty.

P.S.  Sorry to butt into an existing thread if it's going to cause confusion.  Please let me know....  Seems appropriate since it seems to be the identical problem.  If appropriate, please let me know if there is any additional info I can offer.[/QUOTE]

My Router/Modem is a Netgear DG632, apart from the ipv6 problem, I MUST do the following, or I can not access the repositories.

****
This section by *[Python]("http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router")*, I gold!

---

### Post by daveg2 on 2006-05-27
Dual boot system, Dapper and XP.  Wired network.  XP worked fine.  Couldn't ping the router under Dapper.  The NIC is a CNET Pro200WL PCI Fast 10/100 Ethernet Adapter.  lsmod revealed that two drivers, both tulip and dmfe, were being loaded for the card.  modprobe -r tulip, modprobe -r dmfe, modprobe tulip, ifconfig eth0 up. got me up and running for a short time, then dropped.  modprobe -r tulip, modprobe dmfe, ifconfig eth0 up seems to have me up and running.

Now to blacklist tulip so it dosn't load on boot.   That Guy X, I hope my findings help you.  All, thank you for your help and sorry about hijacking the thread.

This is one happy camper after stumbling around in the dark for a day!  Hmmm.  Maybe I better bug this.

---

### Post by jvictor on 2006-05-28
Daveg2, conxn droppage typically looks like a DHCP problem. Try a static IP instead of DHCP u will get things working

can u post the o/p of 

$less /etc/hosts
$less /etc/resolv.conf

---

### Post by daveg2 on 2006-05-28
Jvictor, it's working now.  I'm posting this from Firefox running under Dapper.  Thank you for your help.

---

