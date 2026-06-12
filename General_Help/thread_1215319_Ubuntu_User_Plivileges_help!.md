---
title: "Ubuntu User Plivileges help!"
date: 2009-07-17
forum: General Help
---

### Post by Cityscape on 2009-07-17
Hi guys,

I have Ubuntu 9.04 setup in a VM. It works fine but I can't do lots of things because I don't have Admin privileges. Attached is a message that I get when trying to install VM addons.
A lot of stuff doesn't work without these privileges.

Can someone tell me how to get full privileges of my system?
I need to know because i'll be making Ubuntu my main OS in a few weeks.

Adam :o

---

### Post by lisati on 2009-07-17
What OS are you using as a host for the VM?

---

### Post by Cityscape on 2009-07-17
Host is Windows XP Media Center Edition with SP2.

---

### Post by lisati on 2009-07-17
Apologies for the delay replying: the error message reminded me of something that I've noticed more in Vista than XP, the only workaround I could think of applies to Vista, and my use of VMs is minimal. Anyone else?

---

### Post by litspliff on 2009-07-17
log in as administrator, or run as an administrator....

---

### Post by bodhi.zazen on 2009-07-17
Ubuntu uses sudo

so run the command 

sudo command

enter your log in password when asked

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by litspliff on 2009-07-17
sudo is for ubuntu.....

it is a windows VM app that requires the privelages.

login to your windows box as administrator, or login as usual and use the run-as option to run as administrator

---

### Post by mcduck on 2009-07-17
> **litspliff said:**
> sudo is for ubuntu.....

it is a windows VM app that requires the privelages.

login to your windows box as administrator, or login as usual and use the run-as option to run as administrator

If you actually bother to read the text in the terminal, you'll notice that it's about installing the guest additions for Linux.. ;)

So no, what permissions the user has in the host OS (Windows) have nothing to do with this.

And, like bodhi.zazen already suggested, the solution is to run the command in question using "sudo".

---

### Post by Cityscape on 2009-07-17
But I'm not running the app in Terminal.
So how can i type sudo?

---

### Post by bodhi.zazen on 2009-07-17
Type the same command you did

Now type sudo and then type the command

---

### Post by Cityscape on 2009-07-17
I'm installing by running an executable, I don't think there is a place for me to enter the command!

---

### Post by bodhi.zazen on 2009-07-17
In Ubuntu, open a terminal

Enter your commands

```
cd /media/cdrom
ls
sudo ./VirtualBoxLinuxAdditions-x86.sh
```

Or whatever the exact name of the executable is. You can user Tab-completion

sudo ./V<tab>

x86 = 32 bit arch.
86_64 = 64 bit arch.

---

