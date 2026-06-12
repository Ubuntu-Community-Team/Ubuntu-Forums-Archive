---
title: "FIFO Delay on Ubuntu 10.04 / sshdfilter issues"
date: 2010-09-19
forum: General Help
---

### Post by workmaster2n on 2010-09-19
Hi,

I am trying to set up sshdfilter on my new linux box and can't get the expected functionality. I couldn't get IP's to be blocked no matter how many bad passwords I put in. I have sshdfilter set up to read from a fifo (/var/log/sshd.fifo, which has been chmod'd to 600), but when I run sudo tail -f /var/log/sshd.fifo, I don't see any output as I attempt to SSH into the machine, though /var/log/auth.log is correctly logging the login attempts. However, when I run sudo reboot -h now, the entries from /var/log/auth.log appear in the FIFO. I'm wondering if I don't have a misconfiguration somewhere that isn't allowing my auth.log to pipe to my FIFO (I am running a virtual bridge).

Any ideas?

I can provide more system specific information if anybody is curious (no, I won't give you my IP so you can brute force my sshdfilter-less computer. Nice try though) 

Thanks!

---

### Post by jbrown96 on 2010-09-19
I use fail2ban. It works the same.

---

### Post by workmaster2n on 2010-09-19
fail2ban works right out of the box.  Thanks for the tip!

For anybody else who is new to fail2ban, the system has changed a bit since most tutorials were written.  The tutorials reference /etc/fail2ban.conf as the place to make changes.  Changes are now made inside of "application" *.conf files.  Full documentation is available from the fail2ban [site]("http://www.fail2ban.org/wiki/index.php/Manual").

Quick observation/difference between fail2ban and sshdfilter.  faile2ban defaults to only ban IP or hosts for 15 minutes (nice if you accidentally lock yourself out).  If you want to permanately ban an IP/host, change ban time to a negative number (-1).

I'll leave this as not-solved to see if someone can solve the sshdfilter issue on 10.04.  But in the mean time, fail2ban is working great. 

Thanks for the tip though! My system is now a thousand times safer.

---

