---
title: "create launcher that performs a sudo command first"
date: 2009-10-06
forum: General Help
---

### Post by jtprince on 2009-10-06
I want to create a launcher that will first perform a command requiring sudo privileges and then launches a program (without sudo privileges).  I've tried making a launcher with things like this as the command:

[INDENT]gksudo chown -R name:name /var/local/VirtualBox ; VirtualBox[/INDENT]

Or making a launcher with "run in a terminal":
[INDENT]sudo chown -R name:name /var/local/VirtualBox && VirtualBox[/INDENT]

Also, made a script virtual_box.sh in /usr/bin/ containing the commands separate:

[INDENT]sudo chown -R name:name /var/local/VirtualBox
VirtualBox &
[/INDENT]

This seems trivial, but I can't seem to make it work (either it performs the sudo command or I get a launch but not both)

Thanks very much for any help!

---

### Post by Vaphell on 2009-10-06
do these commands/scripts work when executed? do they cause problem only in launcher form?

---

### Post by undecim on 2009-10-06
I don't think you can use ; to separate commands in launchers. Use this instead:

```
sh -c "gksu chown -R name:name /var/local/VirtualBox ; VirtualBox"
```also, in the script, you should use gksu instead of sudo unless you are using a terminal to run it.

---

### Post by wdzieczny on 2009-10-06
You could try editing your sudoers file in Vi as well.

---

### Post by jtprince on 2009-10-08
Here is the solution that works:
```
sh -c "gksudo 'chown -R user:user /var/local/VirtualBox'; VirtualBox"
```

NOTE: it does not work without the single quotes around the chown command.  gksudo will "grab" the -R option in the chown command and think it owns it, so quoting the chown command is necessary.  

:):)  I really appreciate everyone's input on this as every post helped me to arrive at the final solution.  The folks who help on this forum are awesome :):)

---

