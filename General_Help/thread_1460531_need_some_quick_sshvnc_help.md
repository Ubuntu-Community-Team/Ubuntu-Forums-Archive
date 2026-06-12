---
title: "need some quick ssh/vnc help"
date: 2010-04-22
forum: General Help
---

### Post by onesojourner on 2010-04-22
I am trying to use vnc to controll my desktop from my laptop when I am out of town. I think I have ssh working correctly. I can use vinagre and connect to my desktop over the internet and log in. What do I need to do now to get vnc working?

---

### Post by onesojourner on 2010-04-22
I figured it out if any one is interested:

   2.
         1. Run putty
         2. Set the host name to your No-IP address or IP address. (e.g., spark.no-ip.info).
         3. Set the port to 8443.
         4. Under "Connection" -> "SSH" -> "Tunnels", add a tunnel: Set the source port to 5901, set the destination to localhost:5900, and click the "Add" button.
         5. Save your session: go back to the "Session" category, type "tunnel-home" in the text box under "Saved Sessions" heading, and click the "Save" button.

Usage

   1. On your work computer, open putty and run the "tunnel-home" profile.
   2. A terminal window will appear &#8212; log in using your username and password for your home computer. (If this is your first login from this machine, check to make sure the fingerprint matches. If not, don't enter your password!)
   3. Open VNC client and open a connection to localhost:5901.

---

