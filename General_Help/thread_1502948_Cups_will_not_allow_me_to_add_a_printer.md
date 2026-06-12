---
title: "Cups will not allow me to add a printer"
date: 2010-06-06
forum: General Help
---

### Post by NCLI on 2010-06-06
I'm trying to setup a headless CUPS server, but no matter what I do, I can't add a new printer. Not using the web interface, or the GUI of another computer connected to the CUPS server.I always get to the point shown in the attached screenshot, and then I am asked for a password, which never works. I've practically slaughtered my cupsd.conf, and it now looks like this:
```
LogLevel info
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
AuthType none

<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  Require user @LOCAL
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
```
To my feeble mind, it looks like the above should tell CUPS to never ever ask for authentication, but as you can see in the second screenshot, it still does! I need help :(

---

### Post by KeyserSoze93 on 2010-06-06
I've had intractable issues with this too.

I'm currently using the web interface for my headless CUPS server - is this not an option for you?

---

### Post by NCLI on 2010-06-06
Same thing happens there :(

I got around this by using lpadmin to install the printers, but I'd really like to get it to work.

---

