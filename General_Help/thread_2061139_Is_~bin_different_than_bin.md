---
title: "Is ~/bin different than /bin?"
date: 2012-09-21
forum: General Help
---

### Post by eticket on 2012-09-21
I thought the tilde (~) character referred to the Home directory. I entered the following command at the bash command line to create a small new file with the VI Editor:

vi ~/bin/sys_test

After entering a few characters, then saving and exiting VI, I then entered at the command line: ls

But, the newly created file (~/bin) and its contents (sys_test) were not displayed; only the normal /bin file appear with its standard contents could be seen, unless I specifically entered ls ~/bin.

Can anyone tell me where my ~/bin file is stored and why it doesn't show up when I use the ls command? Is the ~/bin file different than the /bin file then?

Thanks for the help.

eticket

---

### Post by Cheesemill on 2012-09-21
They are different directories.
~ is a short cut for /home/user (where user is your username).

Therefore ~/bin is actually /home/user/bin which is different to /bin

```
rob@arch:~$ cd ~/bin
rob@arch:~/bin$ pwd
/home/rob/bin
rob@arch:~/bin$ cd /bin
rob@arch:/bin$ pwd
/bin

```
```
rob@arch:~$ ls ~/bin
total 24K
-rwxr-xr-x 1 rob users 8.4K Sep 21 18:19 paconky
-rwxr-xr-x 1 rob users 8.4K Sep 21 18:18 paconky~
rob@arch:~$ ls /bin
total 3.0M
lrwxrwxrwx 1 root root    4 Apr  4 10:14 awk -> gawk
-rwxr-xr-x 1 root root 721K Jul 20 03:05 bash
-r-xr-xr-x 1 root root 7.0K Jul 20 03:05 bashbug
-rwxr-xr-x 1 root root  47K Jul 16 03:28 cat
-rwxr-xr-x 1 root root  59K Jul 16 03:28 chgrp
-rwxr-xr-x 1 root root  55K Jul 16 03:28 chmod
-rwxr-xr-x 1 root root  59K Jul 16 03:28 chown
-rwxr-xr-x 1 root root 120K Jul 16 03:28 cp
-rwxr-xr-x 1 root root  63K Jul 16 03:28 date
-rwxr-xr-x 1 root root  55K Jul 16 03:28 dd
-rwxr-xr-x 1 root root  91K Jul 16 03:28 df
-rwxr-xr-x 1 root root  23K Jul 13 03:26 dmesg
-rwxr-xr-x 1 root root   42 Aug 31 23:27 dnsdomainname
-rwxr-xr-x 1 root root  31K Jul 16 03:28 echo
-rwxr-xr-x 1 root root  27K Jul 16 03:28 false
-rwxr-xr-x 1 root root  40K Jul 13 03:26 findmnt
-rwsr-xr-x 1 root root  31K Aug  4 20:04 fusermount
lrwxrwxrwx 1 root root   13 Apr  4 10:14 gawk -> /usr/bin/gawk
-rwxr-xr-x 1 root root  11K Jun 30 16:53 groups
lrwxrwxrwx 1 root root   17 Aug 31 23:27 hostname -> /usr/bin/hostname
-rwxr-xr-x 1 root root  27K Jun 23 17:27 keyctl
-rwxr-xr-x 1 root root  23K Jul 11 18:42 kill
-rwxr-xr-x 1 root root  51K Jul 16 03:28 ln
-rwxr-xr-x 1 root root  31K Jul 13 03:26 login
-rwxr-xr-x 1 root root 108K Jul 16 03:28 ls
-rwxr-xr-x 1 root root  48K Jul 13 03:26 lsblk
-rwxr-xr-x 1 root root  51K Jul 16 03:28 mkdir
-rwxr-xr-x 1 root root  35K Jul 16 03:28 mknod
-rwxr-xr-x 1 root root  35K Jul 13 03:26 more
-rwsr-xr-x 1 root root  35K Jul 13 03:26 mount
-rwxr-xr-x 1 root root  11K Jul 13 03:26 mountpoint
-rwxr-xr-x 1 root root 112K Jul 16 03:28 mv
-rwxr-xr-x 1 root root 122K Aug  7 21:13 netstat
lrwxrwxrwx 1 root root   14 Aug 30 21:11 pidof -> /sbin/killall5
lrwxrwxrwx 1 root root   13 Jul 12 11:19 ping -> /usr/bin/ping
lrwxrwxrwx 1 root root   14 Jul 12 11:19 ping6 -> /usr/bin/ping6
-rwxr-xr-x 1 root root  91K Jul 11 18:42 ps
-rwxr-xr-x 1 root root  31K Jul 16 03:28 pwd
-rwxr-xr-x 1 root root  59K Jul 16 03:28 rm
-rwxr-xr-x 1 root root  43K Jul 16 03:28 rmdir
-rwxr-xr-x 1 root root  68K Nov  3  2011 sed
lrwxrwxrwx 1 root root    4 Jul 20 03:05 sh -> bash
-rwxr-xr-x 1 root root  67K Jul 16 03:28 stty
-r-sr-xr-x 1 root root  46K Jul 16 03:28 su
-rwxr-xr-x 1 root root  27K Jul 16 03:28 sync
lrwxrwxrwx 1 root root   26 Aug 30 21:52 systemd -> ../usr/lib/systemd/systemd
-rwxr-xr-x 1 root root 301K Nov  3  2011 tar
-rwxr-xr-x 1 root root  27K Jul 16 03:28 true
-rwxr-xr-x 1 root root  15K Aug  4 20:04 ulockmgr_server
-rwsr-xr-x 1 root root  19K Jul 13 03:26 umount
-rwxr-xr-x 1 root root  31K Jul 16 03:28 uname

```

---

### Post by jrog on 2012-09-21
> **eticket said:**
> I thought the tilde (~) character referred to the Home directory. I entered the following command at the bash command line to create a small new file with the VI Editor:

vi ~/bin/sys_test

After entering a few characters, then saving and exiting VI, I then entered at the command line: ls

But, the newly created file (~/bin) and its contents (sys_test) were not displayed; only the normal /bin file appear with its standard contents could be seen, unless I specifically entered ls ~/bin.

Can anyone tell me where my ~/bin file is stored and why it doesn't show up when I use the ls command? Is the ~/bin file different than the /bin file then?

Thanks for the help.

eticket
Some aspects of your question are confusing. What directory were you in when you entered the commands that you entered? Here's why I ask: "~/bin" is indeed different from "/bin"; "~/bin" is the "bin" directory in your home directory, whereas "/bin" is the "bin" directory under "/". So, when you typed "vi ~/bin/sys_test", you opened the file "sys_test" under the "bin" directory in your home folder. But you can do that from anywhere in the system, because the shell interprets "~" as the full path to your home directory. So, it is possible that you were in the "/" directory when you entered that command. That means that when you entered "ls", it showed you the contents of the directory you were actually in (which is exactly what it should do), "/". Those contents included "/bin", but not the ~/bin directory, because you weren't in your home directory when you typed it. If you wanted to see the contents of your home directory, you should have typed (without quotes) "ls ~".

That's my take assuming that I understand your question, anyway. (If you are not sure what directory you are in when you enter a command, you can check by typing "pwd". If you enter your home directory ("cd ~" without the quotes), you should see "bin" under that directory, assuming you created it.)

---

### Post by eticket on 2012-09-21
Thank you both for your quick replies.

After thinking about your answers, it sounds like the difference between my ~/bin and /bin subdirectories is that the former is a subdirectory in my Home directory (~), whereas the latter is a subdirectory in my root directory (/).

I guess the concept of directories is different than it is in a Windows environment.

eticket

---

### Post by jrog on 2012-09-21
> **eticket said:**
> Thank you both for your quick replies.

After thinking about your answers, it sounds like the difference between my ~/bin and /bin subdirectories is that the former is a subdirectory in my Home directory (~), whereas the latter is a subdirectory in my root directory (/).
That's right. :)

> **eticket said:**
>  I guess the concept of directories is different than it is in a Windows environment.
I don't know what you mean by this, though.

---

### Post by Vaphell on 2012-09-21
the directory tree is organized differently, true, but the concept is the same. Directories are simply collections of stuff and they form tree(s). Linux has a single tree starting branching from /, while windows uses multiple trees starting from each separate drive C:/D:/E:... for legacy reasons.
I'd argue linux is more logical because you can have drives mounted anywhere, following some overarching logic behind the organization of data, while windows still follows hardware because 30 years ago DOS had it this way.

Windows also supports aliases similar to linuxy ~ or $HOME. you can use %APPDATA% or %WINDIR% or %PROGRAMFILES% or whatever, even though there are no directories with that name, but you can type %APPDATA%\some_dir or %WINDIR%\some_dir and they will simply expand to their true form and will work just like ordinary C:\some_dir.
[http://technet.microsoft.com/en-us/library/dd560744%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/dd560744%28v=ws.10%29.aspx)

---

### Post by JKyleOKC on 2012-09-21
The concept is the same, since both were copied from the same older system. However, "~/bin" is not a file at all. You are correct in stating that it's a subdirectory in your home directory. Your original "vi" command should have created a file named sys_test in the /home/eticket/bin directory (assuming that my guess of your user name is correct). And it should not have been possible for you to write anything at all into the /bin directory unless you were working as the super user, via sudo...

However, if you did not already have a sub-directory named "bin" in your home directory, vi might have lied to you that it was creating the directory but failed to actually do so. That's what happened when I tried to duplicate the situation here. When I tried to write the test file out from vi, it told me I did not have write permission -- and a subsequent search for the new directory Vi said it was creating could not find it.

This may be a bug in vi; it ought to either (a) create the missing directory or (b) declare an error amd refuse to proceed.

---

