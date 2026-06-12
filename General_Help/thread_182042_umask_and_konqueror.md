---
title: "umask and konqueror"
date: 2006-05-25
forum: General Help
---

### Post by jferrando on 2006-05-25
I want that all files that I create with konqueror have umask 0007, but not the files I create when "sudoing", or when
$ sudo -s
from a terminal.

I have tried pam_umask, I have added "umask 0007" in the files ~/.bashrc and ~/.bash_profile, and even added it to the file /usr/bin/startkde.

In this case umask works ok, but even to "sudo" access, so new programs when installed get umask 0007, and I do not wish it, the default administrative umask must be 0022.

What do you think? I think every day that ubuntu/linux is still not ready enough for the average user's desktop, needs a little more maturing.

---

### Post by uteck on 2006-05-25
This page, [http://www.cs.wcupa.edu/~rkline/Linux/environment-sudo.html](http://www.cs.wcupa.edu/~rkline/Linux/environment-sudo.html) may help you out. 
The problem that you are having is that sudo gets it's environment variables from the user, and does not use roots'.  I think if you enclose the commands in single quotes it will run the command using root's settings. 

Or do; "sudo bash" and run your commands as root using its' bash profile.

As to Linux not being ready for the average user, the average user can not find the Internet if their browser does not open to a site they know.  The concept of enter a URL is beyond them, let along running a security update, installing anti-virus and spy-ware protection, and doing any preventive maintanice on their computer.  Linux will become mainstream once games come out for it at the same time as windows.  Games are the only thing preventing it from taking the desktop.

---

### Post by jferrando on 2006-05-25
I have found the answer (I still can't beleive, this issue has never worked fine for me in both Debian sarge/etch and kubuntu).

Forget about the libpam-umask package, is not needed.

Edit the file [COLOR="Navy"]~/.bash_profile[/COLOR] and add
[FONT="Courier New"][COLOR="Navy"]umask 0007[/COLOR][/FONT]
When sudo-ing, the umask in /etc/profile file is kept (in my setup umask 0022).
[FONT="Courier New"]jferrando@alcudia:/etc$ umask
0007
jferrando@alcudia:/etc$ sudo -s
root@alcudia:/etc# umask
0022[/FONT]

---

