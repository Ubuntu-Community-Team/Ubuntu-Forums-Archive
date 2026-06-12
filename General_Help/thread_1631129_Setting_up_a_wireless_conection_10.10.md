---
title: "Setting up a wireless conection 10.10"
date: 2010-11-26
forum: General Help
---

### Post by Jacob72 on 2010-11-26
Hello

Are there any instructions for setting up a wireless connection for 10.10?

I do not know what to put for the following: 

SSIS 
BSSID 
Device MAC address 
Cloned MAC address

Thnaks

---

### Post by oliwek on 2010-11-26
you just click on the network icone, and select the SSID (the name) of your router/box, you should have there a list of wifi routers from the neighborhood. If your wifi adapter works.

you look for the icon looking like a PC monitor :

[IMG]http://t3.gstatic.com/images?q=tbn:ANd9GcT1ntdTHl8BDUJVT7Ejq6kOi08wlQDoZy9vRdVqEcXMLG_ju-oGdw[/IMG]


if it doesn't work, I mean if you see no wifi Access Points list (it's called 'Wireless Networks' as on the picture above), open a terminal (console) window (from Applications>Accessories>Terminal), and type :

```
ifconfig
```

and

```
iwconfig
```

then post (copy-paste) the results here


note : you've got info here : [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

but it's not really newbie-friendly...

---

### Post by jim_deadlock on 2010-11-26
If you've only recently installed Ubuntu, then I would suggest that you first use a wired connection and do your system updates System -> Administration -> Update Manager. This should install the various drivers you need for your wireless card. After that, go to System -> Administration -> Additional Drivers and activate anything you have there. Once you've done all that, unplug your cable and reboot, then click the network manager icon on your top panel and it should list some wireless networks, from there you can select yours, enter the password and off you go.

---

### Post by oliwek on 2010-11-26
Give some details about how you connect to the internet : do you have a wifi router? already set up? another PC or OS (Windows?) to try internet?

---

### Post by Jacob72 on 2010-11-26
Great Reply!

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

jacob@jacob-701:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:e4:5e:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

jacob@jacob-701:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.




---

### Post by nothingspecial on 2010-11-26
It says you don`t have wireless

type

```
sudo lshw -C network
```And post the gobbldygook back here

---

### Post by Jacob72 on 2010-11-26
OK, hold up, I did not see the new posts/edit.

I don't have the monitor icon on the top bar, only the network icon.

> If you've only recently installed Ubuntu, then I would suggest that you first use a wired connection and do your system updates System


Great, now I tried this and got Authenticate box. Not sure what password to put in? I tried my user password but it failed?

---

### Post by nothingspecial on 2010-11-26
> **Jacob72 said:**
> OK, hold up, I did not see the new posts/edit.

I don't have the monitor icon on the top bar, only the network icon.



Great, now I tried this and got Authenticate box. Not sure what password to put in? I tried my user password but it failed?

If you are talking about the updates, then it should be your user password, try it again.

If it is for the wireless network then it is the wireless key

---

### Post by Jacob72 on 2010-11-26
> **Jacob72 said:**
> OK, hold up, I did not see the new posts/edit.

I don't have the monitor icon on the top bar, only the network icon.



Great, now I tried this and got Authenticate box. Not sure what password to put in? I tried my user password but it failed?


Oops, it just worked. Will do this then step two of console.

---

### Post by Jacob72 on 2010-11-26
Installed updates OK.

Typed in 'sudo 1shw -C network' and got:
```
[sudo] password for Jacob:
```
?

---

### Post by Swagman on 2010-11-26
If you have done that from within the Terminal

Enter the password you use to log in / update

Clue.. You **WONT** see * ANYTHING* as you type your password in

---

### Post by Jacob72 on 2010-11-26
Well thanks for the clue!!

I had tried typing the password

---

### Post by Jacob72 on 2010-11-26
Repeated what I did before but it said 'command not found', I then copied and pasted the command from nothingspecial's post and got something else:
```
sudo lshw -C networkjacob@jacob-701:~$ sudo 1shw -C network
sudo: 1shw: command not found
jacob@jacob-701:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:e4:5e:93  
          inet6 addr: fe80::21e:8cff:fee4:5e93/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1592 (1.5 KB)  TX bytes:7970 (7.9 KB)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

jacob@jacob-701:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jacob@jacob-701:~$ sudo 1shw -C network
sudo: 1shw: command not found
jacob@jacob-701:~$ sudo 1shw -C network
sudo: 1shw: command not found
jacob@jacob-701:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:e4:5e:93
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff
jacob@jacob-701:~$ sudo lshw -C network
PCI (sysfs)  

```

---

### Post by Jacob72 on 2010-11-26
Re-booted, and add the command again, this produced 

```
[sudo] password for Jacob:
```

I typed it in very carefully (the cursor did not move?) hit enter and got:
 ... command not found
?

---

### Post by Jacob72 on 2010-11-26
> Give some details about how you connect to the internet : do you have a wifi router? already set up? another PC or OS (Windows?) to try internet?


I am using an Orange Live box wireless router (So I am told)I have a Windows PC connected to it.

---

### Post by Jacob72 on 2010-11-26
> After that, go to System -> Administration -> Additional Drivers and activate anything you have there.

Missed that, Additional Drivers is empty?

Just followed Oliwek's link, as I have a router I can plug in to, should I go to software center in my menu and search?

---

### Post by nothingspecial on 2010-11-26
Sorry, been out.

Your typing a number one, it`s supposed to be a little L

 sudo [COLOR=Red]l[/COLOR]shw -C network

---

### Post by Jacob72 on 2010-11-26
Hello
OK, got this
> jacob@jacob-701:~$ sudo lshw -C network
[sudo] password for jacob: 
  *-network               
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: ----------------------
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff
jacob@jacob-701:~$ 


---

### Post by nothingspecial on 2010-11-26
Your wireless isn`t being recognised.

Do you know what card you have?

---

### Post by Jacob72 on 2010-11-26
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. Device 82d9
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 82d9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
:

---

### Post by nothingspecial on 2010-11-26
Jacob, you don`t appear to have a wireless card. Do you know what make your wireless card is?

---

### Post by Jacob72 on 2010-11-26
I am using an Eee Pc 4g it is as it was out of the box. I had a wireless conection when I was running W XP?

Sorry I do not even know what a wireless card is.

---

### Post by d3v1150m471c on 2010-11-26
```

lspci | grep -i "NETWORK" # will show your wireless card

```

---

### Post by oliwek on 2010-11-29
sorry, I wasn't there to follow your thread... did you solve it?

You use an [atheros wireless card]("http://www.tracyandmatt.co.uk/blogs/media/blogs/tracyandmatts_blog/Eee_PC_3G.jpg") in your eee-pc (included in your netbook hardware). It should work out of the box with ubuntu(I use the same netbook and same OS), but is your wlan/wifi card ON? do you see the blue [LED]("http://en.wikipedia.org/wiki/LED_lamp") lit? If not, the shortcut Fn+F2 should enable it (Fn is the Function key, on the left of the spacebar, press it and the F2 key simultaneously, then you should see the blue LED switching ON and OFF, you need it ON).

see the blue LED (bottom right)showing wifi activated on this picture : [IMG]http://www.wirelessmuse.com/winternet/Asus_20Eee_20PC_20701_20_2D_2D_20mine_20_2D_20with_20Microsoft_20wireless_20mouse_20and_20my_20Internet_20Evolution_20column_20on_20the_20screen_20_2D_20RIM_20Curve_20photo_thumb.jpg[/IMG]

If you can't switch the wifi ON with Fn+F2, then you should reboot, enter BIOS settings, and check that wifi is activated in the BIOS.

---

### Post by Jacob72 on 2010-11-29
> If not, the shortcut Fn+F2 should enable it (Fn is the Function key, on the left of the spacebar, press it and the F2 key simultaneously, then you should see the blue LED switching ON and OFF, you need it ON).


That done it!

Thank you all for your help!

---

