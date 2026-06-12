---
title: "Need help making a simnple script."
date: 2010-07-13
forum: General Help
---

### Post by h4ck3rk1ng on 2010-07-13
Hello, i need to make a simple sript that can be executed from the command line. It imple automates a tedious task i have to do.
it is made to modify windows files. This is how i  need it.
when it starts, i need it to ask me for a drive letter. If i put a valid drive letter in, it looks untill it finds a system 32 folder in that drive, and if it does, (it will if there is windows installed on it)
it looks for cmd.exe (command prompt) and replaces all the files named magnify.exe with it. it then renames itself to magnify.exe (the cmd file that was copied) does anyone know how i can achieve this? i need this to test a ethical hacking exploit i may have found on my system. Please help. it needs to be executed from the command line.

---

### Post by v1ad on 2010-07-13
are you asking how to do it from linux or from windows. 

if you are doing it from linux, there won't be a drive letter. it is a fairly easy script but it could vary on the device that u mount.

it would be some thing like /dev/sda1 instead of C:

if you are not great with linux i would recommend look up some tutorials on shell commands.

---

### Post by h4ck3rk1ng on 2010-07-13
> **v1ad said:**
> are you asking how to do it from linux or from windows. 

if you are doing it from linux, there won't be a drive letter. it is a fairly easy script but it could vary on the device that u mount.

it would be some thing like /dev/sda1 instead of C:

if you are not great with linux i would recommend look up some tutorials on shell commands.
ok i get it, so i need the same thingm only i need to specify the the drive as /dev/sda1 ect... (whatever its called mixing linux with windows does not work)
i can do it manually (using GUI not cli) but the gui actions translate to cli commands. i need it to be a script that does that.

---

### Post by Johnny B on 2010-07-13
[man page for the 'find' command]("http://unixhelp.ed.ac.uk/CGI/man-cgi?find")

---

### Post by h4ck3rk1ng on 2010-07-13
> **Johnny B said:**
> [man page for the 'find' command]("http://unixhelp.ed.ac.uk/CGI/man-cgi?find")
thx, now how do i put it all into a script to be run when i click/call it and how do i do the rest? like specify a drive and have it stored into memory and look through that drive ect...

---

### Post by Dn4mycrownj on 2010-07-13
no offence sounds like you are wanting a trojan done for you.

---

### Post by h4ck3rk1ng on 2010-07-13
> **Dn4mycrownj said:**
> no offence sounds like you are wanting a trojan done for you.
nah, its a backdor explit so i dont need a windows password after i reboot the syste, (assuming its in live cd) i assure you, this is for my computer science class, nothing illegal will be done with it.

---

### Post by h4ck3rk1ng on 2010-07-13
can anyone help? im having trouble...

---

### Post by cariboo on 2010-07-13
We don't support this type of activity in these forums, plus you would probably be better off asking your question on a Windows specific forum. Closed.

---

