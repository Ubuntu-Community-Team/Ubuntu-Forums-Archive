---
title: "Problem with SUDO command"
date: 2011-05-27
forum: General Help
---

### Post by athenroy on 2011-05-27
Hello, I'm running 11.04 64 Bit with Classic Desktop.  I've been able to install programs using Synaptic and the Software Center, but if I try a sudo apt-get in a terminal it asks for my password and locks up and I can't enter it.  Now, if I use the gksu than the password GUI pops up and I can enter my password.  Same holds true if I have to do a function as root such as installing a new sound theme, I have to use the gksu command.  Wondering if this is normal. :confused:

---

### Post by zealibib slaughter on 2011-05-27
in the command line there is no visual feedback when you enter your password the cursor does not move.

---

### Post by oldos2er on 2011-05-28
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by Wim Sturkenboom on 2011-05-28
There is no visual indication of what you type. It's a security 'risk' if you see *** or whatever as people can see how many characters your password is.

So it's normal; type the password and press <enter>

The same will happen at the password prompt of a terminal if you switch to a console (e.g. <ctrl><alt><F2>)

---

### Post by athenroy on 2011-05-28
Thanks, everyone, it's working!  Good policy I guess.

---

