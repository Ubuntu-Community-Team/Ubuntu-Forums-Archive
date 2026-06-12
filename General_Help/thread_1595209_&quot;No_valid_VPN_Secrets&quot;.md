---
title: "&quot;No valid VPN Secrets&quot;"
date: 2010-10-13
forum: General Help
---

### Post by altjx on 2010-10-13
From my laptop I use at work, I exported the ".pcf" file I use with Cisco VPN Client. 

I downloaded vpnc using Ubuntu 10.10, imported that pcf file (all of the settings were there). Tried to connect, and it gives me the error saying 

The VPN Connection 'Work VPN' failed because there were no valid VPN secrets..

What the hell?

---

### Post by vkmita@gmail.com on 2010-10-15
In mine case it successfully works while I'm configuring vpn in vpnc.conf and launching vpnc from console, but fails with the same error for any tries over gnome network plugin

---

### Post by ragtag on 2010-10-15
I got the same error when using OpenVPN in Ubuntu 9.10, so this fix may be irrelevant, but might just work. It had to do with NetworkManager's access to the keychain, and not OpenVPN directly. Here are the steps I used to get around it.

1. Open VPN Connectinos > Configure VPN from the Network applet.
2. Choose Edit on your VPN connection.
3. Change type to "Password with Certificate" (we weren't using passwords, but you had to do this anyway).
4. Enter anything you like in the username and password fields. It's not used.
5. Hit Apply, and try to reconnect to the VPN.
6. When NetworkManager asks for access to the keychain, press DENY.
7. When asked for a password, just enter anything, and check the Save in keycahin checkbox, and hit OK.
8. Press Always Allow when asked about saving to the keychain afterewards.

---

### Post by vkmita@gmail.com on 2010-10-15
> **vkmita@gmail.com said:**
> In mine case it successfully works while I'm configuring vpn in vpnc.conf and launching vpnc from console, but fails with the same error for any tries over gnome network plugin

Update: Solved with help of: [http://ubuntuforums.org/showpost.php?p=7542821&postcount=4](http://ubuntuforums.org/showpost.php?p=7542821&postcount=4)

---

### Post by suw on 2010-10-23
Open "Password and Encription keys" (seahorse) and delete the "VPN Cert pass secret ..." for your openvpn.
Re-connnect your vpn and you-re done.

I've had the same problem, usually after major upgrades (9.4 to 10.4, 10.4 to 10.10 etc)

---

