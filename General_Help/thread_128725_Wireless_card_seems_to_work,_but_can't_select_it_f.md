---
title: "Wireless card seems to work, but can't select it for connection!"
date: 2006-02-12
forum: General Help
---

### Post by playmesumch00ns on 2006-02-12
I've successfully used my wireless card on my sister's network before I got broadband set up at home.

Now I have a linksys g router at home and I can't get the internet going (works fine on windows).

If I go into networking and edit the properties for my wireless card, eth1, I can select my SSID from a list of ones I recognise from the local area (so it's successfully scanning). I put in my ascii WEP key (tho I think the router uses WPA, should that make a difference?) and select DHCP, then activate it. All seems OK, no errors or anything.

Now if I go to the little connection icon in the taskbar at the top-right of the screen, the only connection I can select is the loopback (lo).

Has anyone experienced anything similar to this?

Cheers,

p

---

### Post by Jason_25 on 2006-02-12
I had the same problem and it has the most simple solution.  Just type the name of the interface in the box.  It should magically appear.

---

### Post by playmesumch00ns on 2006-02-12
Argh I was so excited!

Funnily enough when I logged back into ubuntu to try it, eth1 was suddenly on the connections menu... but now it just shows "disconnected" :(

I'm typing this from ubuntu, connected using eth0 (lan cable into the router). iwconfig gives me this:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"linksys"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

sit0      no wireless extensions.

```

which looks pretty bad to me.

Any ideas as to what sort of thing I might try next to get it working?

cheers

---

### Post by njzillest on 2006-02-12
to tell if you have anyconnections go to the terminal and type in iwconfig (its like ipconfig on windows) It should show you the ESSID that you are connected too. Now The little icon at the top that siad it was connected to the LO, shows wether your connected. Press on the icon, and on the space that sais LO, type in ETH1 (or what ever your wireless cards name is) That will give you the status of the ETH1, or what ever input you typed.


As for the disconnected figure, either go to system-Administration-Networking, or click on the interent status, change it to eth1 one and click configure at the bottom. 

Both take you to the networking. Once your there, on the right it should say Activate. Click on that (make sure you have selcted the appropriate card) Next click on properties and make sure at the top the little box is checked "enable this connection" 


exit all, and have fun.



if that does not work, tell me your internet card and ill guide you from there...

---

### Post by playmesumch00ns on 2006-02-12
Thanks for the help :)

I've already tried doing as you suggested. I also tried logging on to a couple of unsecured local networks (naughty I know but it didn't work anyway :() to check that it wasn't a problem with my encryption. 

Anyway, when I activate the eth1 interface it shows the "activating interface eth1" progress window for a long time, then that closes and all seems ok. But trying to select eth1 from the connection manager just gives me the disconnected warning" and the signal strength meter shows 0%.

I'm on a dell inspiron 9300 laptop with an Intel PRO/Wireless 2200BG. The router is a LinkSys WAG354G modem & router (wireless G).

As I mentioned in my first post, it has worked before on another network.

I also tried installing both wifi-radar and kwifimanager.

wifiradar picked up all the local networks, and when I created a profile for mine, specifying just the key and dhcp, wifi-radar says it connected fine (although I still couldn;t get the connection manager to do anything different).

kwifimanager wouldn't connect properly tho, saying i had a signal strength of 0% --although I coulnd't see a way of putting in my key with this app.

Next time I logged in my os was borked... my session was failing immediately somewhere in the tcp code. So now I'm trying from a fresh install, exactly the same behaviour :(

---

