---
title: "Wifi not working after upgrade to Lucid 10.04"
date: 2010-05-08
forum: General Help
---

### Post by peterc150 on 2010-05-08
I have just upgraded from Kubuntu 9.10 (Karmic) to Kubuntu 10.04 (Lucid).  I did the upgrade online using KpackageKit and it completed without any problems.

After the upgrade I cannot connect using wifi with WPA2 encryption which was working before the upgrade.

KNetworkManager keeps putting up a dialogue box "Secrets for xxxx" displaying the password for the wireless access point.  Clicking OK I then get the status "Configuring inteface" but it does not connect.  Eventually the dialogue box "Secrets for xxxx" reappears.

I installed the **b43-fwcuttter - 1:012build1 (i386)** package using KpackageKit and was able to connect via wifi once, but not again.  This also resulted in KDE crashing several times and dropping out to a command prompt login.  The KDE crash has stopped after I removed the fwcutter package.

Any suggestions on how I can get wifi working?

---

### Post by kio_http on 2010-05-08
> **peterc150 said:**
> I have just upgraded from Kubuntu 9.10 (Karmic) to Kubuntu 10.04 (Lucid).  I did the upgrade online using KpackageKit and it completed without any problems.

After the upgrade I cannot connect using wifi with WPA2 encryption which was working before the upgrade.

KNetworkManager keeps putting up a dialogue box "Secrets for xxxx" displaying the password for the wireless access point.  Clicking OK I then get the status "Configuring inteface" but it does not connect.  Eventually the dialogue box "Secrets for xxxx" reappears.

I installed the **b43-fwcuttter - 1:012build1 (i386)** package using KpackageKit and was able to connect via wifi once, but not again.  This also resulted in KDE crashing several times and dropping out to a command prompt login.  The KDE crash has stopped after I removed the fwcutter package.

Any suggestions on how I can get wifi working?

Have you ignored, any kde wallet prompts that came up?

Also if you want to get default lucid, you can delete the kde settings folder. You documents, files and programs will stay, just KDE settings will default

open konsole (not root)
type
```
rm -rf .kde
```

---

### Post by kio_http on 2010-05-08
Also could you please sate what wireless adapter your pc uses.

---

### Post by peterc150 on 2010-05-08
I have entered the KDE wallet password correctly.  The wifi card is integrated with the Netbook.  In Windows the adapter shows as 802.11bgn 1T@R Mini Card Wireless Adapter, with the driver provided by Ralink Technology Corp.

Using iwconfig in Kubuntu the device is listed as RT2860.  Using "lspci | grep Network" the adapter shows as: Network Controller: Ralink RT2860.

---

### Post by kio_http on 2010-05-08
> **peterc150 said:**
> I have entered the KDE wallet password correctly.  The wifi card is integrated with the Netbook.  In Windows the adapter shows as 802.11bgn 1T@R Mini Card Wireless Adapter, with the driver provided by Ralink Technology Corp.

Using iwconfig in Kubuntu the device is listed as RT2860.  Using "lspci | grep Network" the adapter shows as: Network Controller: Ralink RT2860.

I know the card you are referring to. Its very odd because so far this card was supposed to work perfectly. Submit the bug for knetworkmanager in lucid. Mention in the bug-report that you upgraded Kubuntu. Else we may find "unable to reproduce this bug" as result;)

---

### Post by peterc150 on 2010-05-09
I was able to connect briefly again (once) then it dropped out and the error kept repeating.  

I have attempted to file a bug report 3 times now and get a Timeout error, Sorry something just went wrong in Launchpad.   Not a good experience so far, I think I will give up on Lucid.

---

### Post by myjess on 2010-05-09
Look for bugs on rt2860 ralink wifi adapters, your's may be the same problem.

Bug 469XXX I think has something to do with this, or search for my username in the bugs section, you will get the original bg id from my posts.

Rgds.

---

### Post by peterc150 on 2010-05-09
Thanks.  Yes, it looks like this error is fairly common.  It seems an out of date Ralink driver may be the issue [[link]]("http://us.generation-nt.com/bug-574766-2-6-32-3-686-no-wpa-ralink-rt2860-works-upstream-driver-though-help-195840221.html"). 

Its not good that wifi & WPA2 works fine with 9.10 and not under 10.04.  Not enough regression testing apparently.  No easy fix in site so I will either revert to 9.10 (full reinstall) or give Mint a try.

---

### Post by peterc150 on 2010-05-09
This appears to be the same bug: [[link]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575402")

---

### Post by peterc150 on 2010-05-14
Here is a manual fix for this bug.  It involves recompiling RT2860 kernel drivers for Ralink adapter and installing them.  It is tedious but works.

[http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html)

---

### Post by benjaminvitamin on 2011-08-16
Also if you want to get default lucid, you can delete the kde settings folder. You documents, files and programs will stay, just KDE settings will default

open konsole (not root)
type
```
rm -rf .kde
```[/QUOTE]

 Uhm. Please don't ever recommend that. There is important stuff in .kde . All emails for example when using kmail.

---

