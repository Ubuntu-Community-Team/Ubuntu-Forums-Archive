---
title: "monitoring process started remotely"
date: 2010-03-21
forum: General Help
---

### Post by ub007 on 2010-03-21
I started a 'dd copyíng' of one disk drive to another. Both disks are hooked to a remote machine and I initiated the dd command by ssh_ing into it.
I have to shut down the box from which i initiated the ssh session.
Is there any way I can keep monitoring the status (shell script)of the copy process, ie know when the dd command terminates and whether it terminated successfully .
I could then ssh into the macine from another box and still know the status.
any ideas?

David

---

### Post by cjhabs on 2010-03-21
> **ub007 said:**
> I started a 'dd copyíng' of one disk drive to another. Both disks are hooked to a remote machine and I initiated the dd command by ssh_ing into it.
I have to shut down the box from which i initiated the ssh session.
Is there any way I can keep monitoring the status (shell script)of the copy process, ie know when the dd command terminates and whether it terminated successfully .
I could then ssh into the macine from another box and still know the status.
any ideas?

David

The "screen" command allows this - although you will need to restart the process within screen. see the link below:

[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

