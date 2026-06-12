---
title: "ubuntu 9.10 samba having problem to share printer with windows xp"
date: 2009-12-15
forum: General Help
---

### Post by gabak on 2009-12-15
i have installed samba and i see the shared folders and the printer that i have installed in ubuntu pc but when i try to install the printer in all my laptops with windows xp i have this error.
It gives me an error message "The server for the printer does not have the correct printer driver installed. If you want to search for the printer driver, click OK..."
I click OK and it brings up a list of printers and the printer is not in the list.

i have hp psc 2175

---

### Post by cj13579 on 2009-12-15
make sure that your smb.conf file looks like this:

```
# add to [General] section:
  printcap name = cups
  printing = cups
  security = share

# make sure [printers] section looks like this
[printers]
  browseable = yes
  printable = yes
  public = yes
  create mode = 0700
  guest only = yes
  use client driver = yes
  path = /tmp

```

Then restart samba:

```
sudo /etc/init.d/samba restart
```

---

### Post by Fibonacci on 2009-12-24
> **cj13579 said:**
> make sure that your smb.conf file looks like this:

```
# add to [General] section:
  printcap name = cups
  printing = cups
  security = share

# make sure [printers] section looks like this
[printers]
  browseable = yes
  printable = yes
  public = yes
  create mode = 0700
  guest only = yes
  use client driver = yes
  path = /tmp

```

Then restart samba:

```
sudo /etc/init.d/samba restart
```

I have the exact same problem with a Xerox Phaser-6110, and your solution didn't help at all.
I'm running Jaunty, not Karmic, though.

---

