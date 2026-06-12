---
title: "Unable to remove 10GB VirtualBox file from /root!?!"
date: 2012-06-20
forum: General Help
---

### Post by Dn0uk on 2012-06-20
Hello,

After much searching on these forums I've been unable to find a solution  to my problem. I recently installed VirtualBox 4.1 from the software  centre with no issues untill I reset my machine and was greeted with an  error message stating that my graphics card was undetected and I had no  room left on my /root partition. I managed to solve this by removing  some clutter but I noticed that VB had used up 10GB of space so I  removed and purged. Although the system now says VB is not installed and  searches for related files or directories find nothing it's still using  up my space.  If anyone has an idea how to fix this it would be much  appreciated, thanks.

System:

Dell Inspiron 1545
Ubunru 12.04 (Precise Pangolin) x32


Screens:
see attachments


* ls result attached, fails to locate directory

---

### Post by rukiaEnix on 2012-06-20
Could you please post the ls -l of /root/Virtualbox VMs?

---

### Post by SeijiSensei on 2012-06-20
Also make sure there's no /root/.Virtualbox directory by using "sudo ls -la /root".

By the way, if you have your VMs stored in /root, you must have been running as root when you created the virtual machine.  That's generally a bad idea.  You should create VMs as an ordinary user.  You just need to make sure anyone using VirtualBox belongs to the vboxusers group.  Look for the line beginning with "vboxusers" in /etc/group and see if your username is appended at the end of the line.  If not, edit the file as root with sudo and add the usernames of anyone who will be using VirtualBox on this machine separated by commas with no spaces like this:

```
vboxusers:x:122:user1,user2
```

The value 122 may be different on your machine.  Don't worry about that; just add the usernames.

---

### Post by Dn0uk on 2012-06-21
@SeijiSensei

Thanks a lot, Couldn't figure out why it was there but your right I must have ran VB under sudo when I created the machine. Easy fix now I know what a tool I've been :) Thanks again.

---

