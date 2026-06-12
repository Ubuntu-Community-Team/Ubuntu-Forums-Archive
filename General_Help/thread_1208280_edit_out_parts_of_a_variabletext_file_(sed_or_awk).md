---
title: "edit out parts of a variable/text file (sed or awk?)"
date: 2009-07-09
forum: General Help
---

### Post by senor_smile on 2009-07-09
I am learning how to write scripts, and am attempting to write a script to completely automate the process of install and ldap+samba server. I am using expect to automate the parts that require user intervention.  I have run into a snag, however.  I am running the slappasswd program, which expects the admin ldap password to be entered twice and then generates a code similar to:

> {SSHA}8SOL4+D5YBnST2TyMU0d+zsnvBOfI3D4

However, when I run the following:

```
echo "#!/usr/bin/expect -f
set timeout -1
spawn slappasswd
match_max 100000
expect \"*?password:*\"
send -- \"$ldappassword\r\"
expect \"*?Re-enter new password:*\"
send -- \"$ldappassword\r\"
expect eof">~/runslappasswd.exp

chmod +x ~/runslappasswd.exp
slappass=$( ~/runslappasswd.exp )
echo $slappass>>/slappass.txt
echo $slappass

```

the command line displays 
> {SSHA}8SOL4+D5YBnST2TyMU0d+zsnvBOfI3D4
as I would expect.  However, the txt file I created has:
> spawn slappasswd^M New password: ^M Re-enter new password: ^M {SSHA}8SOL4+D5YBnST2TyMU0d+zsnvBOfI3D4

How would I edit out everything before the {SSHA} part to use the $slappass variable where needed later in the script?

---

### Post by t4thfavor on 2009-07-10
$slapass =  `awk {print $10}` 

where $10 is the 10th field in that string array. I believe I counted correctly.

EDIT:
Not quite correct, I'm workin it out.


Heres what it looks like in perl
```

#!/usr/bin/perl -w

my $slapass = 'spawn slappasswd^M New password: ^M Re-enter new password: ^M {S$
print  "$slapass\n";
print `echo $slapass | awk '{print \$10}'`;


```

---

