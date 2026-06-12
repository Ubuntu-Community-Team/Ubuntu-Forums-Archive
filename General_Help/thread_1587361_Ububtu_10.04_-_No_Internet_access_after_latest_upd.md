---
title: "Ububtu 10.04 - No Internet access after latest updates"
date: 2010-10-03
forum: General Help
---

### Post by sandfire on 2010-10-03
Hi,

I am using my laptop to access the internet. The problem is with my Desktop using Ubuntu 10.04. 

New updates were installed on the Desktop last night and this morning I restarted to computer as required by the Update Manager.

Since then I have not been able to access the Internet with the Desktop and Firefox is very slow loading and sometimes can take several minutes, but will not access any websites.

I have even tried Google Chrome which loads very quickly but with the same result - it will not access the internet.

Can anyone help to resolve this please?

Cheers

Sandfire

---

### Post by sandfire on 2010-10-03
> **sandfire said:**
> Hi,

I am using my laptop to access the internet. The problem is with my Desktop using Ubuntu 10.04. 

New updates were installed on the Desktop last night and this morning I restarted to computer as required by the Update Manager.

Since then I have not been able to access the Internet with the Desktop and Firefox is very slow loading and sometimes can take several minutes, but will not access any websites.

I have even tried Google Chrome which loads very quickly but with the same result - it will not access the internet.

Can anyone help to resolve this please?

Cheers

Sandfire

I am bumping this because I need urgent help, please

---

### Post by krishnandu.sarkar on 2010-10-03
I don't know how to solve this problem. But as you are in an urgent position, I'm suggesting you to configure your router to PPPoE mode(i.e. Automatic Dialing mode). Use your internet in this way till other experienced members comes in and helps you.

---

### Post by sandfire on 2010-10-03
> **krishnandu.sarkar said:**
> I don't know how to solve this problem. But as you are in an urgent position, I'm suggesting you to configure your router to PPPoE mode(i.e. Automatic Dialing mode). Use your internet in this way till other experienced members comes in and helps you.

Hi Krishnandu.



Thanks for your attempt to help, but I haven't got a clue how to do what you suggest.

I am not a geek by any stretch of imagination.

Cheers,

Gordon

---

### Post by sandfire on 2010-10-03
I am bumping this again.

Surely there must be someone who can help me resolve this problem, please.

Gordon

---

### Post by dineshs on 2010-10-05
Hope you have a  modem connected via ethernet.Please post the results of the following commands
```
ifconfig -a
```
```
ping 4.2.2.1 -c3
```
Also please ensure that `enable networking' is ticked(rightclick network manager icon on right top of the panel)

---

### Post by sandfire on 2010-10-05
The latest situation is this.

I have cleared Ubuntu 10.04. 

I have installed Ubuntu 9.10. I have made sure all updates in 9.10 are in place. I have then checked internet access with Firfox in Ubuntu 9.10 There is full internet access.

Then...

I upgrade to 10.04 which installs from the internet. It installs including latest updates from the internet. I then check internet access with Firefox in Ubuntu 10.04. There is NO internet access.

Using my laptop with Ubuntu 10.04 installed, I have internet access and can connect to the wireless modem configuration and settings page.

Using my desktop computer 10.04 installed, I cannot connect to the wireless modem configuration and settings page. On my desktop 10.04 was working quite well before the latest updates were installed.

I have twice repeated to re-installation of 10.04 and each time I get the same result. By the time I have cleared the partition, re-installed 9.10, updated 9.10 and upgraded to 10.04 a whole day has been wasted.

Perhaps I would be better to just wait now until 10.10 is available, download the ISO, make a live CD and forget about 10.04.

In my frustration, I started the whole reinstallation process about 5 minutes before I checked this forum. I'll come back to you for help once I have completed installing.

Thank you.

Gordon

---

### Post by krishnandu.sarkar on 2010-10-05
Well...go to your router page(bu default 192.168.1.1 / 192.168.0.1). Then on WAN Connections see it's already configured in bridge mode, change it to PPPoE mode and provide the username and password there.

The advantage is...you won't have to dial internet from any PC, from any OS. Just turn on the router and you'll be connected to internet. :)

---

### Post by tedlux on 2010-10-05
I am having the same problem everything looks fine  . . connected to wireless but still not loading web sites

---

### Post by sandfire on 2010-10-14
Okay, I reverted to V9.10 and I had internet access without any challenges.

Ubuntu 10.10 was on stream so I have installed it. Guess what! No internet Access.

I have spoken to my ISP tech department and they say that:

If I have 10.10 on both computers (Laptop and Desktop) and one computer (Laptop) is
able to access the Wireless Router and connect to the internet, then it cannot be the Wireless
Router.

The fault must be in the Desktop Computer. Are older Wireless networking cards no longer
compatible with Ubuntu 10.04 or 10.10?

If not, what wireless networking card would I be advised to get?

Thanks,

Gordon

---

### Post by spookie41 on 2010-10-17
Same issue here Gateway MX8741 on cox cable wired and wireless thru a lynksys wireless and wired router. After install 10.04 wired ethernet was rock solid, but recently after installing updates, hit and miss. I'm on _wireless running now_, but one thing I've noticed is on the edit connection screen, both the wired or wireless state _never used_, even while I'm on the connection. Secondly I noticed when the wired goes down, on the connections available, _it is grayed out._ I have double checked mac on the wired connection, ticked and unticked IVP6, rebooted in between etc no difference. Deleted and rebuilt it and the same thing several times, right after I rebuilt this last time it was on and hooked up for about an hour, then dropped it, rolling to wireless.  I resorted to two wired connections to see if it was a case of dropping one, no joy. 
_I just networked into the router thru wired, so I'm good to there. _
On a brighter note, tried 10.10 off a flash stick and it immediately saw the home network and the wired. 

Results of ipconfig -a
Link encap: eth0 Ethernet  HWaddr (mac removed by me)
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

So the adapter is there, any ideas? Let me know if you guys want to try any tricks lol, I don't mind working in terminal or whatever.

---

### Post by spookie41 on 2010-10-17
Ok, replaced the cat 5 cable end, ran tests to verify it was right. Threw in the 10.10 on the USB stick and scooted around, solid wired connection. Rebooted back to OS and nadda on wired, thou now I have a firm wired connection showing on top taskbar, neither Firefox nor Opera will load, pidgen is a fail also. 
Does anyone have the Hardware info command for terminal handy? Thanks

---

### Post by dineshs on 2010-10-17
```
sudo lshw -C network
```

---

### Post by spookie41 on 2010-10-17
**Well, I resolved my problem**, quite simple actually. Firestarter was configured for wireless and not for wired connection. I turned the wired connection on by clicking wired connection1 in the connection on the upper right of the task bar. Then I ran the firestarter wizard to configure the connection, and bingo. We're on thru wired. I'm not sure why Firestarter can't be configured to auto switch between the two connections? When I disconnect from wired to wireless, Firestarter stops, shown by the red dot. Hopefully this will help other newbies like me.

Cool thanks!

---

### Post by PokerJoker on 2010-10-23
I've just upgraded to 10.10 from 10.04 by means of Live-CD (Beta) as i couldn't get the network connection (internet only, local network just fine) to work in 10.04.

Here's my problem.
Dualboot system has perfect internetconnection when running Windoze..
On 10.04/10.10, i get a DHCP ip, can access router webpage with FF no problem, can even ping ubuntuforums.org (40ms avg)... so i do have a decent internet connection....
I'm using wired only...

**But:** webpages won't load, also package-manager won't load repositories, traceroute to ubuntuforums.org times-out.....

My first guess would be DNS problems, but tried static ip with valid DNS entries with same results....

Many many problems found, with different causes but not a solution yet to this problem. 
A last remark, my Andriod phone won't work either (wireless) on my home network unless i use static ip. iPhone has no problem on DHCP....

Edit: Just ran the Live-CD on other machine (Dell Latitude notbook) over wireless connection (to same ADSL ISP router) with same result, can ping, can't traceroute/open webpage

---

### Post by PokerJoker on 2010-10-24
My problem solved, had it crossposted in more suitable forum also (sorry) 
Result here: [http://ubuntuforums.org/showthread.php?p=10018683#post10018683]("http://ubuntuforums.org/showthread.php?p=10018683#post10018683")

---

