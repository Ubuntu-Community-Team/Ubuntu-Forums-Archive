---
title: "Path for 'sudo' commands"
date: 2009-09-22
forum: General Help
---

### Post by BillRebey on 2009-09-22
I want to modify the root path, and I did so successfully by editing /etc/bash.rc.

However, this new root path only takes effect when I'm actually logged in as root.

When I "sudo" a program from a user account, though, neither the root path nor the user's path are searched.

How do I add to the path that "sudo" uses so that sudo can find the target program without having to specify it on the command line?

---

### Post by ChumleyEX on 2009-09-22
Just a stab in the dark here. 

```
nano /home/username/.bashrc
```

---

### Post by BillRebey on 2009-09-22
Doesn't seem to have any effect.  Anybody got the answer to this one?

I guess the real root of the question is "where does the path come from that 'sudo' uses to find commands/programs?"

---

### Post by Bachstelze on 2009-09-22
It *is* the $PATH of the user running sudo. You must be doing something wrong.

---

### Post by scragar on 2009-09-22
You might try writting yourself a wrapper till you find a better solution:
```
function sudo(){
  local tmp="$PATH";
  export PATH='/usr/sbin:/usr/bin:/sbin'##...
  /usr/bin/sudo $*
  export PATH="$tmp"
}
```

EDIT: fixed some obvious errors on my part.

---

### Post by arvevans on 2009-09-22
The default path for users is set with a boot-time program called your "profile".  There is a master copy located at "/etc/profile".  

There is also a personal copy which runs when you log into a UNIX or Linux computer.  This is located at "/home/*user_name*/.profile".  The dot preceding the file name means that it is a normally hidden file.  If using a file browser to view it you can show hidden files by entering CTRL-h

The 'profile' programs are bash shell scripts.  You can change the one located in your home directory.

In the 'profile' programs there is a line which sets your default **path** for various executables.  NOTE: you will also need permissions set for these target executables if you want to run them from your login ID.

As an alternative method, you can use the 'alias' command to name a personal link to specific executable programs, assuming you have set the 'permissions' to allow you to use them.

As yet another alternative, you can make a link to specific programs that will show an icon on your desktop, in your menu of applications, or as a quick-start in the top-bar on your screen.

Possible "problem" with Linux is that there are so many ways to do things that you could not do with MS-Windows OS.  This is good, but sometimes confusing to new Linux users.

---

### Post by BillRebey on 2009-09-22
Something's wrong, and I appreciate you folks helping me figure it out.

Backstelze, the 'sudo' PATH is definitely not the user's PATH.  To prove this, I wrote a script called "echopath" that simply echoes the PATH, and "~> echopath" shows the user's path, and "~> sudo bin/echopath" shows a very different, short path.

I've changed the user's .profile, /etc/bash.bashrc, and /etc/profile. None of these solutions work.  In fact, I've tried putting "echo" statements in them to see if they run when I run "sudo", and the echos don't print.

Furthermore, there are no PATH statements in the .profile, /etc/bash.bashrc, or /etc/profile files that set the path to what I'm seeing from "~>sudo bin/echopath".  The PATH that sudo runs with is: '/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin'

Nowhere in any of the files mentioned so far is this PATH set.

I'm using Ubuntu 9.04 in case that matters.

I'm at a loss and appreciate everyone's help.  Where on earth is the PATH set that "sudo" uses??!! Argh!

---

### Post by sisco311 on 2009-09-22
if you want to use the target user's PATH:
```
sudo -i command
```
if you want to set the PATH for sudo, edit the suders file and add:
```
Defaults       env_reset,**secure_path="/bin:/sbin:/usr/bin:/usr/sbin:/your/path:/end/so/on"**
```

NOTE: always edit the file with visudo:
```
sudo visudo
```
or
```
sudo env VISUAL=gedit visudo    #replace gedit with your favorite text editor
```

EDIT: to use the user's PATH:
```
sudo env PATH=$PATH command
```

---

### Post by BillRebey on 2009-09-25
Thanks for the pointers, but I can't set secure_path.  I'm using Ubuntu 9.04, and when I exit visudo, it complains: 

   "visudo: unknown defaults entry `secure_path' referenced near line 8"

If I try SECURE_PATH instead, I get:

   ">>>sudoers file: syntax error, line 7 <<<"

Any thoughts?  This is really frustrating...thanks for your help!

---

