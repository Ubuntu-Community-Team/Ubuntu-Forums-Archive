---
title: "Is there any decent network management software out there?"
date: 2011-11-18
forum: General Help
---

### Post by agentfortyseven on 2011-11-18
Hello guys,
From my personal experience I'd say Network Manager is the best so far. I've tried Wicd and it would never let me connect to my wifi (it gives an error BAD PASSWORD) although it would allow me internet access using an ethernet cable. KNetworkManager would never startup after installation. As for RutilT WLAN manager there's nothing like an "automatically connect" thing.
I use Ubuntu 10.04. Can you guys suggest me some good network management software or at least help me out with the aforementioned issues. I had high expectations from Wicd but it was such a big let down.

---

### Post by Zill on 2011-11-19
agentfortyseven:  The problem is in the lucid wicd-1.7 package and a workaround is to downgrade wicd to version 1.6 (karmic).

Firstly, ensuring that you have a working ethernet connection, completely remove all network-manager packages as network-manager conflicts with wicd.

Then downgrade wicd to version 1.6 as described in comment #9 of [bug report #540070]("https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070").

Hopefully, you will then have a working version of wicd and can use your wifi.

Although I initially experienced the same problem as you with wicd-1.7 on lucid, "cured" by downgrading wicd to 1.6, I found that a later kernel upgrade allowed me to install and successfully run wicd-1.7.

I am currently running wicd-1.7 on lucid with kernel 2.6.32-35-generic #78-Ubuntu).  I would like to say that it performs faultlessly but I must admit to still seeing a (very!) occasional "bad password" messaqe when connecting to my wpa wifi.  However, it always connects OK on the second try.

---

### Post by agentfortyseven on 2011-11-20
Thanks a lot buddy. I just cannot figure out how to add karmic repositories. Can you help me out with this.

---

### Post by Zill on 2011-11-20
> **agentfortyseven said:**
> Thanks a lot buddy. I just cannot figure out how to add karmic repositories. Can you help me out with this.
I had forgotten that Ubuntu 9.10 Karmic Koala went end-of-life on April 30, 2011 so the karmic repos have now been removed.  My apologies.
However, it should still be possible to use the old karmic packages - they just take some finding. ;-)

I suggest you go to [wicd 1.6.1-3ubuntu1 (i386 binary) in ubuntu karmic]("https://launchpad.net/ubuntu/karmic/i386/wicd/1.6.1-3ubuntu1") on Launchpad.  Find the "Downloadable files" link on the right hand side entitled [wicd_1.6.1-3ubuntu1_all.deb]("http://launchpadlibrarian.net/31314878/wicd_1.6.1-3ubuntu1_all.deb") and click on this link and choose to *save* the file so that you can install it later.

Then, using Synaptic, remove *all* network-manager packages and the wicd-1.7 package.

Click on your newly-downloaded wicd-1.6 file and use GDebi to install the package.  Configure as required and, hopefully, this will now work satisfactorily, without the "bad password" error message.

To ensure that wicd-1.6 is not "upgraded" to wicd-1.7 it is necessary to "lock" the package.  This is easily done using Synaptic.  Just highlight the package, then select "Lock Version" from the "Package" menu at the top.

---

### Post by 3rdalbum on 2011-11-20
What's wrong with Network Manager? What makes it "not decent", and what features do you want?

---

### Post by Zill on 2011-11-20
> **3rdalbum said:**
> What's wrong with Network Manager? What makes it "not decent", and what features do you want?
My understanding is that Network Manager is primarily designed as a user-based GUI tool to allow laptops and netbooks to quickly connect to a wifi hotspot.  As such, it is not ideal for desktops and/or servers that may need a more "permanent" connection.  In particular these applications may require network connectivity to be automatically "up and running" on boot and to remain connected whether a user is logged in or not.

In such cases I prefer to use either a hard-configured /etc/network/interfaces file (for a wired connection) or the wicd network manager (for wireless connections).

---

### Post by agentfortyseven on 2011-11-20
> **Zill said:**
> 
I suggest you go to [wicd 1.6.1-3ubuntu1 (i386 binary) in ubuntu karmic]("https://launchpad.net/ubuntu/karmic/i386/wicd/1.6.1-3ubuntu1") on Launchpad.  Find the "Downloadable files" link on the right hand side entitled [wicd_1.6.1-3ubuntu1_all.deb]("http://launchpadlibrarian.net/31314878/wicd_1.6.1-3ubuntu1_all.deb") and click on this link and choose to *save* the file so that you can install it later.

Then, using Synaptic, remove *all* network-manager packages and the wicd-1.7 package.

Click on your newly-downloaded wicd-1.6 file and use GDebi to install the package.  Configure as required and, hopefully, this will now work satisfactorily, without the "bad password" error message.

To ensure that wicd-1.6 is not "upgraded" to wicd-1.7 it is necessary to "lock" the package.  This is easily done using Synaptic.  Just highlight the package, then select "Lock Version" from the "Package" menu at the top.

Thanks mate I'm sure gonna give it a try.

---

### Post by agentfortyseven on 2011-11-20
> **3rdalbum said:**
> What's wrong with Network Manager? What makes it "not decent", and what features do you want?

Network manager (wifi) hangs up on me at times and I usually see a window poppin up asking me to "connect". But I just cannot.. nothing wrong with the password. But it would connect later on when it feels like.. can take upto an hour or two or maybe ten minutes.. My NM is quite moody you see.
Nothing wrong with my router either.

EDIT: I usually but not always encounter this problem when I resume my laptop from sleep mode.

---

### Post by agentfortyseven on 2011-11-23
Got Wicd 1.7 working yay :) and its just awesome. f**k network manager :evil: I know I'm contradicting my earlier statement. But I have realized that NM can't even be compared to Wicd as far as the performance is concerned. All it needs is a sleek interface like NM.

---

