---
title: "Empathy was not working"
date: 2010-01-23
forum: General Help
---

### Post by subhranath on 2010-01-23
A few days back I had a strange problem. After connecting to the internet in Ubuntu 9.10 I couldn't get Empathy working. Even after setting up the accounts, the entire status panel used to remain disabled. After some research the problem seemed to be of the way Empathy is configured by default. I used my MTS usb datacard to connect to the internet. Due to non availability of any proper customized dialer utility, I used wvdial, the console based pppd dialer, which bypasses the entire connection manager of the Gnome environment. And Empathy was looking for the connection manager to notify about the availability of network.

So, to fix it, you may do what I did:
1) Open terminal. (Applications-> Accessories-> Terminal)
2) gconf-editor
3) Browse to apps/empathy
4) Disable the "use_conn" checkbox to make sure that Empathy doesn't wait for notifications from the Gnome connection manager.

Now, everything works fine. And the Empathy status toolbar (panel) is back.

Hope this might be useful.

---

