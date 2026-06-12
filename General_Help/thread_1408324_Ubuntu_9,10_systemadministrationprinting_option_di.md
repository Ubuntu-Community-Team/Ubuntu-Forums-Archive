---
title: "Ubuntu 9,10 system/administration/printing option disappeared"
date: 2010-02-16
forum: General Help
---

### Post by mcgibga on 2010-02-16
I used the system/administration/printing option to set up a printer (Lexmark X4650).
The exact driver wasn't available, so I chose one 'close' to mine, but it wouldn't print.
I followed various threads to try to sort this, but now the system/administration/printing option has disappeared.
I can go in to [http://localhost:631](http://localhost:631) and set up a printer again, but this still doesn't work and the option in system/administration/printing still isn't there!
Whilst I see that there are issues with some Lexmark printers, which I can fire-fight, it's the fact that I've obviously done something to delete the Printing option that is the issue!
Has anyone seen this?


Thanks

---

### Post by nothingspecial on 2010-02-16
What happens if you type

```
system-config-printer
```

---

### Post by mcgibga on 2010-02-20
Sorry it took so long to come back.

I typed system-config-printer, the message The program 'system-config-printer' is currently not installed.  You can install it by typing:
sudo apt-get install system-config-printer-gnome
system-config-printer: command not found
was displayed I entered sudo apt-get install system-config-printer-gnome,
and hey presto, it installed the new package and the option is now in System/Administration.

Thanks for your help!!

---

