---
title: "priorities could fix crash?"
date: 2006-03-31
forum: General Help
---

### Post by Huffers on 2006-03-31
I left my computer idle for several hours with the CDT 'C Development Tools' for Eclipse running, then when I returned Ubuntu was exceptionally slow and the hard drive was going nuts.

I think the CDT indexer had gone crazy (possibly spawning lots of subprocesses) and demanded loads of cpu and hard drive resources. 

When I pressed ctrl+alt+f1 to login with a tty, the login timed out after 60 seconds. So I couldn't kill CDT, so I had to hard reboot.

Now I know this is CDT's problem and not Ubuntu's, but similar situations have occurred with other overrunning programs. Could this situation be fixed if whatever process controls the tty logins (and subsequent shell, commands, etc) always recieves a fixed portion of the system resources, no matter how many other processes are running. And could this be done by altering their priorities?

I could run CDT with 'nice', but it's hard to predict which programs are going to do this.

---

