---
title: "not connecting to all XP computers"
date: 2010-09-04
forum: General Help
---

### Post by KeithBCDN on 2010-09-04
I'm a newb to Linux and have 3 problems for which I have done extensive research on the net for solutions. Help needed!
Perhaps one at a time would be better.

I have configured Ubuntu 10.04 to work on a Windows XP network that has 2 other XP desktops (wired to same router).
Ubuntu sees the icons for each computer in the "network" tab of "places" and can access the shared files 1 of those desktops, no problem, but  trying to access the other one gets the error "Unable to mount location-failed to retrieve share list from server"
I have checked the XP computers and can't find what may be different about them.
Something simple has escaped me and any insight to what I should be looking for would be appreciated.

---

### Post by Morbius1 on 2010-09-04
Could be a firewall problem on the WinXP machine. Run this command from Ubuntu:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Substitute the ip address of the windows machine you cannot get access to.*[/COLOR]

Ports 139, 445, 137, and 138 need to be open.

[COLOR=Blue]EDIT: I keep on forgetting. You need to install nmap first:[/COLOR]
```
 sudo apt-get install nmap
```

Another diagnostic command you can use is:
```
smbtree
```It will show you all the machines on your network and give you errors ( hopefully different than the one you already got ) if something is amiss.

---

### Post by KeithBCDN on 2010-09-04
Here is the result from both computers.The "problem " one first.
Looks like the ports you listed are open.

Not shown: 1982 closed ports
PORT     STATE         SERVICE
135/tcp  open          msrpc
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
2869/tcp open          unknown
6002/tcp open          X11:2
7001/tcp open          afs3-callback
7002/tcp open          afs3-prserver
123/udp  open|filtered ntp
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
445/udp  open|filtered microsoft-ds
500/udp  open|filtered isakmp
1025/udp open|filtered blackjack
1036/udp open|filtered unknown
1900/udp open|filtered upnp
4500/udp open|filtered nat-t-ike
5353/udp open|filtered zeroconf
6001/udp open|filtered X11:1
MAC Address: 00:0D:9D:98:DE:35 (Hewlett Packard)

Not shown: 1000 open|filtered ports, 996 filtered ports
PORT     STATE  SERVICE
139/tcp  open   netbios-ssn
445/tcp  open   microsoft-ds
1039/tcp closed unknown
2869/tcp open   unknown
MAC Address: 00:13:20:3F:DF:E7 (Intel Corporate)

---

### Post by Morbius1 on 2010-09-04
If that's the nmap against the "problem" WInXP machine then the firewall is not the problem. What about the output of smbtree?

---

### Post by KeithBCDN on 2010-09-05
The first info was from the computer Ubuntu can't access and the second is the one it can access.
As for smbtree...I don't know what that is. I'm still learning this Linux stuff.

---

### Post by KeithBCDN on 2010-09-05
Perhaps the printing problem I am also having is associated with the file sharing problem.
This is a network printer on the same Windows network computer that I can access the files on from Ubuntu.
I have set up the printer as instructed in this help file...
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)
Everything goes along just fine until "print test page" No go.
Under "printer properties" the "Make and Model"are showing the correct device in the correct location.
The "Printer State" shows "idle - /usr/lib/cups/filter/foomatic-rip failed"

---

### Post by Morbius1 on 2010-09-05
> As for smbtree...I don't know what that is.Open a terminal and type:
```
smbtree
```
Post the output

---

### Post by KeithBCDN on 2010-09-05
"Emporepenguin" is the computer that is giving the problem.
"Keith" is the Ubuntu machine
"Katitude" is the other XP that I can see and has the printer 

session request to 192.168.0.100 failed (Called name not present)
JOOLZ
    \\KEITH                  
        \\KEITH\keith shared       
        \\KEITH\documents          
        \\KEITH\IPC$               IPC Service ()
        \\KEITH\MyFiles            
        \\KEITH\print$             
    \\KATITUDE               
        \\KATITUDE\Printer            Microsoft Office Document Image Writer
        \\KATITUDE\C$                 Default share
        \\KATITUDE\ADMIN$             Remote Admin
        \\KATITUDE\Printer3           CutePDF Writer
        \\KATITUDE\HPLaserJ           HP LaserJet 1018
        \\KATITUDE\print$             Printer Drivers
        \\KATITUDE\IPC$               Remote IPC
        \\KATITUDE\Kats Shared        
    \\EMPERORPENGUIN         
cli_start_connection: failed to connect to EMPERORPENGUIN<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

---

### Post by Morbius1 on 2010-09-05
I have never seen this error message before:
>  session request to 192.168.0.100 failed (Called name not present)Which machine is 192.168.0.100 ?

While I research this, can you access EMPERORPENGUIN by ip address:
In a terminal type:
```
nautilus smb://192.168.0.120
```[COLOR=Blue]*Change 192.168.0.120 to the ip address of EMPERORPENGUIN         *[/COLOR]

---

### Post by Nythain on 2010-09-05
is an age old problem with gvfs... here's a couple of the launchpad bugs involving it, with various workarounds... good luck, this problem has plauged me for the last 2 or 3 releases of ubuntu now.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/356022](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/356022)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/384881](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/384881)

---

### Post by Morbius1 on 2010-09-05
It may very well be a problem with gvfs but the problem in this situation is that it's affecting only one of his two Windows machines. I would think that if it was something inherent in the Linux machine it would affect all machines. In fact based only on the information we have here it sounds like a Windows problem only on one machine.

If you look at the ports that are open on the machine that's having the problem there's clearly something installed on that box that is not installed on the other Windows box.

---

### Post by KeithBCDN on 2010-09-05
192.168.0.100 is KATITUDE and Ubuntu can access those files. Printer is on SAME
192.168.0.120 is EMPORERPENGUIN no access

I have a total of 4 XP computers on the network and they all share correctly to each other so I came to the conclusion that the sharing options and network setup is correct. Perhaps a poor conclusion. I was hoping that some digging at the Ubuntu end of things might show where to look for a problem.

---

### Post by Nythain on 2010-09-05
so the
```

nautilus smb://192.168.0.120

```
still doesnt allow for connection to the machine? you weren't very specific if you tried and still couldnt retrieve the server list.

everything i could find concerning this error in similar situations actually points to wonky DNS behavior, with isp DNS servers trying to supersede wins/samba/local network DNS resolution.

as crazy and oddly promotional as this sounds, a few people have reported fixing the problem by changing their routers dns server to use Google's DNS servers, 8.8.8.8 and 8.8.4.4

guess we'll see where to go from here based on further input

---

### Post by KeithBCDN on 2010-09-05
Yes, the command did allow connection to Emporerpenguin and I could open shared files.
The folders that I open are now on the Ubuntu desktop.
When I re-boot Ubuntu , I have to do the same command to get access to the files.
 Works for me as I don't usually turn off the network computers.
Does this indicate a solution or do I need to do this every time I want to access the EMPORER... computer?

---

### Post by QLee on 2010-09-06
[QUOTE=KeithBCDN]Yes, the command did allow connection to Emporerpenguin and I could open shared files.
The folders that I open are now on the Ubuntu desktop.
When I re-boot Ubuntu , I have to do the same command to get access to the files.
 Works for me as I don't usually turn off the network computers.
Does this indicate a solution or do I need to do this every time I want to access the EMPORER... computer?[/QUOTE]
Well, I would think that, if Emporerpenguin, is in the hosts file, it shouldn't need to request a DNS translation.

I believe what Nythain was meaning was to set those new DNS servers in your router config so the router hands them out with the IP address rather than the ones announced by the ISP connection. Then you wouldn't need to do the workaround after a reboot.

---

### Post by KeithBCDN on 2010-09-06
I may re config the router but this work around is fine for what I'm doing.
Thanks for the input and I do appreciate the help.
I will open a new thread for the printing issue.

---

### Post by QLee on 2010-09-06
Is the server in the hosts file?

---

### Post by KeithBCDN on 2010-09-06
> Is the server in the hosts file?I'm not as savvy with computers as I could be so could you expand on the question a bit?
please note the "first cup"..and all that :)

---

### Post by QLee on 2010-09-06
> **KeithBCDN said:**
> I'm not as savvy with computers as I could be so could you expand on the question a bit?
please note the "first cup"..and all that :)
Well, plenty of people come here with GNU/Linux experience, since you seemed to be following everything, I didn't know what you might already know, do now.

The file I was referring to is /etc/hosts, servers that are listed in hosts should not need name resolution from a DNS server.

But, since you're happy with the solution you chose, so am I.

If you want to find out more about the hosts file, you can enter the command, man hosts, that will open the manual page for the hosts file.

---

### Post by KeithBCDN on 2010-09-06
Thanks QLee.
I may come back to this at another time but there are other small bugs to work out in the mean time.

---

### Post by 23dornot23d on 2010-09-27
I do not do a lot with networks .....

So if anyone thinks this is wrong please comment .....


aptitude install openssh-server
aptitude install konqueror
aptitude install fish

Create a quick launcher on the desktop ..... left click ..... enter konqueror in the command line and the text you want to see ...
you could also add it as a comment too .........

  Open konqueror 

enter this into the top bar .....

fish://(username)@192.168.1.xxx
[COLOR=Red]or whatever the IP is for the machine that you need to connect to ..........[/COLOR]

It should then ask you for **your username and password** to connect to your machine
I hope that this works ............ 

[COLOR=Blue][I][B]( I tried it out on my machine and all seems good )
[/B][/I][/COLOR] 
If anybody think's that there are any security issues here .... please let me know .......... :confused:

I read about ssh sometimes and hear that it can be vulnerable ..... but I am not sure if its needed in this instance ..... but without it ...... 

I could not connect ..... 

I am always cautious ..... as far as I know people still need your username and password to get in .... 
as these are the first questions you are asked before being allowed into the file system on the other computer .....
and even with them they cannot get in not at root level as far as I know.

But if anyone knows different please tell me how ...... or why SSH  may be unsafe .....

I am connecting using fish ..... 

( but it did not seem to work without the openssh-server installed on my other system )

---

