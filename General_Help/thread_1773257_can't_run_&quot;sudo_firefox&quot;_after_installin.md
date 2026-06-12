---
title: "can't run &quot;sudo firefox&quot; after installing security updates"
date: 2011-06-01
forum: General Help
---

### Post by bep7987 on 2011-06-01
After installing a number of security updates that were listed in the update manager, I can no longer run the "sudo firefox" command.

I got the error message:[INDENT]No protocol specified
cannot open display
[/INDENT]I found this thread:

[http://ubuntuforums.org/showthread.php?t=590265](http://ubuntuforums.org/showthread.php?t=590265)

through which I found that I am able to run "sudo firefox" after running: [HTML]xhost +localhost[/HTML]I realize this doesn't give you a lot to go on, but I have two questions:

[LIST=1]
[*]Is there a way to view which updates were last installed on my system?
[*]Does anyone have any idea what might cause this problem?
[/LIST]

---

### Post by Dustin2128 on 2011-06-01
Sorry that it's not relevant, but why would you ever run firefox, a *web browser*, with root privillages? That said, if you for some reason want to do this, I'd run 
```
gksu firefox
```
instead. Provides the graphical sudo thing.

---

### Post by snowpine on 2011-06-01
+1, you do NOT want to give the internet root access to your system! There is no reason to run "sudo firefox", "gksu firefox", etc.

---

### Post by pqwoerituytrueiwoq on 2011-06-01
you probably messed up your profile permission using "sudo firefox"
```
sudo chown -R $USER:$USER /home/$USER/.mozilla
```
should fix it

---

### Post by bep7987 on 2011-06-02
I only ran firefox with root privileges to update plugins, but you're right. I think the permissions got screwed up.  I completely removed it from my machine and reinstalled and no longer need root permission to update plugins and addons.

---

