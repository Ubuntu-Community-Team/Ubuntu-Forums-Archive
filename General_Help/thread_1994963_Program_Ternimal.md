---
title: "Program Ternimal"
date: 2012-06-03
forum: General Help
---

### Post by z3rO88 on 2012-06-03
Hi i am wondering if anybody could help me with linking the program to a terminal the command. Basically i am after the terminal to name what i want.

Program located: /usr/sbin/chkrootkit

What i want is the ternimal to state:  like user@user/pentest/chkrootkit

---

### Post by z3rO88 on 2012-06-03
Basically i need command that will automatically run it in sudo when click a program such as chkrootkit

---

### Post by steeldriver on 2012-06-03
EDIT: nevermind - didn't see your second post - thought you were asking about customizing the bash prompt

---

### Post by z3rO88 on 2012-06-03
> **steeldriver said:**
> EDIT: nevermind - didn't see your second post - thought you were asking about customizing the bash prompt

Thanks, well let say you have for example nmap it only works in terminal, so i create a menu icon for nmap which i want it to bring up the terminal with nmap without it asking for the sudo password (automatically over-rides the password)

If still not clear i will take print screens and show ya :)

---

### Post by mcduck on 2012-06-03
> **z3rO88 said:**
> Thanks, well let say you have for example nmap it only works in terminal, so i create a menu icon for nmap which i want it to bring up the terminal with nmap without it asking for the sudo password (automatically over-rides the password)

If still not clear i will take print screens and show ya :)

There is no such command. If you want to override the requirement for a password you need to add a line in your sudo configuration to tell that a certain user has the privilege to run that exact command with sudo but without requiring a password confirmation.

This guide should help: [https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

..of course be aware of what commands you allow, and the security issues that might cause. THe requirement of a password confirmation for admin tasks is always there for a reason.

---

### Post by z3rO88 on 2012-06-03
Thanks so they no way at all, i am creating a live dvd and need to get rid of the password so that any user can access the programs.

[IMG]http://img641.imageshack.us/img641/4997/20485292.png[/IMG]

I know made a mistype in name :)

---

### Post by mcduck on 2012-06-03
> **z3rO88 said:**
> Thanks so they no way at all, i am creating a live dvd and need to get rid of the password so that any user can access the programs.

I know made a mistype in name :)

If you are creating a live-DVD sure you will know the user account that is going to exist on the DVD and thus you can also configure it in the sudoers file.

---

