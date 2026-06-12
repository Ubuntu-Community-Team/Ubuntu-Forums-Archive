---
title: "Slow Wi-Fi on 12.04"
date: 2012-05-09
forum: General Help
---

### Post by galdikas on 2012-05-09
<snip>

With rant being over here is the situation.

I have installed dual boot on windows 7. I know that none of this slowness has to do anything with my hardware. Because I made a live USB from same iso file and ran it on different laptop. An exact same problem existed. (it works grand with wired connection). So it is probably to do with router.


My network driverL ath9k_htc.
My router: ZyXEL P-660HW-D1

Here is my question on askubuntu.com for more info: [http://askubuntu.com/questions/134110/very-slow-wireless-connection-unrelated-to-power-management-using-netgear-n15#comment159611_134110](http://askubuntu.com/questions/134110/very-slow-wireless-connection-unrelated-to-power-management-using-netgear-n15#comment159611_134110)
Most common problem seems to be that automatic power management thing. However for me it is off by default.

---

### Post by smurphy on 2012-05-09
FYI - in any Hotel I am, using Zyxel routers/AP's, I have issues accessing the network. Why ? No idea.
Works under windows, but not under KUbuntu.

I noticed, that restarting the Zyxel router/AP solves the issue for about 12 Hours. After that, it has to be restarted.

Eventually you should update the firmware of your Zyxel router/AP, or adapt the configuration.

---

### Post by TBABill on 2012-05-09
Could you open a terminal and enter some commands, then copy/paste into some form of doc so you can paste that info back here? That way you won't have to wait forever for page loads.
 
```
lspci | grep Network
``` That will tell us what sort of wireless you actually have. Without that info any troubleshooting is wasteful of time.
 
```
lsmod
```Will tell us what drivers you have active currently.
 
Edit: I had a similar problem with an Atheros AR9287 and the problem was I had to make a change to nohwcrypt setting. If you have an AR928x model, perhaps search for threads related to see if they make a difference. Just note once you make the change you will need to restart to test in order to reload the .conf file settings. May not be your issue, just offering to save you some time just in case.

---

