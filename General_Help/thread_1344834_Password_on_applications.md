---
title: "Password on applications"
date: 2009-12-03
forum: General Help
---

### Post by Goggeli on 2009-12-03
Hello!

I have been googeling for a while, and found no answer to my question. So what I want to do, is to put a password on a launcher or on the whole application itself. Is it possible to set a passwordblock on applications or launchers? And I do not want to launch anything as root.

---

### Post by nikhilbhardwaj on 2009-12-03
mmmmmm
noting comes to mind to fit this

---

### Post by kamallneet on 2009-12-03
I can't think of a user-friendly solution either :)
But you can create a new user, let's say *otheruser*. Ubuntu will, by default, create a new group also, named *otheruser*.

One time setup:
sudo chgrp otheruser /path/to/executable_that_you_want_to_protect
#allow group member to execute
sudo chmod g+x /path/to/executable_that_you_want_to_protect
#don't allow others to execute
sudo chmod o-x /path/to/executable_that_you_want_to_protect

Then, for running, you have to do:
su otheruser -c executable_that_you_want_to_protect
..and give the password you set for otheruser while creating it.

The program will be run as otheruser, and by default, will not have permission over files in normal user's home directory! But this can be worked around too!

---

