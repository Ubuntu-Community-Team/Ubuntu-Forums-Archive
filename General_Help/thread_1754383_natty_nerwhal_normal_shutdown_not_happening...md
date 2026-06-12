---
title: "natty nerwhal normal shutdown not happening.."
date: 2011-05-10
forum: General Help
---

### Post by rajeshkunnoth on 2011-05-10
i have installed ubuntu 11.04 on my HCL Me Laptop. the OS is not getting halted when i use the shut down or the restart menu from the GUI. it is not shutting down when used the commands 'sudo shut down now' or 'sudo poweroff now' or 'sudo halt now' or 'sudo init 0' also. except when used the 'shut down' command, the command line hangs at:

init: plymouth-upstart-bridge main process (1981) terminated with status 1
checking for running unattended upgrades.

when used the 'shut down' command, the violet screen where the word ' ubuntu ' is written appears and hangs.
i have updated my OS yesterday, but it is not fixing the problem..

all the time I am using power button to have a forced shutdown..

help needed, because i loved the natty nerwhal, except this problem..

---

### Post by mideal on 2011-05-10
Had the same problem and found out, that after all updates, 
sudo shutdown 0
and
sudo reboot -i
worked.

After doing it once manully it also worked via menu for me.

---

### Post by justerson on 2011-05-10
This happened to my with my upgrade to 11.04. Nothing worked. I re-installed 10.10 UNR and now I have the same issue with that install even though I didn't when I used to have it installed prior to my 11.04 upgrade. Menu shutdown doesn't work, cmd shutdowns don't work, nothing.

---

### Post by justerson on 2011-05-10
I had this issue for over a week and tried everything. I stumbled along this thread:

[http://ubuntuforums.org/showthread.php?p=10796364#post10796364](http://ubuntuforums.org/showthread.php?p=10796364#post10796364)

See the "blacklist 2800pci" bit and give it a try. This was the only thing that worked out of all my attempts.

---

### Post by rajeshkunnoth on 2011-05-10
> **justerson said:**
> I had this issue for over a week and tried everything. I stumbled along this thread:

[http://ubuntuforums.org/showthread.php?p=10796364#post10796364](http://ubuntuforums.org/showthread.php?p=10796364#post10796364)

See the "blacklist 2800pci" bit and give it a try. This was the only thing that worked out of all my attempts.

dear justerson,

thank you for your advice..  now the headache is no more.

the blacklisting is making a wonder.

thank you, 
[email]rajeshkunnoth@gmail.com[/email]

---

### Post by makro on 2011-05-11
it doesn't work for me...
I don't have rt2800 module loaded...

I've exactly same problem in post #1

---

### Post by Y_Ernst on 2011-05-14
+1 
Same problem. I'm sorry for the ubuntu team. All the hard work in the last 6 month and than this buggy linux kernel ruined the natty release.

Very frustrating is the fact that you are completely ignored by the kernel developers.
They still focus on server development.

---

### Post by ontwowheels on 2011-05-14
NICE, this did the trick for me.

---

### Post by nucleuskore on 2011-05-22
eeepc 1000H

worked for me too

Thanks!

---

