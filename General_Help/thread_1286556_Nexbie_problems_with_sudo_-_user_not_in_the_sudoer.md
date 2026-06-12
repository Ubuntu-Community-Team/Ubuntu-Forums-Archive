---
title: "Nexbie: problems with sudo - user not in the sudoers file"
date: 2009-10-09
forum: General Help
---

### Post by adameliaz on 2009-10-09
Hi All

I'm a complete newbie as I've just installed Xubuntu 9.04 on my PS3, and I have no experience with any open source software.

Anyways, the installation went fine - no problems. I logged in for the first time - no problem.

When i try to perform almost any task, I'm met by a box where I'm suppose to type my password. I do, and the result is: 

Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

I've been looking around a bit and it seems there might be problem with my sudoers file? When I in the terminal type "sudo synaptic" or any other sudo command, I type my password and  the result is: 

adameliaz is not in the sudoers file.  This incident will be reported.

I've not edited this file - dont know how to.

Typing "groups" in the terminal:

adameliaz cdrom audio admin


Any help appreciated

---

### Post by zvacet on 2009-10-09
Reboot and when grub comes select recovery mode and boot in it.Type

```
adduser adameliaz admin
```

Reboot again but now go for normal boot.See if now you can use sudo.

---

### Post by nothingspecial on 2009-10-09
Nevermind, beaten to it.

---

### Post by adameliaz on 2009-10-09
I am unable to do so:

only root can add a user or group

---

### Post by adameliaz on 2009-10-09
Ah sry. didnt see the grub part. I am working on ps3 - dont think there is a grub menu. if there is how do I access it?

---

### Post by adameliaz on 2009-10-11
bump

---

### Post by s3a on 2009-10-11
Was this account made from another account?

---

### Post by adameliaz on 2009-10-11
I'm not quite sure what you mean. I haven't created any anycounts or added users. its just a clean (or maybe not so clean) installation. I basically haven't made any changes.

Any thoughts?

---

### Post by nothingspecial on 2009-10-11
You need to access a root shell somehow. If your account doesn`t have administrative powers and there is no grub from which you can boot a root shell, I don`t know what you can do.

How did you install ....... I don`t really know what a ps3 is - a games console?

If you used somesort of live disc/usb stick - boot that and look [[COLOR="Magenta"]here[/COLOR]]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by adameliaz on 2009-10-11
Yes, I think you're dead on... And yes a ps3 is a game console aka Play Station 3. The problems is that I can't figure out how to boot to recovery. I'll try to boot from the installation CD...

Is there any way to fix the problem from kboot?

---

### Post by nothingspecial on 2009-10-11
I`m not familiar with kboot but all principals of what you`ve been shown in this thread are the same. Look at the psychocats link I gave you in my last post.

---

### Post by adameliaz on 2009-10-11
Ok,

I know the psinciples of what i'm suppose to do:

1) boot to recorvery

2) Do the repair as shown in psycocats [http://www.psychocats.net/ubuntu/fixsudo#recoverymode](http://www.psychocats.net/ubuntu/fixsudo#recoverymode)

My problem is that I don't know how to boot to recoervery mode on my ps3. There is no grub menu and booting the installation cd just takes me to the installation prgrm. 

You know to boot to recoervery or ps3

I find it all a bit frustrating since I've tried to do everything "by the book":(

Thx for all the help

---

### Post by s3a on 2009-10-11
Actually, try the following:

Boot the live cd (you can use root in there) and do:

***_cd /etc_*** (you will have to slightly modify this command and change /etc to the exact directory of your hard drive to the /etc folder because ubuntu will see your /etc folder as an external hard drive when on the live cd)

sudo gedit sudoers.tmp

it should show:
# User privilege specification
root    ALL=(ALL) ALL

add your username to it:
# User privilege specification
root    ALL=(ALL) ALL
yourusername   ALL=(ALL) ALL

(of course change "yourusername" to whatever your actual user name is)

then save the file and restart the ps3 and see if sudo works.

(Tell me if you find something in my message unclear)

---

