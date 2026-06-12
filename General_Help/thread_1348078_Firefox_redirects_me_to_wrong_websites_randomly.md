---
title: "Firefox redirects me to wrong websites randomly"
date: 2009-12-06
forum: General Help
---

### Post by Slaskie on 2009-12-06
I am using Kubuntu 9.10 with Firefox installed, and lately some strange things have been happening: I type in a url such as google.com and firefox takes me to a previously visited site, such as facebook.com, although it says [www.google.com](www.google.com) in the address bar. This can happen with any site and it becomes frustrating when firefox shows me random sites instead of the ones that I want to go to. I fix this by clearing the cache then restarting my computer. Please help me fix this problem, thanks! :)

---

### Post by japadamaray on 2009-12-16
I have this exact same problem and it happens in all my browsers, Firefox, Google Chrome, even w3m and they all take me to the same wrong page!

---

### Post by synapsys on 2009-12-16
Sounds like a problem with DNS. Maybe try using a different DNS server?

---

### Post by viljun on 2009-12-16
> **synapsys said:**
> Sounds like a problem with DNS. Maybe try using a different DNS server?

Yes, feels like it. Rebooting may help. If not try for example this:


   1. In the System menu, click Preferences, then click Network Connections.
   2. Select the connection for which you want to configure Google Public DNS. For example:
          * To change the settings for an Ethernet connection, select the Wired tab, then select your network interface in the list. It is usually called eth0.
          * To change the settings for a wireless connection, select the Wireless tab, then select the appropriate wireless network.
   3. Click Edit, and in the window that appears, select the IPv4 Settings tab.
   4. If the selected method is Automatic (DHCP), open the dropdown and select Automatic (DHCP) addresses only instead. If the method is set to something else, do not change it.
   5. In the DNS servers field, enter the Google Public DNS IP addresses, separated by a space: 8.8.8.8  8.8.4.4
   6. Click Apply to save the change. If you are prompted for a password or confirmation, type the password or provide confirmation.
   7. Test that your setup is working correctly; see Testing your new settings below.
   8. Repeat the procedure for additional network connections you want to change.

If your distribution doesn't use Network Manager, your DNS settings are specified in /etc/resolv.conf.

---

### Post by japadamaray on 2009-12-18
Thanks guys, i think this fixed my problem.

---

### Post by natravis on 2009-12-18
Good to know that it fixed your issue and this should be a good reference thread for future users. If your issue is resolved, make sure to mark the thread solved using the thread tools menu at the top. Thanks!

---

### Post by zgqcliff on 2009-12-20
I have the same problem under ubuntu too. But now it has been modified. Thanks guys!

---

