---
title: "Directory permissions override file permissions"
date: 2010-07-12
forum: General Help
---

### Post by el_basto on 2010-07-12
Hi. 
Is there a way to have a directory automatically change the permissions of a file that is written to it? 
I have a program which saves files to a directory, and gives those files read-only permissions to members in the group. This is a problem, because other users of my computer need to be able to edit these files. The directory itself has rw permissions for group members.
I guess what I am looking for is a way for the directory permissions to "override" the permissions the program is trying to save the files as. For example, if the directory has "rw" permissions for the group, then any file saved to it will automatically get the same permissions, regardless of what the program writing the file is trying to do.

I'm sorry I can't be more descriptive!

Thanks!

---

### Post by gzarkadas on 2010-07-12
Your quest is actually directory permissions versus *process* permissions, because it is the process that writes the file that decides for its permissions. 

In unix-like systems processes are assigned a umask when they execute, which is the current umask set for the user executing the process. This is set in the user's profile (~/.profile) or the system's global profile (/etc/profile) and can be changed by the `umask' command. But _it cannot be arranged to get overridden on a per directory basis_. Sorry, bad luck; but wait - there are good news also :).

Since the process you execute to write the file inside the directory is invoked typically through a command line, you can change the command line to first modify the umask to the desired value, ie one of:

[LIST]
[*]umask 007 : allows rw for user and group, disallows everything for others
[*]umask 002 : allows rw for user and group, allows r (read) for others
[/LIST]
and then execute the process to write the file. A _catch_ is that the process should not create other files in other places except the intended one; the later would also had the less restrictive premissions and this could be a security hole.

The safest way to do this is to invoke the chain of commands within a subshell. That way you do not have to remember to restore the umask to its default value or worry if the program terminates abnormally and the like. The umask call will only effect the subshell. To run someting in a subshell, simply enclose the command in parentheses, like this (substitute your command in place of `<your-command-line>'):

```

(umask 007 && <your-command-line>)

```

---

### Post by el_basto on 2010-08-17
Thanks for such a helpful and thorough answer; I always want to learn more about processes and become a better user of the terminal!

---

### Post by gzarkadas on 2010-08-18
[FONT=Fixedsys][SIZE=2]Nice to hear :) ; below is a small, incomplete list of links to get you going. It is a lot of staff, so take your time.

**The basics; know your shell, the core commands and your system.**[/SIZE][/FONT][FONT=Fixedsys][SIZE=2]
[/SIZE][/FONT]
[LIST]
[*][FONT=Fixedsys][SIZE=2][Bash Manual]("http://www.gnu.org/software/bash/manual/bash.html") (available also locally; type `info bash')[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][GNU CoreUtils Manual]("http://www.gnu.org/software/coreutils/manual/coreutils.html") (available also locally; type `info coreutils')[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][GNU FindUtils Manual]("http://www.gnu.org/software/findutils/manual/html_mono/find.html")[/SIZE][/FONT][FONT=Fixedsys][SIZE=2] (available also locally; type `info findutils')[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][Ubuntu System Administration]("https://help.ubuntu.com/community/SystemAdministration") (Ubuntu help)[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][Ubuntu Man Pages]("http://manpages.ubuntu.com/") (useful for commands you have not yet installed or for using the browser to read. Installed are available locally; type `man <command>')[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2]A subset of [/SIZE][/FONT][FONT=Fixedsys][SIZE=2]relevant guides and howtos from [The Linux Documentation Project]("http://www.tldp.org/") (tldp.org). Some things may be outdated but they are still useful:[/SIZE][/FONT]
[/LIST]
[INDENT]
[LIST]
[*][FONT=Fixedsys][SIZE=2][GNU/Linux Command-Line Tools Summary]("http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/GNU-Linux-Tools-Summary.html")[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][Introduction to Linux, A Hands on Guide]("http://tldp.org/LDP/intro-linux/html/intro-linux.html")[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][The Linux System Administrator's Guide]("http://tldp.org/LDP/sag/html/sag.html")[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][Linux Filesystem Hierarchy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html")[/SIZE][/FONT]
[/LIST]
[/INDENT][FONT=Fixedsys][SIZE=2]**One step ahead; learn more about advanced techniques, versatile tools and productivity tips.**[/SIZE][/FONT][FONT=Fixedsys][SIZE=2]
[/SIZE][/FONT]
[LIST]
[*][FONT=Fixedsys][SIZE=2][Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/abs-guide.html")[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][Sed - An Introduction and Tutorial]("http://www.grymoire.com/Unix/Sed.html")[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][The GNU Awk User's Guide]("http://www.gnu.org/manual/gawk/gawk.html")[/SIZE][/FONT]
[*][FONT=Fixedsys][SIZE=2][Working more productively with   bash]("http://www.caliban.org/bash/index.shtml")[/SIZE][/FONT]
[/LIST]

---

