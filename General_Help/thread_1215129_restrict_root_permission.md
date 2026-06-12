---
title: "restrict root permission?"
date: 2009-07-16
forum: General Help
---

### Post by aspen_dv on 2009-07-16
Hi
Briefly on the issue: user needs to start an executable that interact with network device, thus need to be run as root. I can allow him to run only that in /etc/sudoers. But this opens a security hole because user can change content of these executables and that could harm the system. I absolutely don't want to give root access.

I was thinking of: once I verify that the executable working harmlessly, I can change permission to r+x only so it can't be modified. But if I give him sudo permission to run it, he could also modify it, am I correct. Or is there a way to restrict this situation? 
Please advice if you have any ideas addressing this issue.

---

### Post by DGortze380 on 2009-07-16
> **aspen_dv said:**
> Hi
Briefly on the issue: user needs to start an executable that interact with network device, thus need to be run as root. I can allow him to run only that in /etc/sudoers. But this opens a security hole because user can change content of these executables and that could harm the system. I absolutely don't want to give root access.

I was thinking of: once I verify that the executable working harmlessly, I can change permission to r+x only so it can't be modified. But if I give him sudo permission to run it, he could also modify it, am I correct. Or is there a way to restrict this situation? 
Please advice if you have any ideas addressing this issue.

Add users needing this script to a group (myGroup). Assuming the script is owned by root, add group myGroup to executable, set permissions to 750

---

### Post by CatKiller on 2009-07-16
> **aspen_dv said:**
>  I was thinking of: once I verify that the executable working harmlessly, I can change permission to r+x only so it can't be modified. But if I give him sudo permission to run it, he could also modify it, am I correct.

No, you aren't. If you put an entry in the sudoers file then that user can only run that file. To become root enough to change the permissions on the file he would need to be able to run *chmod* or *nautilus* or the like as root which, if he isn't a member of the admin group, he can't.

DGortze380's suggestion is much simpler, though. Just make that file executable by a group that the user is a member of.

---

### Post by c0mput3r_n3rD on 2009-07-16
> **DGortze380 said:**
> Add users needing this script to a group (myGroup). Assuming the script is owned by root, add group myGroup to executable, set permissions to 750

Like he said.  You have 3 different groups in Linux.  The User, Group, and Other.  Running ls -l will shows the permission so:
-rwxrwxrwx
The first is whether it's a directory or not.  The next 3 are the Users (your) permission for Reading, Writing, and eXecuting. The next are for the Group, and the last is for the Other.  If you want the Other person to be able to execute the files, and change the permissions of the file with the chmod command.  The chmod command, you need specify User, Group, or Other, then + or - what permission.  
Ex:
```

chmod o+x fileName

```
(you also have the way DGortze said but that using binary and is much more complicated, I think this way is easier.)

So, chmod o+x fileName will give any one who logs onto your system executable rights to that program.  Now with out running a Linux class I'll let you research the chmod command and file permission on your own to gain more knowledge, but I hope that helps (and it really should b/c I don't think it could be explained much better ;))

---

### Post by c0mput3r_n3rD on 2009-07-16
> **CatKiller said:**
> 
DGortze380's suggestion is much simpler, though. Just make that file executable by a group that the user is a member of.

You have the Other group though.  User, Group, and Other, which is designed exactly for issues like this.

---

### Post by DGortze380 on 2009-07-16
> **c0mput3r_n3rD said:**
> You have the Other group though.  User, Group, and Other, which is designed exactly for issues like this.

No, I'm sorry, but you're wrong.

It's OWNER GROUP and 'OTHER'

Owner is the owner of a given file. Not user (ie. you)

Group is all groups to which the file belongs

Other is actually 'everyone else'. If he is concerned about restricting access to this executable, then it would be a bad idea to all Anyone Else on the system to execute it. The defeats the purpose...

---

### Post by aspen_dv on 2009-07-16
Thank you all. Maybe I wasn't clear on the issue. So I understand the group and permission part. But the issue is that once the program runs, it has to run as root, because if running as a normal user, the rest of the script won't work (calling other subroutines). The program will keeps on running, listening to other service until you manually kill it.
Is this possible at all?

---

### Post by DGortze380 on 2009-07-16
> **aspen_dv said:**
> Thank you all. Maybe I wasn't clear on the issue. So I understand the group and permission part. But the issue is that once the program runs, it has to run as root, because if running as a normal user, the rest of the script won't work (calling other subroutines). The program will keeps on running, listening to other service until you manually kill it.
Is this possible at all?

Thats an issue with the program than. Adding access to JUST program via sudo for that user wouldn't fix your problem anyways then.

---

### Post by aspen_dv on 2009-07-16
ok...here's more..I don't really care if user can sudo and run the program, except he will not be able to modify it once I approve it to run on the server. If he needs to change something, then I will reconsider and approve it. The program is a binary executable. I don't know what's there. So that's why I am concerning about what if someone changes that binary to do bad things. Sound like a simple problem and I just over-complicate it???:-)

---

### Post by DGortze380 on 2009-07-16
> **aspen_dv said:**
> ok...here's more..I don't really care if user can sudo and run the program, except he will not be able to modify it once I approve it to run on the server. If he needs to change something, then I will reconsider and approve it. The program is a binary executable. I don't know what's there. So that's why I am concerning about what if someone changes that binary to do bad things. Sound like a simple problem and I just over-complicate it???:-)

I wouldn't be so worried about a binary executable, they'd have to decompile it and reverse engineer the code...

Of course if the user has root access, he could write and run his own malicious program, so you are correct to restrict access to that which is necessary.

... but I don't know that we've solved your problem. If it needs to run as root, then the program must be executed by root ... or the user that does execute it must also have permissions to any resources the program needs... to the best of my knowledge. Of course there must be a way to actually write the program to run as root. That would require access to the source code, not just the executable.

---

### Post by aspen_dv on 2009-07-16
> **DGortze380 said:**
> I wouldn't be so worried about a binary executable, they'd have to decompile it and reverse engineer the code...

Of course if the user has root access, he could write and run his own malicious program, so you are correct to restrict access to that which is necessary.

... but I don't know that we've solved your problem. If it needs to run as root, then the program must be executed by root ... or the user that does execute it must also have permissions to any resources the program needs... to the best of my knowledge. Of course there must be a way to actually write the program to run as root. That would require access to the source code, not just the executable.

Thank you! From what you saying, I can't just make the program non-writeable and allow him to access via sudo (to execute only). Anytime you allow sudo access to a file, they can change the permission to whatever....right?
You're right, the guy is the one wrote that program, that's why i'm afraid he would change something by mistake and screw up my server.
If a program run as root, then all commands inside it will be granted root access too though. Right?

---

### Post by c0mput3r_n3rD on 2009-07-16
I just re-read what you wrote and I misunderstood. Disregard what I said previously.

---

### Post by c0mput3r_n3rD on 2009-07-16
> **DGortze380 said:**
> No, I'm sorry, but you're wrong.

It's OWNER GROUP and 'OTHER'

Owner is the owner of a given file. Not user (ie. you)

Group is all groups to which the file belongs

Other is actually 'everyone else'. If he is concerned about restricting access to this executable, then it would be a bad idea to all Anyone Else on the system to execute it. The defeats the purpose...


Dude, I know, I was making it easy for him to understand, and I didn't give any false information.  Yeah the 'U' doesn't stand for User, but it's easy for him to understand if he thinks of it as himself.  And I didn't say Other is only the Other person he wants to give permissions to.

---

### Post by c0mput3r_n3rD on 2009-07-16
> **aspen_dv said:**
> Thank you! From what you saying, I can't just make the program non-writeable and allow him to access via sudo (to execute only). Anytime you allow sudo access to a file, they can change the permission to whatever....right?
You're right, the guy is the one wrote that program, that's why i'm afraid he would change something by mistake and screw up my server.
If a program run as root, then all commands inside it will be granted root access too though. Right?


Yes you are correct.  Root allows who ever that runs sudo, permission to do what ever they want.  That's why Linux saves you from yourself and makes you execute the sudo command before doing anything possibly damaging to your system.  Can you explain exactly what they have to do that makes them have to run as super user?  Maybe we can fix it by changing it.

---

### Post by DGortze380 on 2009-07-17
> **c0mput3r_n3rD said:**
> Yes you are correct.  Root allows who ever that runs sudo, permission to do what ever they want.  That's why Linux saves you from yourself and makes you execute the sudo command before doing anything possibly damaging to your system.  Can you explain exactly what they have to do that makes them have to run as super user?  Maybe we can fix it by changing it.

Again, I'm sorry but no. Sudo allows root access to whatever is specified in sudoers. That could be everything, or could be just one command.

I think the problem here is not giving the user access to execute, that's been covered multiple ways in this thread already.

The problem is that some commands executed by the program need root access. In this case, I believe the user that executes the program would also need access to these commands.

---

### Post by LightningCrash on 2009-07-17
> **DGortze380 said:**
> The problem is that some commands executed by the program need root access. In this case, I believe the user that executes the program would also need access to these commands.

Running the first runs all of the rest as root. You don't need specific entries in sudoers for each program that is going to be run by the sudo command. Otherwise init scripts would be a nightmare for sudoers.

Google for newsid.c if you're really worried about the process screwing up under your sudo command. newsid will fork a new session for the process you're running, and it's literally not yours after that point (unless you're root already).

---

### Post by DGortze380 on 2009-07-17
> **LightningCrash said:**
> Running the first runs all of the rest as root.

That's my point, he doesn't want to first to be able to run as 'root', just with necessary permissions for a few choice resources.

---

### Post by LightningCrash on 2009-07-17
> **DGortze380 said:**
> That's my point, he doesn't want to first to be able to run as 'root', just with necessary permissions for a few choice resources.

It would appear that he said it **has** to be run as root, he just didn't like sudo because he assumed it would allow them to just replace the executable with whatever they wanted.

OP: Set the sudoers entry for the specific script, chown to root, chmod 755
User won't be able to replace the script.

---

