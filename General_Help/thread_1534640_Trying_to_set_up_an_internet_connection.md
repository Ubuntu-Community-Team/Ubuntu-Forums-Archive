---
title: "Trying to set up an internet connection"
date: 2010-07-19
forum: General Help
---

### Post by xalelexx on 2010-07-19
Hi all,
 
Installed Ubuntu 9.10 on my Toshiba laptop (satellite pro 4200).
Trying to set up the dial-up internet connection, but having troubles.
 
Tried to follow this method:
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html/comment-page-2#comment-41030](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html/comment-page-2#comment-41030)
 
I have been unable to get my connection up and running using the three different methods on this page. Here are the problems:
 
**Networking Option:**
No Networking option under Administration
 
**Using pppconfig:**
“pon Clear.net” // Nothing happens
“plog”
In file /etc/ppp/peers/provider: unrecognized option ‘/dev/modem’
pppd 2.4.5 started by alexander, uid 1000
Can’t get terminal parameters: Input/output error
Script /usr/sbin/chat -v -f /etc/chatscripts/Clear.net finished (pid 1575), status = 0×2
Connect script failed
Exit
 
**Using gnome-ppp:**
"sudo apt-get install gnome-ppp"
E: Couldn’t find package gnome-ppp
 
How can I set up my internet connection?
 
 
 
P.S.
I looked at the suggestions in this thread, but couldn't see a solution for a dial-up connection.
[http://ubuntuforums.org/showthread.php?t=1413950&highlight=set+internet+connection](http://ubuntuforums.org/showthread.php?t=1413950&highlight=set+internet+connection)

---

### Post by kennedyvelez on 2010-07-19
try sudo pppoeconf on gnome terminal...

---

### Post by xalelexx on 2010-07-19
NO INTERFACE FOUND
"Sorry, no working ethernet card could be found. If you do have an interface card which was not autodetected so far, you probably wish to load the driver manually using the modonf utility. Run modconf now?"
 
Yes => modconf: not found

---

### Post by xalelexx on 2010-07-19
Is there anything else that I could try in order to get my internet connection up and running?

---

### Post by xalelexx on 2010-07-19
I have nothing else to do today... any help would be appreciated...

---

### Post by cym104 on 2010-07-19
seems like ur 910 is not recognizing your net card. u can either go to ur vendor's site to download a driver or switch to 1004 and see if it can recognize ur net card.

---

### Post by xalelexx on 2010-07-19
This laptop is old, so probably no drivers available. Will try to switch to 1004

---

### Post by xalelexx on 2010-07-19
> **cym104 said:**
> seems like ur 910 is not recognizing your net card. u can either go to ur vendor's site to download a driver or switch to 1004 and see if it can recognize ur net card.
 
How do I switch to 1004?

---

### Post by cym104 on 2010-07-19
just the samw way u installed 910~~

---

### Post by xalelexx on 2010-07-19
Do you mean download 10.04 update?
Isn't that 700mb or so? Not really a viable download on dial-up.
 
Surely there must be a way to get this working...

---

### Post by cym104 on 2010-07-19
err....well, try run "ifconfig" in a terminal and post the output.
and how's ur modem connected to ur comp? lan or usb?
if lan, then ur 1st have to m ake sure ur comp's net card works.
if usb, then u'll have to install a driver for ur modem.

---

### Post by xalelexx on 2010-07-19
The modem is in-built

---

### Post by xalelexx on 2010-07-19
[FONT=Courier New]Link encap:Local Loopback[/FONT]
[FONT=Courier New]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT]
[FONT=Courier New]inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=Courier New]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT]
[FONT=Courier New]RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Courier New]TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Courier New]collisions:0 txqueuelen:0[/FONT]
[FONT=Courier New]RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)[/FONT]

---

### Post by cariboo on 2010-07-19
[This]("https://help.ubuntu.com/community/DialupModemHowto") may be a better place to get started. First you have to make sure your modem is detected and working, before doing anything else.

---

### Post by cym104 on 2010-07-19
> **xalelexx said:**
> The modem is in-built
 i guess that means it's a 56k telephone modem?
meh that's so old school....
then u really need to go find a driver for it...no other way around. 
good luck to u bro,coz u do need it.

---

### Post by xalelexx on 2010-07-19
My god so much hassle to do something that takes 2 mins in windows T_T

---

### Post by xalelexx on 2010-07-20
[FONT=Courier New]NAME:="Communication controller: Agere Systems 56k WinModem "[/FONT]
[FONT=Courier New]CLASS=0780[/FONT]
[FONT=Courier New]PCIDEV=11C1:0441[/FONT]
[FONT=Courier New]SUBSYS=1179:0001[/FONT]
[FONT=Courier New]IRQ=3[/FONT]
[FONT=Courier New]IDENT=Agere.DSP[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Arial]Now what?[/FONT]

---

### Post by xalelexx on 2010-07-20
Ok I downloaded martian driver for agere systems modem. Here is where I'm up to:
 
Load kernel module and launch user space driver 
# modprobe martian_dev# martian_modemLeave it running and you can access the modem by /dev/ttySM0 file.
 
Ok what does this mean?
 
My last command "sudo martian_modem"
martian: info: Your port is /dev/ttySM0
 
Then I typed /dev/ttySM0 and pressed enter but nothing happened.
 
What to do now?

---

### Post by xalelexx on 2010-07-20
OK now what?

---

### Post by dineshs on 2010-07-20
please ref to this link by alexfish,
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
and post the output of
```
dmesg | grep -e "modem" -e "tty"
```

---

### Post by xalelexx on 2010-07-20
> **dineshs said:**
> please ref to this link by alexfish,
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
and post the output of
```
dmesg | grep -e "modem" -e "tty"
```
 
```
dmesg | grep -e "modem" -e "tty"
```
 
[FONT=Courier New][    0.001854] console [tty0] enabled[/FONT]
[FONT=Courier New][    1.666480] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A[/FONT]
[FONT=Courier New][    1.667931] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A[/FONT]
[FONT=Courier New][ 1761.806986] martian_modem is attached.[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Times New Roman]Thanks much[/FONT]

---

### Post by xalelexx on 2010-07-20
martian_modem is still running, should I stop it?

---

### Post by dineshs on 2010-07-20
Can you send a private message to alexfish or pdc? They may be able to help you.As far as I know most of the winmodems wont work in linux(ref [http://ubuntuforums.org/showthread.php?t=1292578](http://ubuntuforums.org/showthread.php?t=1292578))

---

### Post by xalelexx on 2010-07-20
Sigh... I wish I had checked this before I wiped off Windows and put on ubuntu T_T

---

### Post by xalelexx on 2010-07-20
Is it straightforward to set up wireless internet so I can at least connect at university?

---

### Post by xalelexx on 2010-07-20
> **dineshs said:**
> Can you send a private message to alexfish or pdc? They may be able to help you.As far as I know most of the winmodems wont work in linux(ref [http://ubuntuforums.org/showthread.php?t=1292578)](http://ubuntuforums.org/showthread.php?t=1292578))
 
Thanks for your help dineshs

---

### Post by dineshs on 2010-07-20
1)dialup-Most of the external serial  modems will work in ubuntu.I use an old D-link DFM 560ES when my broadband DSL fails(I have heard USB modems like US robotics also work)
2)Regarding wireless 
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
3)Most of the ethernet cards are supported .So you can use broadband via ethernet

---

### Post by xalelexx on 2010-07-20
> **dineshs said:**
> 1)dialup-Most of the external serial modems will work in ubuntu.I use an old D-link DFM 560ES when my broadband DSL fails(I have heard USB modems like US robotics also work)
2)Regarding wireless 
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
3)Most of the ethernet cards are supported .So you can use broadband via ethernet
 
 
I have a PCMCIA DWL-G630 H/W Ver.: D1 F/W Ver.:4.10
 
This isn't listed here:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

### Post by kennedyvelez on 2010-07-21
If your laptop is old, it should be recognize by your karmic. It means if your laptop was famous in the past, somehow, it should be remember in the repositories. Speaking of repositories, finding an old ethernet driver requires the right repositories... They're right, you should download its driver manually...
Don't quit.

---

### Post by frank cox on 2011-09-08
I know this is an old thread but the cheap USB winmodems on ebay work well in Linux and they are not obtrusive even on a laptop. Many Dell computers have winmodems that you can get free high speed drivers for as they were offered with Linux .
For 12.00 why beat your head into the wall?
The latest threads about Gnome-PPP have some good info. There are a few commands that if you know to use them will allow you to set up one of those cheap modems in less than 20 minutes,

---

