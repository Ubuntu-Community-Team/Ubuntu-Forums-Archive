---
title: "Shutting down/logging off problems"
date: 2009-07-10
forum: General Help
---

### Post by pablopancho on 2009-07-10
Hi,
Sometimes I have a strange problem while logging off from Gnome: a small window appears listing an "unknown program" that is not responding. I wanted to know what is the problem but the only thing I found was this in syslog:
```
Jul 10 15:55:36 pablo-laptop x-session-manager[3865]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed 
Jul 10 15:55:36 pablo-laptop x-session-manager[3865]: WARNING: Client '(null)' failed to reply before timeout 
Jul 10 15:55:36 pablo-laptop x-session-manager[3865]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed 
Jul 10 15:55:36 pablo-laptop x-session-manager[3865]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed 
Jul 10 15:55:36 pablo-laptop x-session-manager[3865]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed 
```

I don't know if this has anything to do with my problem though...

Another problem is that when I shut down or restart the shutting down procedure gets stuck just before it is supposed to power off. It leaves me with black screen and cursor blinking. I have to ctrl+alt+del or ctrl+alt+SysRq+o to reboot/power off.

I am using Ubuntu 9.04 64bit on Dell XPS m1530 laptop with NVidia 8600 (prop. drivers turned on).

---

### Post by jdalton on 2009-07-10
I too have the black screen and blinking cursor problem.

HP 64 bit laptop running 9.04

---

### Post by maverick340 on 2010-01-14
[http://ubuntuforums.org/showthread.php?t=1062579&highlight=unknown+program+shut&page=2](http://ubuntuforums.org/showthread.php?t=1062579&highlight=unknown+program+shut&page=2)

---

### Post by maverick340 on 2010-02-25
I dont know if anyone is following this thread, but the problem has stopped for me. I stopped using banshee (mono based right?) , and have been updating Ubuntu regularly. Compiz is back turned on and so is Docky. I dont get the problem anymore, so yay !

---

