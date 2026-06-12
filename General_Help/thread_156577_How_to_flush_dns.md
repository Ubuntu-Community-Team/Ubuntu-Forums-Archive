---
title: "How to flush dns?"
date: 2006-04-07
forum: General Help
---

### Post by zerohalo on 2006-04-07
Does anyone know how to flush the dns cache in Ubuntu? Ie, the equivalent of c:>ipconfig /flushdns in Windows. Thanks! (Rebooting is not doing it.)

---

### Post by hardrocksr on 2006-05-25
I am looking how to flush dns settings too. Did you ever find an answer?

---

### Post by Ramses de Norre on 2006-05-25
Maybe ```
sudo /etc/init.d/dns-clean start
``` but I'm not sure.

---

### Post by coder_cotton on 2007-07-10
> **Ramses de Norre said:**
> Maybe ```
sudo /etc/init.d/dns-clean start
``` but I'm not sure.

negative.  anyone else?

---

### Post by coder_cotton on 2007-07-10
My router had it cached... I ended up just changing my dns server to 4.2.2.2 (one of the big DNS servers out in cali) until my router updates dns from my ISP...

---

### Post by bisteck on 2007-08-14
This worked for me:

sudo /etc/init.d/networking restart.

Hope this helps.

---

### Post by Rootong on 2007-09-18
Of course, it should work fine for you. But I am also looking for it but do not want to restart the service.

Any ideas?

---

### Post by feld on 2007-09-25
Linux does not cache DNS by default. You have to manually install nscd or a dns server to cache DNS. Your DNS server IS your cache. If you have a router, restart that router. It will clear the cache.

If you run firefox you can go into the config and clear Firefox's dns cache. It has its own. Or just go to offline mode in firefox and then back on. That works too.

Have fun!

---

### Post by tillkowski on 2008-03-19
Where does firefox keep the DNS cache? I would like to clear it from inside a bash script.

---

