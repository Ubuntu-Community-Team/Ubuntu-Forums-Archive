---
title: "SAMBA.. Why does it not work?"
date: 2009-07-26
forum: General Help
---

### Post by xenogia on 2009-07-26
Hey Guys,

I installed Samba as following (sudo apt-get install samba) and also installed the samba-config-util.

Anyhow, I shared the drives and reset samba, and when I go into windows network it says it cannot detect and says the following:

Failed to retrieve share list from server

I honestly don't know what I am doing wrong? Any help would greatly be appreciated.

---

### Post by HappyFeet on 2009-07-26
[Setting up samba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by Iowan on 2009-07-26
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a good How-To.  The How-To author (**dmizer**) also mentions:> **dmizer said:**
> The "Failed to retrieve share list from server" error is almost always firewall related. Try installing GUFW (via Synaptic Package Manager) and disabling the firewall in System > Administration > Firewall configuration.

Also, check Windows to make sure that no anti-virus or firewall is interfering on that end either.

---

### Post by xenogia on 2009-07-28
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a good How-To.  The How-To author (**dmizer**) also mentions:

Thanks for your help, this helped out a lot :)

---

