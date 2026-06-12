---
title: "after update error"
date: 2010-06-26
forum: General Help
---

### Post by miko5054 on 2010-06-26
im receiving this error after update or when im installing new software 

i upload the screenshot 

[HTML] http://www.2shared.com/photo/uruKswRK/Screenshot.html[/HTML]

---

### Post by flanagan on 2010-06-26
nothing but spam on that page

---

### Post by miko5054 on 2010-06-26
sorry for the link a thought i will be useful

check this

```
  Unknown option: hostname
Usage:
      dkimproxy.in [options] LISTENADDR:PORT RELAYADDR:PORT
        smtp options:
          --conf_file=FILENAME
          --listen=LISTENADDR:PORT
          --relay=RELAYADDR:PORT
          --reject-error

        verification options:
          --reject-fail
          --hostname=HOSTNAME

        daemon options:
          --daemonize
          --user=USER
          --group=GROUP
          --pidfile=PIDFILE

      dkimproxy.in --help
        to see a full description of the various options

                                                                         [fail]
invoke-rc.d: initscript dkimproxy, action "start" failed.
dpkg: error processing dkimproxy (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of dtc-toaster:
 dtc-toaster depends on dkimproxy; however:
  Package dkimproxy is not configured yet.
dpkg: error processing dtc-toaster (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 dkimproxy
 dtc-toaster
E: Sub-process /usr/bin/dpkg returned an error code (1)
mikmik@mikmik-deskt
```

---

### Post by Rubi1200 on 2010-06-26
You could try this first and see if it resolves the problem:

```
sudo dpkg --configure -a
```

---

### Post by miko5054 on 2010-06-26
try this already

same result

---

### Post by Rubi1200 on 2010-06-26
Have you tried re-installing dtc-toaster or configuring dkimproxy or downloading dkimproxy separately?

---

### Post by miko5054 on 2010-06-26
no i dont knew anything about it

---

### Post by Rubi1200 on 2010-06-26
The problem seems to be here:

> dpkg: dependency problems prevent configuration of dtc-toaster:
 dtc-toaster depends on dkimproxy; however:
  Package dkimproxy is not configured yet.

Perhaps a re-install might help.

---

### Post by mpcube on 2010-07-05
> **miko5054 said:**
> 
```
  Unknown option: hostname
Usage:
      dkimproxy.in [options] ...

```

if

hostname -d yeilds nothing

but

hostname -f yeilds your hostname

you can edit /etc/init.d/dkimproxy (line 62) accordingly.

...but the Problem is not /etc/init.d/dkimproxy, but something in your DNS setup missing, i think.

GRuesse, Matthias

---

### Post by amrhelmy2004 on 2010-08-02
> **mpcube said:**
> if

hostname -d yeilds nothing

but

hostname -f yeilds your hostname

you can edit /etc/init.d/dkimproxy (line 62) accordingly.

...but the Problem is not /etc/init.d/dkimproxy, but something in your DNS setup missing, i think.

GRuesse, Matthias

This is Works with debian Testing with the same problem, thanks alot

---

