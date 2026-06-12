---
title: "BASH - How can I close the active window from a running script?"
date: 2010-02-24
forum: General Help
---

### Post by allenwjones on 2010-02-24
**Q: How do I close the active window from a Bash terminal script?**
 
Surrounding details:
 
From a Bash terminal script, I mount a particular drive and display the contents in thunar (Xubuntu) to validate contents. I would like the script to automatically close this new window and continue. This window will always be the primary window and does not need to display for more than a moment.
 
Thank You!

---

### Post by Barriehie on 2010-02-24
> **allenwjones said:**
> **Q: How do I close the active window from a Bash terminal script?**
 
Surrounding details:
 
From a Bash terminal script, I mount a particular drive and display the contents in thunar (Xubuntu) to validate contents. I would like the script to automatically close this new window and continue. This window will always be the primary window and does not need to display for more than a moment.
 
Thank You!

Please post your script!

---

### Post by ratcheer on 2010-02-24
If you start the script under the nohup command, you can close the terminal and it will continue to run. You also have to run the script in the background so you can get control back to be able to close the window. E.g.,

```

nohup your_script &

```

Then, hit Enter to get back to a command prompt, then exit or Ctrl-d.

Tim

---

### Post by allenwjones on 2010-02-26
I am sorry, but I will not post the details of the script here as it contains certain information that cannot be disclosed.

However, a similar script might be like:

```

#!bin/bash
# Script to mount a local drive and display it

MOUNT ()
 {
  mount /dev/sda1 /media/local
   thunar /media/local
    ~insert command here~
  return
 }

#Execution
MOUNT
EXIT

```

I would like at this point to close the window opened by thunar after it has displayed the contents.

---

### Post by derrick81787 on 2010-02-26
I would use the "kill" command and the process ID of the thunar command.  For example, I would change your script to:

```

#!bin/bash
# Script to mount a local drive and display it

MOUNT ()
 {
  mount /dev/sda1 /media/local
   thunar /media/local &
   sleep 3 # to wait for 3 seconds. Change to whatever you want
   kill $!
  return
 }

#Execution
MOUNT
EXIT

```

Notice that I used an **&** to open Thunar in the background and then paused for 3 seconds.  The **kill $!** command should kill (and therefore close) Thunar.  The **$!** returns the process ID of the last command that was run in the background (which is Thunar in this case), and so the kill command will only kill that window, as opposed to if you used the "killall" command to kill all Thunar windows.

I think this should work, but I'm currently at work and don't have access to Ubuntu to test it.  I got my information from here: [http://tldp.org/LDP/abs/html/internalvariables.html]("http://tldp.org/LDP/abs/html/internalvariables.html"). Scroll down to the section that describes **$!**.  In general, tldp.org is a good resource for Bash scripting.

I hope this helps.

- Derrick

---

