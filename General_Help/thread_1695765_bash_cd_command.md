---
title: "bash cd command"
date: 2011-02-26
forum: General Help
---

### Post by klein de usa on 2011-02-26
hi 
i have been learning tcl tk. i would like to create a script that would open a terminal and in that terminal cd /home/me/level1 and then run wish in the same terminal, i'v tried this several ways and nothing works correctly.


#!/bin/bash
#
#
#opends a terminal
gnome-terminal

#should change to level1 directory
cd /home/klein/level1

#should start wish in level1 directory 
wish


end

---

### Post by down_to_earth_sort_of_guy on 2011-02-26
Instead do...

<pre>
#!/bin/bash
gnome-terminal -e "cd /home/klein/level1 && wish"
</pre>

or better yet, create a shortcut to gnome-terminal with the parameters as specified above ;)

---

### Post by klein de usa on 2011-03-01
hi
down_to_earth_sort_of_guy 
i created a launcher on the desk top and put in the command you gave me but it comes up (There was an error creating the child process for this terminal) doesn't bring up a normal prompt just a blinking courser .

---

