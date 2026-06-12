---
title: "No SUDO access when admin user created through Kubuntu User Manager"
date: 2010-01-06
forum: General Help
---

### Post by aseibert on 2010-01-06
Original HOWTO can be found at:
[http://awseibert.net/?p=10]("http://awseibert.net/?p=10")

So the other day I was in IRC and someone had brought up a problem where they created a new Administrative user, but didn&#8217;t have rights to use &#8217;sudo&#8217;.  Looked into the problem a little bit to figure out what was wrong, and it turns out that when you create a new user through the user manager (in kubuntu, anyways.  Haven&#8217;t tested in Gnome.) the user gets added to the adm group, however, a quick look at the sudoers file shows that it&#8217;s looking for users in the admin group to allow the use of sudo.  So, to solve the problem we do the following:

If you&#8217;re on the new admin user (which I&#8217;m assuming you are) use the following commands:

    ```
su [insert username of old account without brackets]

sudo usermod -G admin [username of new admin account without brackets]

exit
```

Then simply logout, and then log back in (not always necessary, but the easiest way to flush the permissions.)

    ```
su [insert username of old account without brackets]

```
Means we&#8217;re going to Switch User to the &#8220;old&#8221; admin account

    ```
sudo usermod -G admin [username of new admin account without brackets]
```

This simply adds the admin group to the secondary group list for the new user

    ```
exit
```

Pretty self explanatory

---

### Post by zvacet on 2010-01-07
>  problem where they created a new Administrative user, but didn&#8217;t have rights to use &#8217;sudo&#8217;.

You can do the same if you boot in recovery mode and add user first with command

```
adduser <username>
```

and then add that user to the admin group

```
adduser <username> admin
```

---

### Post by aseibert on 2010-01-07
Correct. Or, seeing as this was geared to ADDING an admin user, you can run those commands (assuming the user has NOT been created through the user manager) as the original user on the system.  No need for recovery, unless you deleted the old user account.

---

### Post by zvacet on 2010-01-08
> No need for recovery, unless you deleted the old user account.

Yes you have to use recovery because 

> they created a new Administrative user, but didn&#8217;t have rights to use &#8217;sudo&#8217;

---

### Post by aseibert on 2010-01-08
ONLY if they deleted the ORIGINAL admin user.  I'll prove the case here:

Created a new user via KDE'S User Management.

Open up a shell and login to the new user account

Just to prove that this is a BRAND NEW user account:

```
aaron@deimos:~$ su test
Password:
You are required to change your password immediately (root enforced)
Changing password for test.
(current) UNIX password:
Enter new UNIX password:
Retype new UNIX password:
You must choose a longer password
Enter new UNIX password:
Retype new UNIX password:
test@deimos:/home/aaron$
```

Ok. So I attempt to use SUDO, and this is what I get:
```

test@deimos:~$ sudo apt-get update
[sudo] password for test:
test is not in the sudoers file.  This incident will be reported.
test@deimos:~$
```

That is to be expected.  Now, since I STILL HAVE my ORIGINAL admin account on the computer, I can su to it:
```

test@deimos:~$ su aaron
Password:
aaron@deimos:/home/test$ cd
aaron@deimos:~$
```

and use sudo in my ORIGINAL admin account to add user 'test' to the admin group:

```
aaron@deimos:~$ sudo adduser test admin
[sudo] password for aaron:
Adding user `test' to group `admin' ...
Adding user test to group admin
Done.
aaron@deimos:~$
```

Switching back to the NEW admin account, we can then verify that SUDO does, in fact, now work:

```

aaron@deimos:~$ su test
Password:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

test@deimos:/home/aaron$ sudo touch /testfile
[sudo] password for test:
test@deimos:/home/aaron$ ls /test*
/testfile
test@deimos:/home/aaron$
```

Voila, new user account now has sudo access.

---

