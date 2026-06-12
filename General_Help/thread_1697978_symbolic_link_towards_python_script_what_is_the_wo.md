---
title: "symbolic link towards python script: what is the working folder?"
date: 2011-03-01
forum: General Help
---

### Post by axeoth on 2011-03-01
Hello everybody,

 I have a python script (namely, the waf building system: [http://code.google.com/p/waf/](http://code.google.com/p/waf/)) who requires to be copied into a folder with write access.

 The waf script is in the /home/user/waf folder and it works very well if launched with /home/user/waf/waf or with ./waf.

 However, I have a symbolic link ("ln -s") in the /usr/bin directory. When launching with "waf", the script is called, but warns that the /usr/bin folder is not writeable (which is true).

 Why when launching the python script through the symbolic link the former thinks that its folder is /usr/bin (the directory where the symbolic link lays in) and not the /home/user/waf/waf, the *actual* folder where the python script resides in? And how to change?

 Thanks everybody.

---

### Post by axeoth on 2011-03-01
i just noted that the shebang line of the waf script is "#!/usr/bin/env python" and not "/usr/bin/python" as i was expecting. however, it seems that "#!/usr/bin/env python" simply looks on path for the python interpreter and then launches the script.

---

### Post by axeoth on 2011-03-01
to those who may read: the solution that i found so far is to use os.path.realpath() instead of os.path.abspath() in the waf (python) script.

unfortunately, this still requires editing the python script. and i still do not know how to avoid that.

---

### Post by DaithiF on 2011-03-01
what is your goal, to be able to invoke waf without specifying a path, ie. just by calling waf?

a couple of options:
1. define an alias in your .bashrc
alias waf="python /home/you/waf/waf'

2. rather than putting a symbolic link into /usr/local/bin put a  wrapper script there instead -- ie. a 1-liner like so:
python /home/you/waf/waf

---

### Post by axeoth on 2011-03-02
Thank you, DaithiF.

Actually, I have implemented both the alias and wrapper script solutions, and they work. But it is my goal to have a symbolic link to launch that python script (waf).

Editing the script and calling os.path.realpath() instead of os.path.abspath() works.

I just wanted to know if there is a solution which both 1.) uses a symbolic link and 2.) does not require editing the python script.

Anyway, maybe I should suggest to people in the waf to use realpath() instead of abspath().

I will mark this as solved, even if not 100% true.

Thanks!

PS+OT: You have the nicest avatar.

---

