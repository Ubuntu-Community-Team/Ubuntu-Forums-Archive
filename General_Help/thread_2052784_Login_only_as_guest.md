---
title: "Login only as guest"
date: 2012-09-03
forum: General Help
---

### Post by Crossbow on 2012-09-03
Hi - I was having this problem and purging and reinstalling nvidia as described appeared to fix it, except afterwards I couldn't log in as myself, only as a guest user. So I tried this:

[http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04](http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04)

Then I had no log in at all, graphic OR textual! I managed to get a login back in recovery mode but I still can't log in as myself.

---

### Post by oldfred on 2012-09-03
@ Crossbow

Moved to new thread as now you issue is not related to nVidia.
Originally this thread.
[http://ubuntuforums.org/showthread.php?t=2049054](http://ubuntuforums.org/showthread.php?t=2049054)

Is it a password issue or user issue?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Broken sudo
Check permissions - should be
 ls /etc/sudoers -l
-r--r----- 1 root root 723 Jan 31  2012 /etc/sudoers
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
chmod 0440 /etc/sudoers
chown root:root /etc/sudoers

---

### Post by Crossbow on 2012-09-04
Thanks. 

Neither of those seem to apply. I can go into text and use sudo just fine, and when I deliberately put the wrong password in the login I get an "invalid" message. When I put the right one in, it appears to accept it and looks like it's logging me in but then bounces me back to the login page. Just in case I had accidentally changed the password at some point, I did go in and reset it. So, the password is right and I do have sudo power. And when I look at users, it says I am the admin. The problem is only with the GUI login, not the text one. 

I should also explain that I have an actual alternate login called "guest," not just the guest login that doesn't need a password. I think there is probably a way to use that to access my files, but I don't know how.

---

### Post by NikTh on 2012-09-04
Hello , 

maybe it is an .Xauthority issue ? 

Try this from Console Mode (Ctrl+Alt+F2)

```
sudo service lightdm stop
sudo chown username:username ~/.Xauthority
sudo service lightdm start
```Where username replace it with your actual username. 
Thanks

---

### Post by Crossbow on 2012-09-04
It worked! I'm not sure why because I probably did it wrong, but I'm back in now. 

That first command made the screen go black. No arrow, no cursor. I waited. Nothing happened. I restarted. Then I tried the second command and it was accepted but didn't give me a response. So I put in the third and it said lightdm was already running. I restarted and still couldn't log in. I went back to console and did the stop command again. Black screen again. Restarted and then I could log in. 

Thanks!

---

