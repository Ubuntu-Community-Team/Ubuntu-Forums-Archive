---
title: "sudo: must be setuid root"
date: 2011-06-25
forum: General Help
---

### Post by greenonions on 2011-06-25
While trying to downgrade Firefox I unconciously change /usr/lib and /usr/bin ownership to copy some files. So, now chromium won't open, I cannot even remove it. 
When a try to restore root ownership to those filesystems I get sudo: must be setuid root
I even try the same from recovery mode and the ownership is root now, but when i go back to normal mode i get the same sudo: must be setuid root


What can i do?!!!!=!?!?

---

### Post by Bachstelze on 2011-06-25
Back up your files and reinstall.

---

### Post by Ozymandias_117 on 2011-06-25
Go back to recovery mode and do this:
```
chown root:root /usr/bin/sudo
chmod 111 /usr/bin/sudo
chmod u+s /usr/bin/sudo
```

Edit: Although reinstalling might be a good idea.  You will have problems with more programs.

---

### Post by greenonions on 2011-06-25
Great did that !  and reinstall chromium  apt-get --reinstall install chromium-browser

Working fine! 
thanks!

---

### Post by lovinglinux on 2011-06-26
If you want to downgrade Firefox, don't mess with the system files. Download it from Mozilla and install in your home directory or /opt. See the manual installation method at [http://www.webgapps.org/tutorials/firefox/general/installing-other-versions](http://www.webgapps.org/tutorials/firefox/general/installing-other-versions)

If you provide the reasons why you want to downgrade, perhaps we can help to fix the issues. [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by smssms on 2011-08-10
Very new to all this, but got a netbook with Natty 11.04 installed. 

All going well, but on day 3 I start getting "sudo: must be setuid root" all the tine when I try to do stuff. No idea what caused this problem to start, but may have been around the time I tried out the Unity 2-d thing. 

I have googled and looked on here for solutions and tried many "chown" and "chmod" commands in recovery mode but I still just keep getting "sudo: must be setuid root"

help????

---

