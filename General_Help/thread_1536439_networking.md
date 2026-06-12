---
title: "networking"
date: 2010-07-22
forum: General Help
---

### Post by softtouch on 2010-07-22
Hi, i am absolute beginner, do not understand terminolgy yet, please be kind.  I have just installed Ubuntu to dektop, i have another desktop and a laptop both running XP, all connected via Devolo Dlan plugs, all can connect to internet, but ubuntu machine will not acess Xp, or vice versa.  Have run Samba and have shared folders.  Am i missing something.  Thanks in advance.

---

### Post by varunendra on 2010-07-23
Log into the XP machine, open command prompt (Start>Run>cmd) enter this command:
```
ipconfig /all >"%userprofile%\desktop\ipconfig.txt"
```A file named "ipconfig.txt" will be generated on your desktop. Post its contents here.

Also, log into your Ubuntu machine, open terminal (Applications>Accessories>Terminal), enter and post results of the following commands:
```
ifconfig -a
``````
sudo dhclient
``` (remember- running ANY command with 'sudo' will run it as root. You'll be asked for 'Your' password which you won't see as you type)
```
route
```
If you have problems only in accessing shared folders between XP and ubuntu, maybe this thread can help you:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by softtouch on 2010-07-23
Hi, thanks for reply, will try suggestions at weekend and get back to you, thanks again.

---

### Post by softtouch on 2010-07-24
Hi, seems i know less than i thought, no txt file came to desktop, copy/paste option not available.  Managed to get results from ubuuntu, please find three attachments.  Thanks.

---

### Post by varunendra on 2010-07-24
> **softtouch said:**
> Hi, seems i know less than i thought, no txt file came to desktop, copy/paste option not available.  Managed to get results from ubuuntu, please find three attachments.  Thanks.

sorry, it was a typo on my part :(
I have corrected (& tested) the command ipconfig....... in the my previous post. Please try again.

My ISP is currently playing hide & seek with us, so maybe I'll reply sometime later. :)



**EDIT:** Posting the contents is better than posting the txt files themselves. This makes the viewing easier for all- both Windows & Linux users.
**Method:** Highlight the whole content, copy, paste in your post. Then highlight the pasted text (in your post), and click on "#" icon on the top of the post editing window.

---

### Post by softtouch on 2010-07-24
```
Hi, results for Windows IP Configuration hope it helps.                                           Host Name . . . . . . . . . . . . : Phils2nd
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
 
Ethernet adapter Local Area Connection:
 
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-16-17-E1-46-C0
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        IP Address. . . . . . . . . . . . : fe80::216:17ff:fee1:46c0%4
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
                                            fec0:0:0:ffff::1%1
                                            fec0:0:0:ffff::2%1
                                            fec0:0:0:ffff::3%1
        Lease Obtained. . . . . . . . . . : 24 July 2010 12:49:17
        Lease Expires . . . . . . . . . . : 25 July 2010 12:49:17
 
Tunnel adapter Teredo Tunneling Pseudo-Interface:
 
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
        Physical Address. . . . . . . . . : FF-FF-FF-FF-FF-FF-FF-FF
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : fe80::ffff:ffff:fffd%5
        Default Gateway . . . . . . . . . : 
        NetBIOS over Tcpip. . . . . . . . : Disabled
 
Tunnel adapter Automatic Tunneling Pseudo-Interface:
 
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Automatic Tunneling Pseudo-Interface
        Physical Address. . . . . . . . . : C0-A8-01-02
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : fe80::5efe:192.168.1.2%2
        Default Gateway . . . . . . . . . : 
        DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                            fec0:0:0:ffff::2%1
                                            fec0:0:0:ffff::3%1
        NetBIOS over Tcpip. . . . . . . . : Disabled
```

---

### Post by varunendra on 2010-07-25
Sorry for a late response....

Although you stated clearly in your first post that "all can connect to internet...">  I have just installed Ubuntu to dektop, i have another desktop and a  laptop both running XP, all connected via Devolo Dlan plugs, all can  connect to internet, but ubuntu machine will not acess Xp, or vice  versa.....but I somehow confused it as if 'the ubuntu machine is not able to connect to "anywhere" at all'. Now I feel stupid about it as the outputs you posted make it clear that you are having no problems in connecting to internet from 'Any of the Three machines'.

Now for the problems in Ubuntu and XP machines seeing each-other, have you followed the link to dmizer's thread I provided in my first post?

As a basic checkup, here are some points you should make clear:

[LIST=1]
[*]XP and Ubuntu machines can ping each-other's IPs (obvious, but won't hurt checking).
[*]Both XP and Ubuntu machines should be members of same workgroup or domain. By default, Ubuntu is member of workgroup- "WORKGROUP".
[*]Make sure windows firewall is turned off at the connected interface (connection>Properties>Advance tab>Firewall Settings>"Off"; also clear the checkbox for the selected interface found under 'Advance' tab of Firewall Settings)
[*]If they still can't see each other, try accessing them with their IPs (in Ubuntu, open Places>Network, then click on Go>Location... and type > smb://192.168.1.2while the XP machine 192.168.1.2 is running. Or, on XP machine, open any folder and type in the address bar:> \\192.168.1.4while ubuntu machine (192.168.1.4) is running.
[/LIST]
For a detailed idea of these and more issues, please follow the thread I gave you link of.

---

### Post by softtouch on 2010-07-25
Hi, again, here are some results of tests you suggested,  ping test from XP machine to Ubuntu ok.  Ping from Ubuntu to XP ok.
both on "workgroup". 
When i search for Ubuntu ip adress i get a website.
When i search on Ubuntu machine i get not found error.
Following link i tried prolem 2, but when i typed in "gksudo gedit/etc/samba.conf" i got nothing.
When i typed "gksudo gedit/etc/nsswitch.conf" i got nothing.
 Did not turn off firewall as last time i did that i had even more problems, will above only work with firewall off?

---

### Post by varunendra on 2010-07-25
> **softtouch said:**
> When i search for Ubuntu ip adress i get a website.
make sure you don't type //192.168.1.4 (notice it is 'forward' slash which is wrong for for a local address in windows) it should be a 'backslash':
```
\\192.168.1.4
```


> **softtouch said:**
> When i search on Ubuntu machine i get not found error.again, make sure it is exactly as I quoted in my previous post. (you can just copy-paste the commands)


> **softtouch said:**
> Following link i tried prolem 2, but when i typed in "gksudo gedit/etc/samba.conf" i got nothing.
When i typed "gksudo gedit/etc/nsswitch.conf" i got nothing.
 Did not turn off firewall as last time i did that i had even more problems, will above only work with firewall off?Since that was dmizer's thread, you should should seek further guidance about these discrepancies there (you can simply put a reference link to this thread there and ask for help).
However right now, I can see following syntax errors in your commands that you should correct first:

[LIST=1]
[*]you've left no 'space' between gedit and /etc......... Also, it is /etc/samba/smb.conf (not /etc/samba.conf). To avoid typo, just copy-paste the command:```
gksudo gedit /etc/samba/smb.conf
```
[*]In the next command also, there should be 'space' between gedit and location:```
gksudo gedit /etc/nsswitch.conf
```
[/LIST]
As for firewall issue, although it 'should not' be necessary, yet in the past I have experienced problems with it. So either you should turn it off completely, or you may need to define exceptions there for your local hosts. For now I'd suggest to turn it off at least until your sharing problem is solved- just to be sure that it is not the culprit! :)

---

### Post by softtouch on 2010-07-25
Hi, copied and pasted code into XP browser, but still get search page.
 Did the same on Ubuntu machine and got a result!  Will go through suggestions from link you gave and see what happens.  Thanks again for your help and patience.:)

---

