---
title: "Suddenly lose"
date: 2011-02-21
forum: General Help
---

### Post by Quarkrad on 2011-02-21
Running 10.04.  For some reason, starting today, I have no internet connection unless I run this command in terminal -   **sudo dhclient eth0** .  I have a hard wired ethernet connection on a Desktop PC with a static IP address (there are a number of devices in the house) and it has been running 100% for months and months.  Why suddenly do I have to enter this command to get connection?   When I switch on I get a connection in that when I click on the Top Panel icon and right click *Connection Information* it tells me I have an active connection to my router on the normal IP address.  I cannot ping the router and Firefox says Server not found.  After **sudo dhclient eth0** everything works - what has happened since yesterday evening and this morning to stop what has been 100% for months?

---

### Post by Quarkrad on 2011-02-22
Bump - still the same (next day).

---

### Post by Clever_Username on 2011-02-22
I wonder, is your static IP listed in the dhclient.conf.... Wait, of course it is, otherwise you wouldn't get it when you fired up the client. 
Maybe it's a lease issue with the IP. Seems like dhclient would be for Dynamic ips. 
Hopefully one of the pro's can jump in here

---

### Post by Clever_Username on 2011-02-22
I just found [this]("http://ubuntuforums.org/showthread.php?t=743860") link. Hopefully it helps.

And another [link]("http://superuser.com/questions/151936/ubuntu-i-need-to-run-sudo-dhclient-eth0")

---

### Post by Quarkrad on 2011-02-22
Thanks;  what seems odd to me is that nothing has changed in my set up apart from it now will not connect or ping the router.  I am with TalkTalk - a standard ISP - and Ubuntu has just worked *out of the box* on this machine/configuration since 8.04.  If I had been *playing* perhaps I could understand but something has happened outside me doing anything. Very strange.

---

### Post by scheuri on 2011-02-22
Hi there

If I understand correctly, you use a router. Is that correct?

So, let us know a few things, please:
1) What fix IP did you give your computer (which it does not have anymore apparently)
2) what IP does it get when you use the dhclient?


I had the same issues back with 6.06 and, if I recall correctly, with 6.10.
For some reason, which I do not know, it kept forgetting that I gave the computer a fix IP address in my LAN. I was unable to ping my router/gateway or to the outside (using IP instead of URL).
As fast as it appeared, it was gone as well. So I am unable to give you a hint about it.

Fact is, try to update (if possible and necessary) and check your configuration about your fixed IP again. Maybe you have to re-do it again?

Thanks and good luck
scheuri

---

### Post by Quarkrad on 2011-02-22
Sorted - I deleted the 'connection' via the Top Panel network icon/Edit Connections and made a new one with the same settings.  Rebooted and got internet connection straight away.  I guess somethings are not worth the effort of trying to find out why they happen (if they are a one off) - better to re-install/set up if it fixes the issue.  Thanks.

---

