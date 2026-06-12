---
title: "Xubuntu doesnt recognize my password"
date: 2010-03-02
forum: General Help
---

### Post by Lord Maiden on 2010-03-02
Hello, when xbuntu starts up and the username and password box shows up, I enter my password and it says authentication failure. Is there a way to change my password so i can login?

---

### Post by Lord Maiden on 2010-03-02
anyone?

---

### Post by sisco311 on 2010-03-02
You can reset it in the *Recovery Mode*:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Lord Maiden on 2010-03-02
i dont have that option when selecting. There are four lines:

Linux....
old....
gameos....
shell...
and something else. But nothing about recovery mode.

---

### Post by sisco311 on 2010-03-02
> **Lord Maiden said:**
> i dont have that option when selecting. There are four lines:

Linux....
old....
gameos....
shell...
and something else. But nothing about recovery mode.

Oh, you are running Xubuntu on a PS3, right?

At the kboot prompt start a BusyBox shell, remount the root partition read/write, chroot into ubuntu & change your password with the passwd command:
[http://psubuntu.com/wiki/EditingFromKboot](http://psubuntu.com/wiki/EditingFromKboot)

At step 4 type:
```
passwd **username**
```
to reset your password. Replace **username** with your login name.

---

### Post by Lord Maiden on 2010-03-02
Yup, I'm running it on a my PS3 using petitboot. I tried what you suggested but it doesn't even recognize the first line starting with umount.

---

### Post by sisco311 on 2010-03-02
According to their [home page]("http://ozlabs.org/~jk/projects/petitboot/"), you have to press Alt+F1 and the partition is already mounted under /var/tmp/mnt/ps3da1. So try to chroot into Ubuntu:
```
chroot /var/tmp/mnt/ps3da1 bash
```
and change the password:
```
passwd user
```

Alternatively, you can try kexec to boot in *Recovery Mode*:
```
  kexec -f --append="root=/dev/ps3da1 ro single" /var/tmp/mnt/ps3da1/boot/vmlinuz-**XYZ**
```
where **XYZ** is the version number of the kernel.

To get the version of the kernel, type
```
ls /var/tmp/mnt/ps3da1/boot/vmlinuz*
```

---

### Post by Lord Maiden on 2010-03-02
I will try this. Thanks.

---

### Post by Lord Maiden on 2010-03-03
My password does not work. I've tried a ton of things suggested and I still can't login to ubuntu. I'm running it on a ps3.

---

### Post by hansdown on 2010-03-03
Hi Lord Maiden.

It is likely asking for your user name first. Fill that in, and it will ask for the password.

---

### Post by Lord Maiden on 2010-03-03
Yes, I know. My problem is after typing in my password, it gives me an "authentication failure". When I try to change it by "passwd username" in the shell, it tells me user not found. That's after I've booted up ubuntu, get to the login box with my username already there. It just doesn't recognize my password. I want to use ubuntu and I can't.

And it sucks.

---

### Post by hansdown on 2010-03-03
Sorry about that.

You can try replacing the password with a new one.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Lord Maiden on 2010-03-03
No apologies needed.

I've done what you have suggested before. There is no GRUB screen. When I'm in the shell - "root@ps3-linux/#:" Is already there. So when I type "passwd (my username) It looks like - 

root@ps3-linux/#: passwd username

username can not be found.

I was able to change the password for root but it gets me nowhere after ubuntu boots up and it's time to put in the password. I simply cannot login.

---

### Post by sigurnjak on 2010-03-03
As root create new user and see what happens . Maybe your install is borked .

---

### Post by Lord Maiden on 2010-03-03
OK. How do I do that? When you say "as root," are you talking about when you are in a shell? Right now it's BusyBox v1.14.4.

---

### Post by alexandari on 2010-03-03
```
 su 
```
```

useradd "username"
passwd "username"


```

---

### Post by Lord Maiden on 2010-03-03
OK. I will try. Thank you.

---

### Post by Lord Maiden on 2010-03-03
Nope. It doesn't work. I type in su and I get:

su/bin/ash: su: not found

This sucks.

---

### Post by Lord Maiden on 2010-03-03
when I go the shell, I'm looking at this:

BusyBox v1.14.4 built in shell (ash)
root@ps3-linux:/#

Has anyone used this?

---

### Post by alexandari on 2010-03-03
Wow wait. the "su" command is to log in as root. But I see here "**root@ps3-linux/#: passwd username**" <--- you wrote this,and you are actually under root...sorry for not seeing this. So just type "**useradd** username" and...see what happens.

---

### Post by Lord Maiden on 2010-03-03
I did. Nothing happens. I get something like: useradd not found.

---

### Post by Lord Maiden on 2010-03-03
Tell me I'm going to have to reinstall this thing. Crap.

---

### Post by fluffman86 on 2010-03-03
Your installation is pretty much hosed. Reinstall.

---

### Post by sisco311 on 2010-03-03
> **Lord Maiden said:**
> Tell me I'm going to have to reinstall this thing. Crap.

At the petitboot console you are not logged in in Ubuntu. You have to chroot into it first:
```
chroot /var/tmp/mnt/ps3da1 bash
```
Then change the password:
```
passwd username
```

Please post the exact error message in case you get one.

EDIT: Can you boot a Live CD or USB ?

---

### Post by Sef on 2010-03-03
Merged duplicate threads.   If you wish to easily follow your thread then do this: Thread Tools > Subscribe to this thread.   Then to follow it:  Quick Links > Subscribed Threads.  Alternatively before clicking submit reply, go down to Thread Subscription and set it to the type of desired subscription.

---

### Post by Lord Maiden on 2010-03-03
> **sisco311 said:**
> At the petitboot console you are not logged in in Ubuntu. You have to chroot into it first:
```
chroot /var/tmp/mnt/ps3da1 bash
```Then change the password:
```
passwd username
```Please post the exact error message in case you get one.

EDIT: Can you boot a Live CD or USB ?

Yup, I did that already. When I try to chroot i get a message telling me the file or directory cant be found.

You know what? I did install petitboot after I installed ubuntu. Maybe with petitboot installed, I should boot with the CD and reinstall?

Yes, I do have usb. I have a stick with 4gb and two ports.

Sorry if I'm a pain in the ***. I'm really new to Linux but I am willing to learn. I like a challenge.

---

### Post by sisco311 on 2010-03-03
> **Lord Maiden said:**
> Yup, I did that already. When I try to chroot i get a message telling me the file or directory cant be found.

You know what? I did install petitboot after I installed ubuntu. Maybe with petitboot installed, I should boot with the CD and reinstall?

Yes, I do have usb. I have a stick with 4gb and two ports.

Sorry if I'm a pain in the ***. I'm really new to Linux but I am willing to learn. I like a challenge.

So the chroot command returns something like:
```
chroot: cannot change root directory to /var/tmp/mnt/ps3da1: No such file or directory
```right?

That means that Ubuntu's root partition is not mounted on /var/tmp/mnt/ps3da1.

Type:
```
mount
```
to list the mounted partitions.

If the partition is mounted somewhere, the command should return something like:
```
/dev/ps3da1 on **/mount/point** type ext3 ...
```
where the bold text is the mount point of the partition.

Then run:
```
chroot **/mount/point** bash
```
and
```
passwd username
exit
exit
```
and you are done.

If the partition is not mounted, then you have to mount it first:

list the partitions:
```
fdisk -l
```
the output should look like this:
```
...
   Device Boot      Start         End      Blocks   Id  System
/dev/ps3da1               1        1305    10482381   83  **Linux**
/dev/ps3da2            1306        2614    10514542+  **whatever**
...

```

create the mount point:
```
mkdir /ubuntu
```
assuming that /dev/ps3da1 is the Linux partition type:
```
mount -o rw -t ext3 /dev/ps3da1 /ubuntu
``` 
to mount it.

chroot into ubuntu & change the password:
```
chroot /ubuntu bash
passwd username
exit
exit
```

---

### Post by Lord Maiden on 2010-03-03
OK, I'll try that and post the outcome, good or bad. 

Thanks for helping. That last post made me see how this stuff works a little better.

You had the first one right, BTW. I would have to write everything down because the CPU is downstairs and the PS3 is upstairs.

---

### Post by Lord Maiden on 2010-03-03
OK. I get to where is asks me to put in a new UNIX password. When I do I get:

Authentication token manipulation error

Damn.

---

### Post by sisco311 on 2010-03-03
> **Lord Maiden said:**
> OK. I get to where is asks me to put in a new UNIX password. When I do I get:

Authentication token manipulation error

Damn.

Uh, try to create a new user:
```
adduser uname
```
add the user to the admin group:
```
gpasswd -a uname admin
```

Reboot, login as uname & post the content of the /etc/passwd and /etc/shadow file.

```
cat /etc/passwd
sudo cat /etc/shadow
```

EDIT: Do you have a /etc/shadow file on your system at all?

```
cat /etc/shadow
```
If not try to generate a new one:
```
pwconv
```
Lock the root password & set one for your user:
```
usermod -p ! root
passwd username
```

---

### Post by Lord Maiden on 2010-03-04
It's all good now. I reinstalled and now it works perfectly. Thanks for the help.

---

### Post by hansdown on 2010-03-04
Glad you got it going Lord Maiden.

---

### Post by Lord Maiden on 2010-03-04
Yeah, this is awesome. Firefox is 10 times better than the PS3's browser. I was playing around with it last night and when I get a better grasp on things, I'll probably put Linux on my main PC.

---

