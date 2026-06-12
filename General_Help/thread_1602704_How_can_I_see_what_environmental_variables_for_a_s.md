---
title: "How can I see what environmental variables for a specific application are set to?"
date: 2010-10-21
forum: General Help
---

### Post by Buttons840 on 2010-10-21
First, I will point out that I have read this Ubuntu documentation on Environmental Variables: [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)  However, I still have a few questions.

My general question is how can I determine what environmental variables are set to?  I will illustrate with two examples.

1) When starting a Python interpreter the PYTHONPATH environmental variable is used to determine the python path will be (sys.path from within python).  I run a printenv command, and see that there is no PYTHONPATH set, then I start python and pring sys.path and there is the usual python path listed.  Where did this come from?  I then "export PYTHONPATH=/" from the terminal and restart python and print sys.path again, and it has no changed.  It appears the environmental variable was not used.

2) I'm working with Tomcat6, and I see frequent references to $CATALINA_HOME, etc.  How can I determine what these values are set to?  They don't appear when I printenv.

Thank you.

---

### Post by kfishy on 2010-10-21
In the Python man page, it says that the default search path for the Python installation is always appended to $PYTHONPATH irregardless of whether it was set already. That probably explains the discrepancy.

---

### Post by Buttons840 on 2010-10-21
Thanks, but I'm more interested in env vars in general rather than python specific details.

Lets say I set a PYTHONPATH in .pam_environment (which I have done in the past).  My shells don't show $PYTHONPATH as having any value, so where is the real PYTHONPATH env I set living?  Probably in the shell instance (I don't know the correct term) that is running the desktop environment?  If so, how can I see the env vars defined there?

---

### Post by kfishy on 2010-10-21
If you've set it in .pam_environment then the variable applies to an instance of your login session. So if you open up gnome-terminal once you've logged in, you can see if the variable is set by running "pam_getenv NAME" or "echo $NAME".

Make sure you're formatting .pam_environment properly, though. It's set differently from .profile or .bashrc; instead the format is ```
NAME    DEFAULT=VALUE
```

---

