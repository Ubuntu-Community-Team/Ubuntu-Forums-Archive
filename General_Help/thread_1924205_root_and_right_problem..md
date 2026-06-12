---
title: "root and right problem."
date: 2012-02-12
forum: General Help
---

### Post by JohnPta on 2012-02-12
Somehow my system setup changed.
I was copying DVD's yesterday with Brasero Disk Burner.
Now I can not for one or other dark reason see my DVD any more or change the rights of the users. I still can see the DVD player under Guest.

Besides that when I try to log in via Terminal I get this message:
jan@jan-desktop:~$ sudo -i
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
jan@jan-desktop:~$ 

Regards

PS I did an upgrade today with "Update manager".

---

### Post by raja.genupula on 2012-02-12
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

by using that link add your user name to root group.

---

### Post by yetiman64 on 2012-02-12
You can't use sudo -i because the very file that controls who uses sudo is in the wrong ownership (yours).

Please post back the terminal output of ```
ls -l /etc/sudoers
``` please note your username may show here.

---

### Post by JohnPta on 2012-02-12
> **raja.genupula said:**
> [http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

by using that link add your user name to root group.

This is what I did and got: 
jan@jan-desktop:~$ useradd -G root jan
useradd: user 'jan' already exists
Than I created the user "solve"
That worked.
jan@jan-desktop:~$ id solve
uid=1004(solve) gid=1005(solve) groups=1005(solve),0(root)

However when I want to log into the "root_user solve" it asks me for a password.
Than I tried to change/give "solve" a password
 chpasswd solve
12345
chpasswd: line 1: missing new password
solve
chpasswd: line 2: missing new password
exit
chpasswd: line 3: missing new password
solve
chpasswd: line 4: missing new password

It looks like I am not clever enough to solve that problem.
Any more ideas?

---

### Post by JohnPta on 2012-02-12
> **yetiman64 said:**
> You can't use sudo -i because the very file that controls who uses sudo is in the wrong ownership (yours).

Please post back the terminal output of ```
ls -l /etc/sudoers
``` please note your username may show here.

jan@jan-desktop:~$ ls -l /etc/sudoers
-r--r----- 1 jan jan 574 2011-04-15 18:02 /etc/sudoers
jan@jan-desktop:~$

---

### Post by yetiman64 on 2012-02-12
> **JohnPta said:**
> jan@jan-desktop:~$ ls -l /etc/sudoers
-r--r----- 1 jan jan 574 2011-04-15 18:02 /etc/sudoers
jan@jan-desktop:~$
That should read " root root " not your username, this is why you can't use sudo.

If you reboot and at the grub screen (hold down shift during boot to get it to show if you have only one OS), select the recovery mode for your current kernel, select to drop to a root shell (don't need the networking) and use the command

```
chown root:root /etc/sudoers
```no need for sudo as you will be operating as root.

Type
```
exit
```to get back to the menu and you can boot on as normal to your desktop. Test "sudo -i" again.

---

### Post by JohnPta on 2012-02-12
> **yetiman64 said:**
> That should read " root root " not your username, this is why you can't use sudo.

If you reboot and at the grub screen (hold down shift during boot to get it to show if you have only one OS), select the recovery mode for your current kernel, select to drop to a root shell (don't need the networking) and use the command

```
chown root:root /etc/sudoers
```no need for sudo as you will be operating as root.

Type
```
exit
```to get back to the menu and you can boot on as normal to your desktop. Test "sudo -i" again.


This is what I got after typing "sudo-i"

jan@jan-desktop:~$ sudo -i
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
jan@jan-desktop:~$

---

### Post by yetiman64 on 2012-02-12
Please post back the command output again of "**ls -l /etc/sudoers**", if you issued the chown command from root recovery shell it should have changed the files ownership to root.

---

### Post by JohnPta on 2012-02-12
> **yetiman64 said:**
> Please post back the command output again of "**ls -l /etc/sudoers**", if you issued the chown command from root recovery shell it should have changed the files ownership to root.

It did not show the root user:
jan@jan-desktop:~$ ls -l /etc/sudoers
-r--r----- 1 jan jan 574 2011-04-15 18:02 /etc/sudoers
jan@jan-desktop:~$ 

So I tried your instructions again. Still NO success. 
However when I execute your command "ls -l /etc/sudoers" the response from the computer is "chown:changing ownership of '/etc/sudoers':readonly file system.

---

### Post by Elfy on 2012-02-12
You possibly need to use the mount drives option in the recovery menu before you run the chown command

---

### Post by JohnPta on 2012-02-12
> **forestpiskie said:**
> You possibly need to use the mount drives option in the recovery menu before you run the chown command

Ok I read your instruction but how do I do that?

PS This whole problem started because I am not able to mount my dvd player/drive.

---

### Post by cryptotheslow on 2012-02-12
Reboot and Select Recovery Mode from the GRUB menu:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/grubmenu1110.png[/IMG]

From the Recovery Menu select the remount option to mount the / filesystem read/write - press ENTER when prompted:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryremount2.png[/IMG]

You are then presented with a slightly different menu - select the bottom option to drop to a root shell:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryconsolerootprompt.png[/IMG]


Then proceed with the chown command as above.

---

