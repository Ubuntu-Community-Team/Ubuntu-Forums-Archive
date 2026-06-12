---
title: "shutdown after running scripts"
date: 2010-11-22
forum: General Help
---

### Post by boondocks on 2010-11-22
We have Ubuntu system that is used infrequently to gather, sort and save data.

This script is submitted to crontab as root, I am trying to shutdown the system after it has finished all the tasks:
```
#!/bin/bash

  #####  gather 
  
  #####  sort

  #####  save

  shutdown -h now

exit 0
```The only thing that does not work is the shutdown.
How do I make the system shutdown in this script?

---

### Post by skillet-thief on 2010-11-22
Does the system shut down correctly if you run the script at the command line instead of as a crontab?

---

### Post by boondocks on 2010-11-22
Yes it does.
When I do "sudo bash", enter the password and then execute the script - it does shutdown.

But when I submit the same script to crontab during the "sudo bash" session then it does not shutdown.
But the other tasks before the script execute just fine.

---

### Post by t4thfavor on 2010-11-22
Do this from a normal bash session:

```
sudo crontab -e 
```

Then you should setup the cron job as desired, the system should* then shutdown apropriately.

I'm not sure about the sudo bash command, but I have done this kind of stuff in the past.

---

