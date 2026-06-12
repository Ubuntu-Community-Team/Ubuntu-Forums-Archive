---
title: "Gnome 3: Games not launching because of path environment"
date: 2011-04-29
forum: General Help
---

### Post by nukedeath on 2011-04-29
Hello!
I installed Gnome 3.0 today on my fresh Ubuntu 11.04 with the ppa.

But games i install wont work!
When i click on the icon in applications it will not launch.
Running in terminal gives me "not available in "/usr/games/"whatevergame"
The command could not be located because '/usr/games' is not included in the PATH environment variable.

I checked my /etc/environment and it says:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

I really have no idea how i can fix it :(

---

### Post by nukedeath on 2011-05-03
I solved the problem.
Added PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
to the bottom of .profile and .bashrc

---

