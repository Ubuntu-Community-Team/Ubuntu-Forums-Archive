---
title: "Specifying directory for .ssh login"
date: 2011-04-16
forum: General Help
---

### Post by Leo Simon on 2011-04-16
I want to be able to specify a directory other than $HOME when I log in via ssh.    A clunky but almost-workable way to do this would seem to be to first rcp the cd command to ~/.ssh/rc, then ssh in.  I'm able to change directory this way, but by the time I reach the shell prompt, the directory has been changed back to $HOME.   I've verified that ssh must be running some script between when it runs my ~/.ssh/rc and when it runs my .login file.    I thought this program must be /etc/sshrc, which everybody talks about on the web, but this file doesn't exist on my machine.

Can anybody advise what script this would be please?

I'm running ubuntu hardy.

Thanks for your help!

---

