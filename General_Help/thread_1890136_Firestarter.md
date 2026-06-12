---
title: "Firestarter"
date: 2011-12-02
forum: General Help
---

### Post by UltimateCat on 2011-12-02
Have Ubuntu 10.04 ; Ultimate Edition 2.7My experience with this Operating System is only a little over a year. Connection is established by modem and DSL line w/o phone; using a wireless Linksys Adapter to communicate with the modem. The connection is good with XP Pro. However; Firestarter displays " the device etho is not ready" or " the device pppo is not ready"

Network MGR is not in my Applications nor System.....Could it be that Ubuntu does not recognize the adapter I have?

Went through the Wizard and instructions...Firestarter continues to fail-:confused:...help!

---

### Post by Dangertux on 2011-12-02
> **UltimateCat said:**
> [FONT=Comic Sans MS]Have Ubuntu 10.04 ; Ultimate Edition 2.7[/FONT]
[FONT=Comic Sans MS]My experience with this Operating System is only a little over a year. [/FONT]
[FONT=Comic Sans MS]Connection is established by modem and DSL line w/o phone; using a wireless Linksys Adapter to communicate with the modem. The connection is good with XP Pro. However; Firestarter displays " the device etho is not ready" or " the device pppo is not ready"[/FONT]

[FONT=Comic Sans MS]Network MGR is not in my Applications nor System.....Could it be that Ubuntu does not recognize the adapter I have?[/FONT]

[FONT=Comic Sans MS]Went through the Wizard and instructions...Firestarter continues to fail-:confused:...help![/FONT]

Firestarter is a little bit buggy and out of development -- I would recommend stickign with UFW/GUFW or iptables to control netfilter. However , it is possible that Ubuntu does not recognize your adapter, though it is more likely that UFW and Firestarter are conflicting if you haven't uninstalled UFW. 

Hope this helps.

---

### Post by UltimateCat on 2011-12-02
> **Dangertux said:**
> Firestarter is a little bit buggy and out of development -- I would recommend stickign with UFW/GUFW or iptables to control netfilter. However , it is possible that Ubuntu does not recognize your adapter, though it is more likely that UFW and Firestarter are conflicting if you haven't uninstalled UFW. 
 
Hope this helps.
 Ty now i just have to educate myself on the uninstall-

---

### Post by staf0048 on 2011-12-02
Hop into a terminal and type:

```
sudo iwconfig
```

This will let you know if your network card is powered up and linked to your modem.  Here's an example of my own output.

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Motorola"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:A5:91:92:3C   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:1752   Missed beacon:0

```
***ignore the smilies

Notice, it's a wireless card (wlan0) and is connected to my "Motorola" cable modem.  This should be a start, to at least know if your card is recognized.

If it appears the card is not powered up issue:

```
sudo iwconfig wlan0 up
```
***Note to replace wlan0 with either eth0, wlan1, etc, etc, depending on your personal output.  

One last thing, and I don't mean to be offensive, but if your connection requires a password, remember to connect to your modem with that password.  We can sometimes forget if we have it set automatically on that "other" OS.  :-)

---

### Post by UltimateCat on 2011-12-02
I know if I am not certain typing in command line could cause havoc....ZT, the Manufactuer didn't put a card in- 
Is it wise for me to type in [COLOR=darkslateblue]sudo iwconfig [/COLOR] if it's not a card?

---

### Post by staf0048 on 2011-12-02
> **UltimateCat said:**
> [FONT=Comic Sans MS]Is it wise for me to type in [COLOR=darkslateblue]sudo iwconfig [/COLOR] if it's not a card?[/FONT]

It will be fine, all that command does is list your current configuration.  It does not initialize anything itself, until you issue the "up" part of it.  But even then, it only powers up the adapter.  However, your caution in issuing random commands you've not seen is understood.  Try googleing iwconfig or ifconfig to learn more.  Hopefully it will lead you to a solution.  

All the best,

---

### Post by oldtimer7777 on 2011-12-02
> **UltimateCat said:**
> [FONT=Comic Sans MS]Have Ubuntu 10.04 ; Ultimate Edition 2.7[/FONT]
[FONT=Comic Sans MS]My experience with this Operating System is only a little over a year. [/FONT]
[FONT=Comic Sans MS]Connection is established by modem and DSL line w/o phone; using a wireless Linksys Adapter to communicate with the modem. The connection is good with XP Pro. However; Firestarter displays " the device etho is not ready" or " the device pppo is not ready"[/FONT]

[FONT=Comic Sans MS]Network MGR is not in my Applications nor System.....Could it be that Ubuntu does not recognize the adapter I have?[/FONT]

[FONT=Comic Sans MS]Went through the Wizard and instructions...Firestarter continues to fail-:confused:...help![/FONT]

I really liked UE back when it was at 9.04-10 Ubuntu..  Lately, the whole installation process for regular plain Ubuntu has become much smoother for new users.  You may want to consider upgrading at some point soon because support for that version will probably expire. 

Here is a nice walk-through to install Ubuntu on your system:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

As for your question about Firestarter, I really liked Firestarter in the beginning, but it became too much of a pain in the --- after a while, and I really like GUFW/UFW better now, so you may want to considering installing that instead.  Instructions are in the above walk-through as well.  Goodluck.

---

### Post by UltimateCat on 2011-12-11
:DThank you for your input and giving me the link to follow the Instructions to :
GUFW/UFW....I might install the new version of Ubuntu 11.04 but for now I need to get this network connections problem solved first.

---

### Post by UltimateCat on 2011-12-22
As time has progressed I think ( newbie ) that Firestarter is not the problem and is working fine.  Worked well in the past; summer of 2010

I think what the problem is that the internal realtek RTL8111/8168B is the issue.  By that I mean it needs a driver to work like it should.  I have  been  googling and doing research and finding that a lot of members have had trouble with this internal card. 

 Also, lose my online connection consistently on and off throughout the day and evening.  This has also been other members problems/symptoms as well.


  I'm not going to install the RT73 driver unless my efforts to aid the realtec card fail.

Not sure if I need the firmware either....still learning and having difficulty understanding how Os and other things work. 

 Being a newbie has been (lack of a better word) extreamly frustrating at times and educational as well.  

Hope I can be of assistance to others as I learn more.

Thanks to members who have written to me and have been a help.

Have a safe and Happy Holiday!:)

Sincerely,
UltimateCat

---

