---
title: "Shell permissions"
date: 2010-08-31
forum: General Help
---

### Post by Diderik From on 2010-08-31
I'm running scientific software on two different machines both with Ubuntu 10.04 64bit. I've updated both OS and the program on both workstations. On one I get an error message, whereas on the other it works fine. The offending command in the program is:
```
{subjdir}.bedpostX/monitor&
```Both in bash, on one workstation I get:
```
lethe:..path> /full/path/to....bedpostX/monitor
/full/path/to....bedpostX/monitor: Permission denied.
```Whereas on the other it works fine (i.e. the script is executed). I have tried this on the exact same file. On the local machine, there is the above error message, whereas on the machine where the disk is NFS mounted it works fine. And of course, I have execute permissions. Is there some basic configuration I have missed?

Please help!

Edit: I sort of solved this by changing
```
{subjdir}.bedpostX/monitor&
```to
```
. {subjdir}.bedpostX/monitor&
```but still I'd like to know what causes such different behaviour.

---

### Post by Brandon Williams on 2010-08-31
What is the very first line of the script? It should specify the interpreter for the script. If you can source the script (that's what the '.' does), then I expect that the interpreter specified in the script is not the same as the shell you actually run for interactive use.

---

### Post by Diderik From on 2010-09-01
Thanks for your reply!

The interpreter is 'sh', i.e. the first line is #!/bin/sh.

On both machines I slip into bash before executing. I might be mistaken, but I thought bash was backwards compatible with sh. (There is a quite some configuration put into /root/.bashrc upon installation so I do not think I can execute this program in sh because it is not configured.) On the other hand, I tried changing the interpreter (the first line) to bash, but it made no difference.

Thanks!

---

### Post by slakkie on 2010-09-01
/bin/sh could be dash and/or any other shell. That's why you could have these issues.

---

### Post by Brandon Williams on 2010-09-01
If the specified interpreter is /bin/sh, then that's unlikely to be the problem, since any ubuntu machines will always have a "/bin/sh" that is executable ... lots of things would be broken if that were not true.

Re: bash and posix shell compatibility, bash can run a posix compliant shell script, but a posix shell (such as dash, the ubuntu default /bin/sh) cannot necessarily run a bash script. If you use features that are in bash and not in posix, then you must specify bash as the interpreter. This issue would not lead to a "permission denied" error for the script, though.

Are you absolutely certain that the permissions are correct? From what you describe, the only explanation that makes sense is that the script does not have execute permission for the correct user. What is the output of 'stat /full/path/to/file' on both machines?

---

### Post by spjackson on 2010-09-01
Since most of the obvious things have been checked, I'll throw another one into the mix. What does 'mount' show for the partition in question on the machine where you get the error? In particular, is it mounted with the 'noexec' option?

---

### Post by scorp123 on 2010-09-01
> **Brandon Williams said:**
> If the specified interpreter is /bin/sh, then that's unlikely to be the problem **Strongly disagree.**

Since a few releases **/bin/sh** points to **_d_ash** and not **_b_ash** anymore. And I've already run into numerous issues where dash proved to be the culprit.

Example from my system:
```
> ls -al /bin/sh
lrwxrwxrwx 1 root root 4 2010-05-14 11:41 /bin/sh -> dash

```

How to get rid of dash and use bash again:
```
sudo dpkg-reconfigure dash
```

... a dialogue will pop-up and ask if you want /bin/sh point to dash ... say "No" and it will point to bash again.

This solved many problems in several shell scripts for me.

---

### Post by Diderik From on 2010-09-02
Thank you all for input!

Re: Permissions. Yes! Everyone has execute and read permissions. Also, my user name, uid and gid are the same on the two machines.

Re: What is the output of 'stat /full/path/to/file' on both machines?
Machine where it works ok and file is NFS mounted:
```
  File: `/.../monitor'
  Size: 711           Blocks: 8          IO Block: 1048576 regular file
Device: 18h/24d    Inode: 7239751     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/     per)   Gid: ( 1000/     per)
Access: 2010-09-02 10:22:20.269894697 +0200
Modify: 2010-08-31 20:07:19.349894451 +0200
Change: 2010-08-31 20:07:19.349894451 +0200

```Machine where the file is locally and I get 'Permission denied':
```
  File: `/.../monitor'
  Size: 711           Blocks: 8          IO Block: 4096   regular file
Device: 811h/2065d    Inode: 7239751     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/     per)   Gid: ( 1000/     per)
Access: 2010-09-02 10:22:20.269894697 +0200
Modify: 2010-08-31 20:07:19.349894451 +0200
Change: 2010-08-31 20:07:19.349894451 +0200

```Re: What does 'mount' show for the partition in question on the machine where you get the error?
```
(rw,noexec,nosuid,nodev)
```on the offending machine
and
```
(rw,hard,intr,addr=10.42.43.1)
```on the nfs mounted machine.

It seems we've located the problem!

The main program is installed on the startup drive whereas the files it is working on resides on an internal hard drive automounted from fstab with 'default' options. The main program then creates a small script and places it with the files. It is this file that will not execute. I'll change my fstab and add 'exec' to the options. It a bit weird though that when the drive is mounted as no-exec you can just put a dot in front of what you want to execute.

I'd like to remount the drive with exec permissions and test immediately, but I just spent ages configuring sun gridengine on these two machines and they are in the middle of a major batch process.

Thank you all! This was educational.

---

### Post by Brandon Williams on 2010-09-02
> **scorp123 said:**
> **Strongly disagree.**

Since a few releases **/bin/sh** points to **_d_ash** and not **_b_ash** anymore. And I've already run into numerous issues where dash proved to be the culprit.


A script that specifies /bin/sh as the interpreter should not depend upon bash-specific functionality. It should use only functionality that is specified in [the POSIX specification](http://www.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02) of the shell command language. If you're trying to write portable scripts, then it's important to stick to the standard and use a strictly POSIX compliant interpreter. Solving the problems you describe by switching to a different interpreter is only appropriate for those who are not concerned about portability.

That said, my point was that you would not see "permission denied" errors as a result of running a bash script with dash. In that case, you would see syntax errors.

---

### Post by Diderik From on 2010-09-03
I'm afraid changng mount options in fstab does not work.

I changed:
```
/dev/sdb1    /media/SDB_EXT4  ext4    default,user    0        2
```to

```
/dev/sdb1    /media/SDB_EXT4  ext4    defaults,user,exec     0        2
```but 'mount' still gives:

```
/dev/sdb1 on /media/SDB_EXT4 type ext4 (rw,noexec,nosuid,nodev)
```What am I missing?

Edit:
For some reason 'sudo mount -a' was not enough. After a reboot 'noexec' did not show in 'mount'

And yes, the program works fine now.
Thanks!

---

