---
title: "Problems after upgrade to ubuntu 10.10"
date: 2010-10-11
forum: General Help
---

### Post by leeg on 2010-10-11
I have just updated to ubuntu 10.10 netbook edition and all went fine until the compunter rebooted and all I have is a pretty purple screen I have managed to get online using my internet button on the keyboard but I have no menu or even a curser apart from when i have my browser open...any ideas:(:confused:

---

### Post by Bow rat on 2010-10-11
Hi!

I had the same issue - I needed to un-install and re-install gnome-session to fix it.

I also had issues with network manager losing my ethernet, mucking up wireless and VPN. I fixed ethernet and wireless again by un-installing and re-installing network manager and am still working on the VPN issue, which appears to be related to strongswan rather than network manager.

Hope this helps & good luck!

Bow rat

---

### Post by meske on 2010-10-13
I had the same issue on an Aspire One netbook.  After upgrade, the netbook interface wouldn't start (pink screen).  I have multiple users on the PC, and I could get into my "classic" desktop no problem, but when I tried another user on the PC, the screen would come on upside down with all the text backwards.  Strangest thing I ever saw.

What I found was that 10.10 automatically installed and enabled the Nvidia drivers, and it didn't remove the UBUNTU-DESKTOP or UBUNTU-NETBOOK packages.  I had to remove those packaged, and removed UNITY as well, then reinstalled UNITY.

I then had to make a change to the custom.conf file to change the default from "une" to "unity" so the netbook edition would show up in the environment list on login.

Took me a while tinkering and restarting to get this all done, but it's finally working.

Not loving the UNITY netbook though, as I haven't found a way to hide the left side quick bar yet.  On a netbook, that takes up just enough pixels to make web browsing a pain as I'm no longer at 1024 wide and I've found that there is a lot of horizontal scroll on certain pages.

---

### Post by Alfafa on 2010-10-15
Hi. About the strongswan problem in Ubuntu 10.10. I stumbled over a  german guy who writes that a work around to the bug is to change the  order of loading the plugins for the charon daemon

So the config should something like this
/etc/strongswan.conf:
         ...
        charon {
                       ...
                        load =  curl ldap aes des sha1 sha2 md5 random x509 pubkey pkcs1 pgp  dnskey pem openssl fips-prf xcbc hmac agent gmp attr kernel-netlink  socket-default farp eap-identity eap-aka eap-md5 eap-gtc eap-mschapv2 nm  dhcp resolve
                       ...
 

 Original found here: [http://mopoinfo.vpn.uni-freiburg.de/node/99](http://mopoinfo.vpn.uni-freiburg.de/node/99)

---

### Post by FishFoot on 2010-10-19
I'm having similar problems but the steps outlined here don't fix my issues.

When I finished the upgrade I got the purple background from 10.04 and my cursor is an "X".  

I tried removing the packages described and re-installing them in different combinations.  I also edited the /etc/gdm/custom.conf file and changed the "une" to "unity".  This also didn't help.

When I kill "X" from a terminal I get presented with a logon screen that I wasn't getting otherwise.  From there I can choose "Ubuntu Desktop Edition (Safe Mode)".  When I do I get what appears to be my prior "desktop", the 10.04 look.  I get a status bar across the top and my system tray returns (so I can at least get wifi up and running through this).

This kind of sucks.  I'm not sure what to do next. 

-Fishfoot

---

