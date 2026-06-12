---
title: "Messed up my file permissions"
date: 2009-11-29
forum: General Help
---

### Post by neon401 on 2009-11-29
Hi, I managed to do *sudo chmod 0644 /* and now I can't do anything at all.

Is there any way I can solve this without reinstalling?

---

### Post by Roasted on 2009-11-29
Edited. Please ignore.

---

### Post by Cytochromec on 2009-11-29
I never figured out what that extra number is for (the 7 above). I know mine is not a 7, but you want something like drwx------  which indicates read, write, and execute privileges for the owner and not group or other users.  Try sudo chmod o+rwx maybe if the above doesnt help, which means add permissions read, write, and execute to owner only. None of those commands are exact, you might want to google some more info about permissions.

---

### Post by neon401 on 2009-11-29
The problem is, I don't have access to sudo anymore.

---

### Post by Cytochromec on 2009-11-29
> **neon401 said:**
> The problem is, I don't have access to sudo anymore.

In the terminal type su then enter. Does it prompt you for a password? Do you know that password? If you do, enter it and you will be given root privileges.

---

### Post by lswb on 2009-11-29
As long as you didn't use the -R option to chmod it should be easy enough to fix. If you can't sudo, then reboot and from the grub menu, select "recovery mode" then select "root shell" (Or boot from a live CD and mount your hard drive, if you need help with that post again)

Once at the shell prompt, use the command "chmod 755 /" 

If you booted from a live CD and mounted the hard drive, substitute the mountpoint for '/'

---

### Post by Roasted on 2009-11-29
> **lswb said:**
> As long as you didn't use the -R option to chmod it should be easy enough to fix. If you can't sudo, then reboot and from the grub menu, select "recovery mode" then select "root shell" (Or boot from a live CD and mount your hard drive, if you need help with that post again)

Once at the shell prompt, use the command "chmod 755 /" 

If you booted from a live CD and mounted the hard drive, substitute the mountpoint for '/'

I don't understand how 755 will help him.

I'm working on a fresh, unaltered install and mine is 700.

---

### Post by lswb on 2009-11-29
> **Roasted said:**
> I don't understand how 755 will help him.

I'm working on a fresh, unaltered install and mine is 700.

The OP ran his command on /, not /root. Take a look:
```

$ ls -ld /
drwxr-xr-x 23 root root 4096 2009-11-24 18:56 /
$ ls -ld /root
drwx------ 27 root root 4096 2009-11-11 10:46 /root
$ 

```

---

### Post by scouser73 on 2009-11-30
> **neon401 said:**
> Hi, I managed to do *sudo chmod 0644 /* and now I can't do anything at all.

Is there any way I can solve this without reinstalling?

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by Roasted on 2009-11-30
> **lswb said:**
> The OP ran his command on /, not /root. Take a look:
```

$ ls -ld /
drwxr-xr-x 23 root root 4096 2009-11-24 18:56 /
$ ls -ld /root
drwx------ 27 root root 4096 2009-11-11 10:46 /root
$ 

```

You, my friend, are absolutely right. I don't know why I didn't pick up on it sooner.

So I was right, while at the same time being wrong. Haaaa - Life is good. 

**IGNORE MY POST ABOVE. 700 is not what permissions you want.**

---

