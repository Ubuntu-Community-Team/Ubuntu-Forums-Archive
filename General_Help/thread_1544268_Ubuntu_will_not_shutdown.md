---
title: "Ubuntu will not shutdown"
date: 2010-08-02
forum: General Help
---

### Post by michaelbobe1 on 2010-08-02
I just added Ubuntu 10.4 to my laptop. Its is a dual boot with Win7. Win7 was installed first. Whenever I shut down or restart, its just sits at the Ubuntu splash screen. What should I do?

---

### Post by stlsaint on 2010-08-02
Are you implying that the system freezes?
What are your computer specs and how much swap do you have?

---

### Post by KdotJ on 2010-08-02
Is it the splash screen or the login screen? Because for me, occasionally when I click shut down or restart it just throws me to the login screen. I have to do a hard shutdown in that scenario

---

### Post by michaelbobe1 on 2010-08-02
> **stlsaint said:**
> Are you implying that the system freezes?
What are your computer specs and how much swap do you have?

Whenever I restart or shutdown, the Ubuntu logo displays with the dots under it and the they just keep moving to the right, turning red. I have 4GB swap

---

### Post by michaelbobe1 on 2010-08-02
> **KdotJ said:**
> Is it the splash screen or the login screen? Because for me, occasionally when I click shut down or restart it just throws me to the login screen. I have to do a hard shutdown in that scenario

Also, when I hit escape, the last two lines say:

*will now restart
                Killed

---

### Post by cob on 2010-08-02
Show us your /var/log/dmesg and /var/log/syslog, perhaps there are clues there.  Also, if during shutdown you're able to hit ALT+SHIFT+F1 and get a console and log in, run sudo ps aux and tell us what services are still running.

---

### Post by ST3ALTHPSYCH0 on 2010-08-02
Before doing a hard shutdown always try:
hold alt+prntscrn+(type in sequence)r-e-i-s-u-o

---

### Post by michaelbobe1 on 2010-08-02
> **cob said:**
> Show us your /var/log/dmesg and /var/log/syslog, perhaps there are clues there.  Also, if during shutdown you're able to hit ALT+SHIFT+F1 and get a console and log in, run sudo ps aux and tell us what services are still running.

When I type those two commands in the command line, I get access denied and nothing happens with ALT+SHIFT+F1

---

### Post by chrisinspace on 2010-08-02
Do you have any network drives mounted using samba or cifs?  If so, did you make them persistent using fstab?  If yes to both, it's a [known issue]("http://ubuntuforums.org/showthread.php?t=1344278") that has not been fixed yet, though there are some work arounds (described in the link).

---

### Post by michaelbobe1 on 2010-08-02
> **chrisinspace said:**
> Do you have any network drives mounted using samba or cifs?  If so, did you make them persistent using fstab?  If yes to both, it's a [known issue]("http://ubuntuforums.org/showthread.php?t=1344278") that has not been fixed yet, though there are some work arounds (described in the link).

No I do not.

---

### Post by cob on 2010-08-03
How about the logs?

---

### Post by michaelbobe1 on 2010-08-03
> **cob said:**
> How about the logs?

I can see the logs.

---

### Post by michaelbobe1 on 2010-08-03
> **ST3ALTHPSYCH0 said:**
> Before doing a hard shutdown always try:
hold alt+prntscrn+(type in sequence)r-e-i-s-u-o

Does not do anything.

---

### Post by ubunterooster on 2010-08-03
It's r-e-i-s-u-b

See: [http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html](http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html)

---

### Post by ST3ALTHPSYCH0 on 2010-08-04
REISUB is reboot... REISUO is shutdown, but I've had systems that down respond to both (although it's usually reboot that doesn't work).
Anyway, typically if that doesn't work then your system is frozen for real. Sorry I can't be any help in diagnosing.

---

