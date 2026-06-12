---
title: "compiz-fusion screenlet not loading correctly"
date: 2009-11-18
forum: General Help
---

### Post by fokuslee on 2009-11-18
Hi all i am runing some screenlets with compiz fusion, they will not load correctly at startup i have to restart compiz via fusion-icon every time i boot up my comp. 
Is there a way to avoid doing this? ie tell screenlet to load way later after compiz is fully started?

---

### Post by Giblet5 on 2009-11-18
It sounds like you're not allowed to save configuration information. That would make compiz not start by default.

Open a terminal window (Applications -> Accessories -> Terminal) and enter the following Really Long command line:
```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

That will set reasonable permissions and ownership on every file in your home directory.

Log off. Log in.

Set up compiz via System -> Preferences -> Appearance. Click the Effects tab, select extra. Quit the tool.

Set up compiz the way you like it.

Now whenever you log in, compiz should start about the same time that screenlets load and everything should be as you expect.

---

