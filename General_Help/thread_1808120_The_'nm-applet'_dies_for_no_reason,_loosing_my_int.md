---
title: "The 'nm-applet' dies for no reason, loosing my internet, I tried other Solved posts!"
date: 2011-07-19
forum: General Help
---

### Post by ahears on 2011-07-19
**Here is the start-up output:**

> 

** Message: applet now removed from the notification area

** (nm-applet:29335): WARNING **: Invalid connection /system/networking/connections/1: 'NMSettingConnection' / 'type' invalid: 3
** Message: applet now embedded in the notification area
** (nm-applet:29335): DEBUG: old state indicates that this was not a disconnect 0


**Here is the crash output:**

> 
** (nm-applet:5900): DEBUG: foo_client_state_changed_cb
** (nm-applet:5900): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:5900): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** Message: Caught signal 15, shutting down...
The 'nm-applet' application (part of the network manager) dies on its own and I can't seem to track down why. Please help.

---

### Post by cariboo on 2011-07-19
This isn't a security question, moved to General help.

---

### Post by ahears on 2011-08-02
> **ahears said:**
> **Here is the start-up output:**

**Here is the crash output:**

The 'nm-applet' application (part of the network manager) dies on its own and I can't seem to track down why. Please help.

I am marking this thread as SOLVED because I have found that when using software called PREY ([http://preyproject.com/](http://preyproject.com/)) that this will interfere with the nm-applet while the WiFi Auto connect is turned on (in the PREY Program). I have disabled the Wifi Autoconnect feature and all of the mysterious nm-applet crash problems have ceased to exist.

---

### Post by tredegar on 2011-08-02
> I have disabled the Wifi Autoconnect feature [*in **prey***] and all of the mysterious nm-applet crash problems have ceased to exist.
You just need to be aware that **prey** may not now work as you would like or expect.

Please test it out - pretend your PC is stolen. Does **prey** work?

You might like to consider alternatives to NM - like **wicd** or configuring your network manually by editing **/etc/network/interfaces**

Again, please test it out. If you discover something interesting or useful, please post the link to your new thread here, as this thread is already marked as "Solved" (but it isn't, really).

Best wishes.

---

### Post by ahears on 2011-08-31
Well in my case it is solved because the problem is the Prey software and therefore not an Ubuntu issue. Meaning that the WiFi auto-connect feature in Prey was not written correctly or implemented correctly for it ***not ***to interfere with the nm-applet in Ubuntu.     :) To date: all of the issues with the nm-applet have ceased as a result of no longer using the WiFi auto-connect feature in Prey, however I still use all of the other features that come with Prey and it functions correctly.

---

