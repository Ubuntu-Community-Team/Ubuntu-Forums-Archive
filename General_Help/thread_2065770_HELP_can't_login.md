---
title: "HELP can't login"
date: 2012-10-02
forum: General Help
---

### Post by cyclingchap on 2012-10-02
Please help. Yesterday I added a script file to 

/etc/pm/sleep.d/  called "80-synaptics-three-finger".

I was following instructions posted on this forum to enable middle click with a touchpad on a laptop. The script contains:

#!/bin/sh  # Restore three finger tapping  case "$1" in         resume|thaw)                 sleep 5;                 /bin/su YOUR_USER_NAME -c "/usr/bin/synclient TapButton3=2"                 ;; esac
and to create the file I typed :

gksudo gedit /etc/pm/sleep.d/80-synaptics-three-finger.

Really regretting doing this now, as every time I try and log in, I keep getting bounced back to the login screen. I can't remove the "80-synaptics-three-finger" script file when logged in as guest, which is what I'm doing now to access the this forum. Typing 'sudo' when looged in as guest doesn't help.

When booting up in a 'root shell' I still can't delete the "80-synaptics-three-finger" script file.

I'm sure this file is to blame ....

Someone please help!!

Cheers..

---

### Post by cyclingchap on 2012-10-02
OK.. so after a CTL-ALT-F1 and a login as USID I can remove the script file in /etc/pm

However, I still get bounced back to the login screen when I try and login with the full graphics.

After reading related threads, I've tried :

sudo mv .Xauthority .Xauthority.bak
sudo shutdown -r now

and also

chown USID .Xauthority
sudo shutdown -r now

and neither of these work. I am totally frustrated now. Ubuntu is supposed to be a superior OS. I've been using it for 3 weeks .. how on earth can this happen?

I've spent hours installing compilers/libraries/software .. etc. I do not want to have to reinstall the whole OS (as some have suggested in other threads)!

Someone, please help!!

---

### Post by cyclingchap on 2012-10-02
just to add, I notice that my .Xauthority file is empty .. i.e. 0 bytes.

Is this as it should be?!?

---

### Post by steeldriver on 2012-10-02
on successful login it should contain one or more 'magic cookies' - typically a few tens of bytes 

did you check its permissions? it should be -rw------ (mode 600)

---

### Post by cyclingchap on 2012-10-03
Yes the permissions are 600, i.e.  -rw------. But the file is empty. 

My username/usid also has 'ownership' of the file, not root. On other threads someone said that if root has ownership of this file then that can cause a login problem.

---

### Post by cyclingchap on 2012-10-04
OK, so a work friend resolved this problem for me.

Somehow the paths in my .profile file had been changed, probably after installing the scientific data visualization package 'VISIT'.

A single "PATH=/home/USERNAME/Programs/visit2_5_2.linux-x86_64/bin/visit " line had been appended to my  .profile file. 

This was overriding all the PATH settings earlier in the file, which was stopping all commands from working, including ones necessary to successfully log in.

A tell tale sign that the paths were screwed up was a message like 'ls -l command not recognized, command is in /usr/bin' when trying to get a simple file listing after logging in following a CTL-ALT-F1.

Amending the offending path command at the end of the .profile file to the following:

export PATH="$PATH:/home/paul/Programs/home/paul/Programs/visit2_5_2.linux-x86_64/bin/visit$I"

completely cured the problem.

Morale of the story .. check the simple things first when diagnosing a problem! ;)

---

