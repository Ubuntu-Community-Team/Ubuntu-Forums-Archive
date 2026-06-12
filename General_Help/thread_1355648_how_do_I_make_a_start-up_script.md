---
title: "how do I make a start-up script"
date: 2009-12-15
forum: General Help
---

### Post by rhythmiccycle on 2009-12-15
Every time I reboot, I have to run these 3 lines of code to get my monitor set up right. 

Is there a way to make these 3 line run automatically every time I boot?

---

### Post by audiomick on 2009-12-15
Have a look at this

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by Brandon Williams on 2009-12-15
Try adding those lines to /etc/rc.local, just in front of the line that reads 'exit 0'. Make sure that /etc/rc.local is executable with 'sudo chmod a+x /etc/rc.local'. As long as it is executable, /etc/rc.local will be run at the end of the boot-up sequence.

If that doesn't work, there are other things to try, but you'll probably want to be more specific about the commands you need to run so we can figure out what the special requirements might be.

---

