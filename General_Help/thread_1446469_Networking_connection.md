---
title: "Networking connection"
date: 2010-04-04
forum: General Help
---

### Post by dimitriv on 2010-04-04
Hi

My DSL network connection is failing to connect after an upgraded from 8.1 to latest production build. I have tested the modem & ISP connection, they are fine.

**Please advise any steps to fix or troubleshoot.**

Looking in the syslog after failed attempt to connect it shows NetworkManager reporting 

*<WARN> pppd_timed_out(): Looks like pppd didn't initialize our dbus module*

&

*Marking connection 'ISP1' invalid*

Under the ISP1 connection settings, I have tried All and one at a time of the PPP Settings 'Configure Methods'

I need to get the Internet established ugently so would welcome any suggestions.

Many thanks

---

### Post by Nisal on 2010-04-04
its DSL right ? well i dont know about that but i had that problem with mobile broadband and when i configure with google DNS it works fine

---

### Post by dimitriv on 2010-04-04
Thanks for the sugggestion I tried entering a DNS Server (wasn't sure what to put in 'Search domains', and wasn't sure about the 'Routes' entry.

This used to work, what's broken it/how to fix?

Thanks

---

### Post by shikhar_sharma on 2010-04-04
dude u r using dsl or pppoe??because if u r using pppoe then u gotta do pppoeconf to configure ur connection.and then pon dsl-provider to trigger it.plz clarify wat type of connection u use??

---

### Post by dimitriv on 2010-04-04
> **shikhar_sharma said:**
> dude u r using dsl or pppoe??because if u r using pppoe then u gotta do pppoeconf to configure ur connection.and then pon dsl-provider to trigger it.plz clarify wat type of connection u use??

Hi, I'm using PPPOE which shows under the DSL tab. On 8.1 I didn't have to manually enter some config (just a/c & password), what config should I add?

Thanks very much

---

### Post by dimitriv on 2010-04-05
Please, if anyone has any ideas about this please advise i urgently need to get this resolved. Thank you

---

### Post by shikhar_sharma on 2010-04-11
ok all you need to do is go to terminal and type
sudo pppoeconf
this will bring up a wizard.follow the wizard and dont change any settings that u dont understand.just leave the default values.Then it will ask u for user name and password.after entering all the details you can trigger the connection by
sudo pon dsl-provider
and terminate the connection by
sudo poff

Note:if you are using DHCP to get ur ip then this will work but if you have static ip then you need to create a connection in wired connection which by default is eth0.enter you ip over there manually and then connect with that connection.once it says connection established then trigger the pppoe connection.This was much easy in 8.1

anywayz enjoy

---

### Post by efflandt on 2010-04-11
You said you "upgraded" from 8.1.  Did you install 9.10 from scratch, or did you upgrade 8.1 to 9.04 and then to 9.10?

---

