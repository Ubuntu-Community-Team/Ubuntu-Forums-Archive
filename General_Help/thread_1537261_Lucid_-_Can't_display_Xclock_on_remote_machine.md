---
title: "Lucid - Can't display Xclock on remote machine"
date: 2010-07-23
forum: General Help
---

### Post by ktraub on 2010-07-23
Hello All,
I'm having trouble displaying Xwindows programs on a remote machine.

If I run "ssh -X newmachine" and I login and then run a program like xclock, I get the error message:
Error: Can't open display: localhost:10.0

If I run the same command to an anothermachine which is running Ubuntu 8.04 it works fine and xclock displays on my localmachine.

If I run the command "echo $DISPLAY" on newmachine, I see:
localhost:10.0

Also, I have checked and xauth is installed on newmachine.

Can anyone tell me what setting I have to change on Ubuntu 10.04 to allow remote display of Xwindows programs?

Thanks,
-Kev

---

### Post by ktraub on 2010-07-23
Anyone help please?

---

### Post by ktraub on 2010-07-30
No answer yet. Anyone please help!

---

### Post by gmargo on 2010-07-30
That's odd.  I tried all different combinations of 8.04 and 10.04 machines and it all works for me.  The only way I was able to make it fail was by turning off "X11Forwarding" in the target's /etc/ssh/sshd_config file.  But then the DISPLAY variable does not get set.

Random ideas: Is X11Forwarding set to yes on the target machine?  Are you setting DISPLAY in a startup (i.e. .bashrc) file instead of inheriting it from ssh?  Is there anything relevant in $HOME/.ssh/config?  Does anything show up in a log file under /var/log on the initial host (like permission denied)?

One more: check home directory for files owned by root instead of user.

---

### Post by ktraub on 2010-07-30
> **gmargo said:**
> That's odd.  I tried all different combinations of 8.04 and 10.04 machines and it all works for me.  The only way I was able to make it fail was by turning off "X11Forwarding" in the target's /etc/ssh/sshd_config file.  But then the DISPLAY variable does not get set.

Random ideas: Is X11Forwarding set to yes on the target machine?  Are you setting DISPLAY in a startup (i.e. .bashrc) file instead of inheriting it from ssh?  Is there anything relevant in $HOME/.ssh/config?  Does anything show up in a log file under /var/log on the initial host (like permission denied)?

gmargo - X11Forwarding is set to yes on the target machine.
Also, there is no $HOME/.ssh/config nor $HOME/.ssh directory on either the source or the target machines and there are no strange messages showing up in the source machine's /var/log
Also the source machine can display X apps from other machines.
Any other ideas?
One other thing, the target machine is Ubuntu 10.04 64bit.

---

