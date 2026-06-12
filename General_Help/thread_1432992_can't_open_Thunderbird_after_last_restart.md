---
title: "can't open Thunderbird after last restart"
date: 2010-03-18
forum: General Help
---

### Post by dluzius on 2010-03-18
Yesterday I had to reboot for some updates to take effect. Now, when I click on my Thunderbird icon, it won't open. Instead I get an error message "Failed to execute child process "thunderbird" (No such file or directory)"
What is the proper command line to enter in properties so it will work again?
TIA, Dave

---

### Post by paulkater on 2010-03-19
Best thing to do is first find out where thunderbird lives. Open a terminal and type

which thunderbird  (press enter)

If that does not tell you where the program is, it is not in the $PATH. In that case try

locate thunderbird | less  (press enter)

That should give you a screen full of info about all things thunderbird.
If you can't make heads or tails of it, you could do
locate thunderbird > /tmp/dump.txt and copy the contents of /tmp/dump.txt here so we have a look with you. (In case you are not used to 'less', press q to quit that.)

---

