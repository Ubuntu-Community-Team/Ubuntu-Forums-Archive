---
title: "Default browser for 'environment'"
date: 2006-06-04
forum: General Help
---

### Post by siplus on 2006-06-04
I just installed Dapper on my computer this morning, and I am for the first time setting up BOINC ([http://boinc.berkeley.edu](http://boinc.berkeley.edu))  for two distributed computing projects.

It was easy to set up, save one issue: it can't open websites. This particular program is very web-site oriented and although it does give a url, i can't c/p it (and they are fairly lengthy urls)

I took a screenshot of the error message and uploaded it to my site here (showing the smallest url i could find in the program): [http://wb.skudd.com/siplus/BOINC_Manager_Browser.png](http://wb.skudd.com/siplus/BOINC_Manager_Browser.png)

I set GNOME and KDE's default browser explicitly to firefox, but it still doesn't recognise that i set a default browser. I looked for any sort of setting in the options of the program, but they were surprisingly limited.

Any help would be appreciated

---

### Post by bjc on 2006-06-04
(Disclaimer: I haven't used BOINC).

It's looking for the environment variable $BROWSER to contain the path to your web browser. So, assume you start the program with the command *bonic*, and you have Firefox installed, try this from a terminal:
```

BROWSER=`which firefox` bonic

```

If that works, we can set that variable permanently.

---

### Post by siplus on 2006-06-04
I tried the command in the program's directory:

BROWSER=`which firefox` ./boincmgr

and it worked fine, thanks!

Now i'm going to try to make a shortcut to it on the gnome-panel, and in the command section 

```
BROWSER=`which firefox` ./home/siplus/BOINC/boincmgr
```
and that's not a valid command (where it worked in the terminal). Any advice for correcting this shortcut button?

---

### Post by TheCat on 2006-06-05
I have the same problem.  I installed boinc and boincmgr using Synaptic and it automatically opens a terminal browser (Lynx?) instead of Firefox.  It installed boinc and boincmgr in /usr/bin.  Using this command from terminal works:

BROWSER=`which firefox` bonic

but I can't get that to work using the installed *BOINC Manager* launcher in Applications \ Accessories.

---

### Post by jocko on 2006-06-05
Try making a simple script for starting it:
```
gedit ~/startboincmgr
```
Paste the command into the new file, save and close it (the file will end up in your home directory).
Make the file executable:
```
chmod 755 ~/startboincmgr
```
Try if it works by running ```
./startboincmgr
``` in your home directory.
Then you should be able to make a shortcut pointing to this script.

---

### Post by TheCat on 2006-06-05
Yeah, that would work, but it would be nicer if the package maintainer fixed the package so it respected the default browser setting.

How do we send a message to the package maintainer?

---

### Post by TheCat on 2006-06-06
I reported the bug.

[https://launchpad.net/distros/ubuntu/+source/boinc/+bug/48766](https://launchpad.net/distros/ubuntu/+source/boinc/+bug/48766)

---

