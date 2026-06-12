---
title: "devilspie problem"
date: 2010-09-22
forum: General Help
---

### Post by dld on 2010-09-22
This is a nuisance problem.   I have used devilspie for several years to place and size windows in workspaces at startup.  Programming devilspie is not trivial, and sometimes apps change their class or name.  I can handle those things.  But:

On startup often Firefox starts in workspace 1 rather than 3, where it belongs.  So I close it and restart it, or move it.  I am tired of doing those things every time I boot Ubuntu.  Occasionlly Seamonkey windows start in 1 rather than workspace 2.

Are these windows being built before devilspie is started, or what????  And what do I do about it?

---

### Post by dodo3773 on 2010-10-17
> **dld said:**
> This is a nuisance problem.   I have used devilspie for several years to place and size windows in workspaces at startup.  Programming devilspie is not trivial, and sometimes apps change their class or name.  I can handle those things.  But:

On startup often Firefox starts in workspace 1 rather than 3, where it belongs.  So I close it and restart it, or move it.  I am tired of doing those things every time I boot Ubuntu.  Occasionlly Seamonkey windows start in 1 rather than workspace 2.

Are these windows being built before devilspie is started, or what????  And what do I do about it?

I messed with this program all morning. The way I got it to work for me was with

     
     ```
devilspie -a 
```That way if the applications load first then devilspie will still apply your settings afterwards. I also wrote this script for myself

     ```

#!/bin/bash  

evolution & deluge & firefox & sleep 15 && devilspie -a &  sleep 20 && pkill -f "devilspie -a"  
exit

```In this script the applications load first, then the script sleeps, then devilspie loads, then it sleeps again and finally kills devilspie.  I only use it initially at startup. Also, I do not run it as a startup  application either. Oh, and for me I found that it was better to load  all of your rules in a single .ds file in the .devilspie folder instead  of multiple files all with one rule each. I hope that helps.
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9989195")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=9989195")

---

### Post by dld on 2010-11-04
I tried the -a option for a week.  It doesn't make devilspie any more consistent than it was.  I am reluctant to try your script.  I don't want to stop devilpie as some controlled windows get opened and closed throughout the day.

---

### Post by Jose Catre-Vandis on 2010-11-04
I'm guessing this is a "when" related thing, with apps loading before devilspie can get hold of them.

I would create your startup script with some "sleep" in it, either for the whole script, or for individual applications or try starting apps in a different order.

I take it you don't have Compiz running? (if you do, why not try the compiz feature for placing windows)

You could edit dodo's script to remove the bit about killing devilspie:
```
#!/bin/bash  
evolution & deluge & firefox & sleep 15 && devilspie -a  
exit
```

I would probably work it round the other way:
```
#!/bin/bash
devilspie;
sleep 15;
evolution;
deluge;
firefox;
exit
```

---

