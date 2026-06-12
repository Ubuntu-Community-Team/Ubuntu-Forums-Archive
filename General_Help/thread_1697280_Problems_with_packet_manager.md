---
title: "Problems with packet manager"
date: 2011-02-28
forum: General Help
---

### Post by Snorkeys on 2011-02-28
Whenever i try to install any software, it comes up with this error:

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type &#8216;echo&#8217; is not known on line 2 in source list /etc/apt/sources.list.d/winff.list, E:The list of sources could not be read.


**Then when i click close it comes up with this:**


E: Type &#8216;echo&#8217; is not known on line 2 in source list /etc/apt/sources.list.d/winff.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


Can anybody help?
Many Thanks

---

### Post by Smart Viking on 2011-02-28
What is the output of this command:
```
cat /etc/apt/sources.list.d/winff.list
```

---

### Post by Snorkeys on 2011-02-28
echo "deb [http://winff.org/ubuntu](http://winff.org/ubuntu) hardy universe"

sudo apt-get update && sudo apt-get install winff


Thats the reply from the command. What do you think is wrong?

---

### Post by Smart Viking on 2011-02-28
I donno how that got there, just delete it with this command:
```
sudo rm /etc/apt/sources.list.d/winff.list
```

Then try to install some other software and see if you get that error.

---

