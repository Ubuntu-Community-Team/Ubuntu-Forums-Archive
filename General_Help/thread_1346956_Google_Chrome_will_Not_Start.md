---
title: "Google Chrome will Not Start"
date: 2009-12-05
forum: General Help
---

### Post by Joseph Schwenker on 2009-12-05
```
[2249:2249:296281133:FATAL:/usr/local/google/home/chrome-eng/b/slave/chrome-official-linux/build/src/chrome/browser/zygote_host_linux.cc(117)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /opt/google/chrome/chrome-sandbox is mode 4755 and owned by root.
Trace/breakpoint trap
```
Google Chrome used to launch, then when I closed it, its status became "Zombie", and I could not kill it.  Eventually, I was able to kill it, and now it won't start!  Songbird won't start either!  I hate Ubuntu 9.10!

---

### Post by linusr on 2010-03-11
did u solve it? Chrome became zombie in my laptop as well....

damn... firefox saved my day... tried all possibility I knew - re-insatll, delete profile dir, tried unstable version and chrome loves to be zombie..

---

### Post by Meatless Balogna on 2010-03-11
I got chrome working no problem on 9.10 hardy - maybe you want to try that instead of jaunty

---

### Post by linusr on 2010-03-11
> **Meatless Balogna said:**
> I got chrome working no problem on 9.10 hardy - maybe you want to try that instead of jaunty

I'm on Ubuntu 9.10 32-bit. Chrome was working till last week. our of nowhere chrome-sandbox becomes zombie

---

### Post by linusr on 2010-03-11
everytime I open chrome ~/.xsession.errors has an entry

Failed to move to new PID namespace: Operation not permitted

It's an chrome bug!!?

---

### Post by n0dix on 2010-03-11
I don't think is a Chrome bug. I have the recent Google-chrome version (5.0.307.11 beta) on Arch Linux without any problem.

---

### Post by linusr on 2010-03-11
> **n0dix said:**
> I don't think is a Chrome bug. I have the recent Google-chrome version (5.0.307.11 beta) on Arch Linux without any problem.

You are correct. Recently moved /opt to a separate partition and fstab entry had nosuid which seems to be the cause of prblm...

removing 'nosuid' solved the problem..

chrome zombie seems to be related to /opt/google folder permissions

---

### Post by Joseph Schwenker on 2010-03-12
I don't have any idea what caused the problem.  Reinstalling Chrome solved it, though.  My computer crashed a month later due to a hardware failure, which I believe is either the PSU's or motherboard's fault.

---

### Post by n0dix on 2010-03-12
> **Joseph Schwenker said:**
> I don't have any idea what caused the problem.  Reinstalling Chrome solved it, though.  My computer crashed a month later due to a hardware failure, which I believe is either the PSU's or motherboard's fault.

Be careful with that. ;)

---

### Post by Joseph Schwenker on 2010-03-12
> **n0dix said:**
> Be careful with that. ;)

After replacing the power supply, CMOS battery, taking out my graphics card, and reseating the CPU, how could I NOT be careful?  ;)

---

### Post by Joseph Schwenker on 2010-05-07
Apparently, it's a permissions problem.  I changed /opt to be owned by me using ```
sudo chown joseph:joseph -R /opt
```

The error message indicates that chrome-sandbox needs to have permission 4755, so I ran this command: ```
sudo chmod 4755 /opt/google/chrome/chrome-sandbox
```
and Chrome ran perfectly.  Even changing /opt back to root with the command ```
sudo chown root:root -R /opt
``` does not allow Chrome to run!

---

### Post by cuberts on 2010-05-07
> **Joseph Schwenker said:**
> ```
[2249:2249:296281133:FATAL:/usr/local/google/home/chrome-eng/b/slave/chrome-official-linux/build/src/chrome/browser/zygote_host_linux.cc(117)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /opt/google/chrome/chrome-sandbox is mode 4755 and owned by root.
Trace/breakpoint trap
```Google Chrome used to launch, then when I closed it, its status became "Zombie", and I could not kill it.  Eventually, I was able to kill it, and now it won't start!  Songbird won't start either!  I hate Ubuntu 9.10!Then you should upgrade to Lucid. and also when you see that it is not running then you should always try a reboot.

---

### Post by eliudhr on 2012-01-19
> **Joseph Schwenker said:**
> Apparently, it's a permissions problem.  I changed /opt to be owned by me using ```
sudo chown joseph:joseph -R /opt
```The error message indicates that chrome-sandbox needs to have permission 4755, so I ran this command: ```
sudo chmod 4755 /opt/google/chrome/chrome-sandbox
```and Chrome ran perfectly.  Even changing /opt back to root with the command ```
sudo chown root:root -R /opt
``` does not allow Chrome to run!

Yes its works :) in any linux distro. Thanks ! :popcorn:

---

### Post by oldos2er on 2012-01-19
Closed, necromancy.

---

