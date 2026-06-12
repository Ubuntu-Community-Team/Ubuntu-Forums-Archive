---
title: "&quot;netcat&quot; script on Ubuntu11.04, output = bring me KO. on Backtrack5 output is OK"
date: 2011-08-22
forum: General Help
---

### Post by slauper on 2011-08-22
Hi

I tried some workaround and search for help on internet, and now i asking about help.

GOAL OF SCRIPT:
Get the IP interface info (WAN IP) on my router. Because I want to access my ssh Demon and don't want to pay for system like dyndns.


ACUTAL SITUATION :
I Have :

[LIST]
[*]      3 Computer involved
[LIST]
[*]2 pc ubuntu 11.04 (last upgrade : everyday)
[*]1 laptop Backtrack5 (last upgrade : everyday)
[/LIST]
 
[*]3 Router (WIFI and LAN)
[*]2 Locations
[*]1 problem : this script above
[/LIST]

MY WISH :
What is wrong ? My ISP dhcp server send every 1 day to my router a new WAN IP. (I now i can change this value but it does not resolve the problem). So i use my backtrack_laptop_WIFI_or_LAN to script a code to get every 24 Hours my WAN IP:

GetRouterInfo.sh on Backtrack platfrom (i.e. : backtrack_laptop_WIFI_or_LAN)
```
netcat -t 192.168.1.1 23 >> /root/Desktop/MyGatewayInfo_Actual_Location << EOF
myusernameissecret
mypasswordissecret
netstat -i
quit
EOF
```With backtrack_laptop_WIFI_or_LAN and on every locations the script run well. I am logged in with backtrack default root. And become the /root/Desktop/MyGatewayInfo_Actual_Location file filled with my WAN IP info.

And modified script for Ubuntu platform
```
netcat -t 192.168.1.1 23 >> /home/MyUsername_CO/Desktop/MyGatewayInfo_CO << EOF
myusernameissecret
mypasswordissecret
netstat -i
quit
EOF
```and i triied also
```
netcat -t 192.168.1.1 23 >> /tmp/MyGatewayInfo_CO << EOF
myusernameissecret
mypasswordissecret
netstat -i
quit
EOF
```MY PROBLEM:
This script doesn't fill the > MyGatewayInfo_CO file under Ubuntu 11.04 platform i logged in with "MyUsername" and triied to run
```
,/GetRouterInfo
```and
```
sudo ./GetRouterInfo
```the output of
```
ls -l ~/Desktop
```is on backtrack_laptop_WIFI_or_LAN
```
-rwxr--r-- 1 root root 110 2011-08-22 17:39 GetRouterInfo.sh
```on both Ubuntu Ubuntu 11.04 platform
```
-rwxr--r-- 1 MyUsername_CO MyUsername_FR 110 2011-08-22 17:53 GetRouterInfo.sh
```HOW TO RESOLVE MY PROBLEM:
What do i need to modify to this script to run it on ubuntu?

---

### Post by Tamlynmac on 2011-08-22
Since this isn't a help section of the forums, might I suggest you use the report button and ask the staff to move your thread to the appropriate section.

Theoretically, this section of the forums is for members to share their experiences and testimonials. Please see the sectional guidelines and this [sticky]("http://ubuntuforums.org/showthread.php?t=1343965").

Good Luck

---

### Post by overdrank on 2011-08-22
Moved to General Help

---

### Post by slauper on 2011-08-22
Thx i was searching how to contact Forum admin Team, sorry i am not familiar with forum i'll go read the "Code of Conduct" i missed it on the road. thx for moving it so fast and keep forum well structured.

---

### Post by Dangertux on 2011-08-22
I really would like to help with this but I'm having a very difficult time understanding your flow charts, are you saying that the Backtrack install works at BOTH locations, however the Ubuntu install works at neither location? Or the Ubuntu install works at 1 location but not the other?

Another thing that might make a difference (although I doubt it). Your ubuntu install might have a different version of netcat (ie: openbsd vs traditional) although this shouldn't change anything. IIRC the version installed on Backtrack is the traditional version of netcat, you can try that. 


Also have you tried manually stepping through the script on the ubuntu machine to see precisely which point it is failing at?

IE: is netcat failing to properly auth to telnet, is it not pulling your wan info, is the script just broken etc...

 I'm sorry if you answered that already, but as I said I had a very hard time understanding your post :-(

---

### Post by slauper on 2011-08-22
Hi Dangertux
 thx answer me.
 I know it is a complicated situations.
 
 Yes running the script on Backtrack platform work on both location.
 Yes running the script on Ubuntu platform doesn0t work on both location.
 
 on both platform i run :
 ```
netcat -help
``` it output me following on Backtrack5: > [v1.10-38] and it output me following on Ubuntu11.04 > OpenBSD netcat (Debian patchlevel 1.89-3ubuntu5) You was right the version aren't the same. how should it affect the script differently?
 
 I tried to "verbose" the script but i don't know how to run a script step-by-step(breakpoint like) in verbose mode.
But i triied it manually step-by-step in the terminal as MyUsername and Sudo like step above on both location it was OK:

[LIST=1]
[*]```
netcat -i 192.168.1.1 23
```> Router system ask me for login
[*]```
myusernameissecret
```> Router system ask me for password
[*]```
mypasswordissecret
```> Router system waiting for my command
[*]```
netstat -i
```> Router system show me interface infos (include IP WAN)
[*]```
quit
```> Router system say me "Goodbye." and terminal take handover
[/LIST]

 
Yes on ubuntu11.04 the script don't fill the MyGatewayInfo_CO file that normally should contain the collected router IP WAN.

---

### Post by Dangertux on 2011-08-23
ok -- great so now we know where the issue is. 

It's not writing the output. Have you tried echoing the netstat -i command output into the file instead of the output of the original netcat command.  

That might help :-/ I am just having a hard time understanding why it works in bt but not ubuntu that is bizzarre.

---

### Post by slauper on 2011-08-23
Thanx for add ideas.

I tried until i understand about following reflection :

[LIST=1]
[*]I need to logged on my Gateway with full Read/Write access to run ```
netstat -i
```
[*]I can't store data on my Gateway.
[*]I can't set up an ssh connection from my gateway to one of my computer.
[*]I don't want go hacking my own Gateway.
[LIST]
[*](...I will experiment this way only if it's the last chance, because i want to keep my script as portable/easy-to-use as possible.)
[/LIST]
[*]Because it's unclear why it not full function in actually way of mather.
[/LIST]

---

