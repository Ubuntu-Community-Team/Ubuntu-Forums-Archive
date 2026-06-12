---
title: "Restart goes to login"
date: 2012-03-02
forum: General Help
---

### Post by retrodans on 2012-03-02
Whenever I try to get Ubuntu to restart/shutdown using the GUI or after a synaptic update, it simply shuts the desktop and goes to the login screen.  No restart/shutdown actually happens.  I have a bad feeling this is due to something I have done, but wanted to see whether this is a more common issue with anyone, and whether there is a nice way I can investigate it.

Thankyou,
Dan

---

### Post by raja.genupula on 2012-03-02
I hope this can help you
[http://superuser.com/questions/63500/problem-restarting-my-ubuntu-system](http://superuser.com/questions/63500/problem-restarting-my-ubuntu-system)

---

### Post by grahammechanical on 2012-03-02
Are you the only user?

If someone else is using the machine and they log out and you log in, then when you shutdown you get put back to the log in screen. The first user needs to log in and they can run shutdown and it should work as expected.

Regards.

---

### Post by retrodans on 2012-03-03
@raja.genupula
Thanks for the link, sadly, I don't have a kexec file to modify on my machine.  Also, if it helps, I ran the ```
sudo shutdown -r now
``` command in terminal.  This rebooted the machine as required.

@grahammechanical
I am the only user on the machine, it auto boots in, there is no login required on boot.

---

### Post by paradox242 on 2012-03-08
I have the same problem you describe. When I try to shutdown from the GDM login screen, or from within Unity, it takes me back to the GDM login.

I can run sudo init 6 or other command line options to reboot and it works as expected.

I can't pinpoint the exact time this started occuring, but sometime in the last month. I do recall installing something that used KDE libraries (Smb4K) but other than that I've just been running regular system updates.

I tried to follow the instructions in that link, but there is no such file as /etc/default/kexec.

---

### Post by retrodans on 2012-04-16
UPDATE: I no longer have this issue it seems.  I am not sure what I did, but after ignoring it a while, and keeping my system up to date, it has just gone away.  If I work out what the solution was, I will let you know, otherwise I will have to assume it was an update I ran in.

---

