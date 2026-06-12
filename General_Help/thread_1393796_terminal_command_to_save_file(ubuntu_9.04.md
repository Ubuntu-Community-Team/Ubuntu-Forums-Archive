---
title: "terminal command to save file(ubuntu 9.04"
date: 2010-01-29
forum: General Help
---

### Post by rdema19403 on 2010-01-29
i have a file that i want to change the line in it 
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Negotiate ([want to delete negotiate  and replace with basic)
<Location />
  Allow all
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Encryption Required
i donot know how to save this change
Thanks in advance

---

### Post by wojox on 2010-01-29
If you use nano it's Ctrl+O to save and Ctrl+X to quit.

---

