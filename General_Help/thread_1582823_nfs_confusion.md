---
title: "nfs confusion?"
date: 2010-09-27
forum: General Help
---

### Post by Tweisted on 2010-09-27
Hello everyone, I am trying to setup nfs to mount the drives located on my desktop, to my laptop, so I can watch them on my laptop rather then my desktop. I have both nfs server running on both the desktop and laptop. Desktop is running Arch Linux and the laptop is running Ubuntu, I keep gettinng this error claiming that the devices dont exist. I restarted all the services on both machines and tried editing my fstab/exports on both machines also but still nothing seems to be working, maybe someone can possibly shed some light on this issue

Here is my nfs restart log from my laptop

[http://pastebin.com/irXJj8Eh](http://pastebin.com/irXJj8Eh)

and now desktop

[http://pastebin.com/vAw7pxbg](http://pastebin.com/vAw7pxbg)

here is the export/fstab from my desktop

[http://pastebin.com/UVcEhLqn](http://pastebin.com/UVcEhLqn)

Now for my laptop export/fstab

[http://pastebin.com/xMtV5Gk0](http://pastebin.com/xMtV5Gk0)

There rather the same, but just wanted to include both for each machine just in case there is a distinct difference in something I did.

If there is anything else I can give that would help just let me know. Any help is much appreciated Thank you :)

---

### Post by Zill on 2010-09-27
Tweisted:  Please confirm that you have the following packages (and all recommended dependencies) installed on *both* machines:
nfs-common
nfs-kernel-server
portmap

AIUI, your desktop machine is the server and the laptop is the client.  You only need the exports file on the server machine, with corresponding entries in the client fstab file.

What is the output from the following command when run on the **server** machine (192.168.1.8?)
```
showmount -e 192.168.1.8
```

---

### Post by Tweisted on 2010-09-27
Oh okay, I wasnt sure if I needed the export for both machines or not, I did that just in case. Would that be a reason for error maybe?

And here is the output when I do showmount -e 192.168.1.8

]$ showmount -e 192.168.1.8
clnt_create: RPC: Port mapper failure - Unable to receive: errno 111 (Connection refused)


And thank you for the response much appreciated.

---

### Post by SeijiSensei on 2010-09-27
You don't have portmap installed on the NFS client.  It listens on port 111.  Usually it's a dependency of nfs-common.  Are you sure you have all the packages Zill mentioned on both serve and client?

You don't have any firewalls between these machines, do you?

---

