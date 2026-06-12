---
title: "run &quot;su/sudo&quot; in a script"
date: 2010-04-10
forum: General Help
---

### Post by dheerajkabra on 2010-04-10
Here some background:

I am running Ubuntu 9.10 in virtualbox. Everytime I log in, I have to run two commands (route and mount) as root. So I do "su" and run it . 
I am trying to automate this process using a script. Once I have the script handy, then I will add it to the startup and my commands will get executed automatically.

I need your help to write this script.

**How to use "su" or "sudo" in a script? I tried various option, but the scripts asks for the password and doesn't proceed until I enter it. How can I pass the password to "su" or "sudo" in this scripts.**

I am least bothered about the security as this an ubuntu VM running on my laptop and I am the only user.

Thanks.
-Dheeraj.

---

### Post by undecim on 2010-04-10
Do you need to run these commands every time you log into the VM, or every time the VM boots?

Also, whatever you are mounting with the mount command... Is there a reason it can't be put in /etc/fstab?

EDIT: For setting the route on boot, have a look at #6 here: [http://ubuntuforums.org/showthread.php?t=38621](http://ubuntuforums.org/showthread.php?t=38621)

---

### Post by dheerajkabra on 2010-04-10
@undecim, that was a lightspeed fast reply. Many thanks.

I got it working, here is the solution:

I added my user to the "admin" group and then made following entry in the sudoers file

**%admin ALL=NOPASSWD: ALL**

now my script when ran as a user does not ask for the password and runs fine.

Here is the information:

[B]# grep ^admin /etc/group
admin:x:115:abcd[/B]

[B]# grep admin /etc/sudoers 
%admin ALL=NOPASSWD: ALL[/B]

and here is my script:
[B]
# cat startup 
#!/bin/bash
sudo mount -t vboxsf windows_folder /mnt
sudo route add default gw 192.168.1.1[/B]


Cheers !!

---

### Post by dheerajkabra on 2010-04-10
damn that smiley

---

