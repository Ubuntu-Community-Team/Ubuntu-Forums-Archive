---
title: "Home directory permissions problem"
date: 2010-06-09
forum: General Help
---

### Post by weixifan on 2010-06-09
I have come across a very strange permissions problem. I have two users on the system, say A and B. B is on the sudoers list and is an "admin" account. A isn't. I'm using Ubuntu 9.10.

What's happening is that for some reason, the permission on B's home directory (located at /home/B) reverts back to 500 every time B logs off, no matter what I chmod it to while logged in as B. Hopefully the following exercise will shed some light on the problem. (Am I missing something very obvious? :confused:)

To reproduce the problem:

I first log in (Gnome) as A, then I open a Terminal window. Note that B is currently not logged in anywhere in any form. The following is the output upon executing "ls -l" in /home inside the Terminal window:

```

total 24
drwx------  2 root root  16384 2010-03-14 22:47 lost+found
drwxr-xr-x 58 A    users  4096 2010-06-08 17:11 A
dr-x------  2 B    B      4096 2010-03-14 22:59 B

```

But now I open another Terminal window, and log in as B via "su B". Now I go back to the first window (in which A is logged in), and now I type the same "ls -l" command, and we see a different output:

```

total 32
drwx------  2 root root  16384 2010-03-14 22:47 lost+found
drwxr-xr-x 58 A    users  4096 2010-06-08 17:11 A
drwxr-xr-x 39 B    users 12288 2010-06-09 04:22 B

```

As you can see, the home directory permission (and group) on /home/B changes when I log in as B in another window. In fact, I will now change the permission of /home/B to 777 in the second window (in which B is logged in), and then immediately close that second window. Back in the first window (in which A is logged in), an "ls -l" shows output identical to the first code box shown above :confused:.

What's more, I now open two more Terminal windows and log in both as B via "su B". Back in the first window (in which A is logged in), "ls -l" shows

```

total 32
drwx------  2 root root  16384 2010-03-14 22:47 lost+found
drwxr-xr-x 58 A    users  4096 2010-06-08 17:11 A
drwxrwxrwx 39 B    users 12288 2010-06-09 04:22 B

```

So we see that the 777 permission is there. Now I close ONE of the two Terminal windows currently logged in as B. If I now perform "ls -l" in the first window (in which A is logged in), I get the same output (the third code box). But if I also close the remaining window with B logged in, I now see something different when I do "ls -l" in the first window (in which A is logged in): I see output identical to the first code box.

This demonstrates that B somehow "remembers" its permissions on /home/B, but reverts it back to what it was when it logs off. This is very strange.

---

### Post by dcstar on 2010-06-09
> **weixifan said:**
> I have come across a very strange permissions problem. I have two users on the system, say A and B. B is on the sudoer's list and is an "admin" account. A isn't. I'm using Ubuntu 9.10.

What's happening is that for some reason, the permission on B's home directory (located at /home/B) reverts back to 500 every time B logs off, no matter what I chmod it to while logged in as B. Hopefully the following exercise will shed some light on the problem. (Am I missing something very obvious? :confused:)
.........

Nothing at all happens to different /home folder permissions/credentials on my system when I follow those steps.

---

### Post by BoneKracker on 2010-06-09
I wonder if it's some kind of ACL thing (apparmor, selinux, etc.) preventing to non-admin user from having rights on an admin user's stuff?

---

### Post by weixifan on 2010-06-09
[quote="dcstar"]
Nothing at all happens to different /home folder permissions/credentials on my system when I follow those steps.
[/quote]

Yeah, sorry...I wasn't very clear. Those are steps to reproduce for me, and they won't work on any other Linux box I tried.

[quote="BoneKracker"]
I wonder if it's some kind of ACL thing (apparmor, selinux, etc.) preventing to non-admin user from having rights on an admin user's stuff?
[/quote]

I just tried getfacl in place of ls -l to view the permissions, and it appears that ACL is just as confused. ACL sees the same change of permissions upon log in/log out.

I also don't have SELinux installed. I haven't worked with AppArmor before, but I checked the AppArmor profiles in /etc/apparmor.d, and none of them seem to be relevant.

Thanks for your help though. Any other ideas?

---

