---
title: "Guake will not launch"
date: 2011-01-14
forum: General Help
---

### Post by mkeyes001 on 2011-01-14
I'm running ubuntu 11.04, when I attempt to start guake I get the spinner and I see the starting guake in the menu bar and then nothing....is it not compatible with my version yet?

```

helium01# guake
Traceback (most recent call last):
  File "/usr/lib/guake/guake.py", line 1353, in <module>
    if not main():
  File "/usr/lib/guake/guake.py", line 1296, in main
    instance = Guake()
  File "/usr/lib/guake/guake.py", line 620, in __init__
    self.add_tab()
  File "/usr/lib/guake/guake.py", line 1137, in add_tab
    final_params = self.get_fork_params(default_params)
  File "/usr/lib/guake/guake.py", line 1086, in get_fork_params
    self.update_proxy_vars()
  File "/usr/lib/guake/guake.py", line 1102, in update_proxy_vars
    ssl_port = self.client.get_string('/system/proxy/secure_port')
glib.GError: Type mismatch: Expected `string' got `int' for key /system/proxy/secure_port

```

---

### Post by mkeyes001 on 2011-01-14
I've fixed this issue....in /usr/lib/guake/guake.py

```

proxy = '/system/http_proxy/'
                ssl_host = self.client.get_string('/system/proxy/secure_host')
                #ssl_port = self.client.get_string('/system/proxy/secure_port')
                ssl_port = self.client.get_int('/system/proxy/secure_port')

```

I commented out the get_string section and added the the get_int section below it

I found this fix on the guake website for anybody interested...

---

### Post by mkeyes001 on 2011-01-14
I've fixed this issue....in /usr/lib/guake/guake.py

```

proxy = '/system/http_proxy/'
                ssl_host = self.client.get_string('/system/proxy/secure_host')
                #ssl_port = self.client.get_string('/system/proxy/secure_port')
                ssl_port = self.client.get_int('/system/proxy/secure_port')

```I commented out the get_string section and added the the get_int section below it

---

### Post by Fancycakes on 2011-02-02
I tried your suggestion, but guake still won't appear for more than half a second after I turn it on.

---

### Post by napas on 2011-06-16
i'm solved by:

```

cd /usr/share/pixmaps/guake/
cp guake-tray.default.png guake-tray.png

```

:p

---

