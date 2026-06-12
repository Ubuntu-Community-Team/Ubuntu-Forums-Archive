---
title: "Shutting Down at inopportune moments"
date: 2011-01-03
forum: General Help
---

### Post by Sennacherib on 2011-01-03
I'm not sure where to start sorting this out, so any help would be appreciated.  Basically Ubuntu shuts down randomly.  The only information I can glean is from the shut down screen when it says Broadcast Message received (unknown).  Is there a way I can capture the processes information for a better diagnostic?

---

### Post by houseworkshy on 2011-01-03
First people will need to know about your system.  The easy way is to install something called "sysinfo" this can be done either via System>Administration>synaptic package manager OR via the terminal ( Applications>Accesories>Terminal ) with the command "sudo apt-get install sysinfo" .  Either way it will install after you bung in the password.  
Once that is done you will have an entry for it in Applications>system tools> sysinfo.  Just run it and under "file" seclect "save".  This will produce a text document which will have the nessesary info.  You could then attach this to a post here.
One thing which can cause random shutdowns is heat.  A major cause of heat can be dust in the machine, one should really clean them twice a year using compressed air, more if one smokes.
There is a tiny program one can install to take a look at heat, this post has details  [http://ubuntuforums.org/showthread.php?t=1494180](http://ubuntuforums.org/showthread.php?t=1494180)
You could also take a look at the log file viewer  which can be found under System>Admin

Good luck

---

