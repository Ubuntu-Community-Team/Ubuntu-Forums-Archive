---
title: "Clock drift"
date: 2009-11-09
forum: General Help
---

### Post by imchipbrown on 2009-11-09
My clock is drifting about 1 min/hour.  I've installed a new battery on the MB with no change.

I've found that the command ntpdate -u time.nrc.ca will give "Permission Denied".  The same command works fine using sudo and the time gets updated. However, I get a password prompt. 

I want to set this as a scheduled task, which is now running every 15 minutes per the system log, but the time is not updating.

I thought maybe the task was running silently, waiting for the password, then quitting after a while when no password is supplied.

I added a group called sudo, put myself and root in it, and edited my sudoers so that group "sudo" has %sudo ALL=NOPASSWD: ALL

Using the command sudo (whatever) still gets me a password prompt.

Maybe there's a simpler/different way or a mistake in this method?

---

### Post by XCan on 2009-11-09
Did you schedule it using crontab? Perhaps you could try adding the command to root's crontab instead of yourself.

---

### Post by Johnsie on 2009-11-09
+1 for having it in crontab


> 

sudo nano /etc/crontab



Then add the following lines:


> 
00 *    * * *   root ntpdate -u time.nrc.ca   
15 *    * * *   root ntpdate -u time.nrc.ca    
30 *    * * *   root ntpdate -u time.nrc.ca   
45 *    * * *   root ntpdate -u time.nrc.ca   



Then it will happen automatically every 15 minutes

---

### Post by imchipbrown on 2009-11-09
That worked great.  Thank you. Any idea what was wrong with the original method?

---

### Post by XCan on 2009-11-09
Glad it worked out. Since you didn't say how you scheduled the original method it's hard to say what exactly was wrong, but it's safe to say that you scheduled it under an unpriviledged user, whereas the command requires root access.

---

