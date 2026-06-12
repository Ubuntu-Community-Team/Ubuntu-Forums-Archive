---
title: "Complete list of preinstalled software"
date: 2010-03-19
forum: General Help
---

### Post by da burger on 2010-03-19
I need a list of all the packages that are on a new ubuntu install. This is for a script I am trying to write. Does any one know where I can get this without doing a clean install and running dpkg -l?

P.s. even better would be being able to find out if a package was on the pc when it was a clean install.

---

### Post by spiky001 on 2010-03-19
you can open synaptic then there is an option that shows installed hope this helps you

---

### Post by da burger on 2010-03-20
I need to know the packages on a clean install not the packages on my current install.

---

### Post by linden940 on 2010-03-20
if you have VBox just put the clean install on there and check...


another thing you can do is have the program do the check when it gets onto the computer and do alot of "if" code lines....idk what your trying to make but just tryin 2 help

even if u knew what where all the reinstalled software...that will change often...so you would end up doing alot of "if" codes to make it work

---

### Post by da burger on 2010-03-20
I have found a solution to the problem. It's not quite as good as I would like but it is a lot easier. The program I was writing was intended to find out what software had been manually installed by the user. It does that through checking dependencies. Because of this it means that there are only 5 or 6 pre-installed packages with no reverse dependencies which is low enough to ignore. Unfortunately the program does not work as well as I would like because a few programs on my system have "loops" of dependencies.

---

### Post by linden940 on 2010-03-20
hmm...i can see how that would be helpful...that can be run by "noobies" so we can see what they have or have not done...


good work...keep at it

---

