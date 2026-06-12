---
title: "cannot login - getting redirected to login screen after giving correct password"
date: 2012-01-10
forum: General Help
---

### Post by tevang on 2012-01-10
Hi,

I use Kubuntu 11.04. Every time I give my password, the screen becomes black, the cursor is displayed as an "X", and then I'm redirected back to the login screen.

I tried Alt+Ctrl+F2, logged in and checked that the X-server is already running with the startx command. "sudo kdm" also did nothing.

It is noteworthy that disk partitions were full but I released 17 GB from my /home. Now /home is used by 85%, / by 62% and /boot by 30%.

Please somebody tell me what else I can do!!

---

### Post by tevang on 2012-01-10
Anybody???

---

### Post by Grab&amp;Drop on 2012-01-10
Try update to 11.10

---

### Post by tevang on 2012-01-10
There won't be enough disk space to do the upgrade via the command line. I will need to do it from a live-cd and that requires backing up my disk and probably formatting it.

Does anyone have a more practical solution to suggest please?

---

### Post by Grab&amp;Drop on 2012-01-10
No, it doesn't.

In the Live-CD install, you have an option to "Upgrade Ubuntu 11.04 to Ubuntu 11.10".

---

### Post by tevang on 2012-01-11
Ok, let the upgrade be my last resort. Can anyone suggest something less time consuming please?

---

### Post by Wayne_V on 2012-01-11
it sounds like when /home filled up your home directory was corrupted.

try booting to recovery mode and then do:

# cd /home
# mv <user> <user>.save
# mkdir <user>
# chown <user>:<user> <user>

Then reboot and see if you can log in with this clean home directory.  If so, then you can recover what you want out of <user>.save to <user>

I'm assuming it was only /home that filled up ....

---

### Post by tevang on 2012-01-11
Yes it worked! Thank you! But how can I find the source of the corruption? Is trial and error the only way?

---

