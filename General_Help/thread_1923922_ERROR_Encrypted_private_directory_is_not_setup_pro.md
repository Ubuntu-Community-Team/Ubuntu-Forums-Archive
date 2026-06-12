---
title: "ERROR: Encrypted private directory is not setup properly"
date: 2012-02-11
forum: General Help
---

### Post by joejoejoe77 on 2012-02-11
Welcome

I can not log in to the administrative account in ubuntu 11.10. I created a new account with super user priviliges named root. From this new account I don't have an access to the home/joe directory available on the administrative account.
1.The text shows the content of the directory joe available form the account called root.

Access-Your-Private-Data.desktop it's a Link to desktop configuration file (application/x-desktop)

and readme.txt

2.After opening the second doc. named readme.txt 

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

3.After typing a command in the terminal:

root@ubuntu:~/Desktop# ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

How to open the directory joe? 
Every suggestion, instruction welcome.

---

### Post by Paddy Landau on 2012-02-12
> **joejoejoe77 said:**
> I created a new account with super user priviliges named root.
Oops. That breaks the security model in Ubuntu. As there is already a user named root, I cannot even imagine how you managed to do that.

You should never, ever, have to sign in to a super user. When you need to run the occasional program as root (which is not often), you use either sudo (for the command line) or gksudo (for GUI programs).

> **joejoejoe77 said:**
> From this new account I don't have an access to the home/joe directory available on the administrative account.
If a user's home folder is encrypted, *only* that user can access his data. If he is signed on, then other users can access his data (subject to permission), but if that user is not signed on, *no one* can access his data.

It is possible to access joe's data from another user if, and only if, you have the decryption passphrases (there are two). The precise method is poorly documented and therefore not easy to follow.

I suggest you sign into Joe's account (that's your account, isn't it?) to access your data. As you have created a new account called root (how did you do that?), I don't know whether or not sudo and gksudo will work any more.

[s]What version of Ubuntu are you using?[/s] EDIT: You already told us.

---

