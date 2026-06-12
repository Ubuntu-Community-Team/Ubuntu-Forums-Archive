---
title: "3 user accounts 1 admin"
date: 2010-02-06
forum: General Help
---

### Post by adenewton on 2010-02-06
Hi, 

I'm installing a new laptop for a friend of mine and he wants 3 user accounts, similair to how he runs his windows setup.

1, an admin account, we have called this account peacemaker.

2. his account

3. an account for his girlfriend.

The problem we have is that if we want to do anything from the terminal that requires elevated priviledges, sudo does not accept his password or that of peacemakers.

we have done sudo -i -u peacemaker but it still doesn't accept either password, stating his account is not in the sudoers list.

I'm not a massive expert here, but research brought me to this page: [https://help.ubuntu.com/community/RootSudo#Allowing%20other%20users%20to%20run%20sudo](https://help.ubuntu.com/community/RootSudo#Allowing%20other%20users%20to%20run%20sudo)

But that then just means his account has admin rights, which is what we were trying to avoid. We wanted a setup similair to windows where if you want to run someting with elevated privledges if pops up asking for the admin password. This works in the gui, but not in the terminal.

So in short, my question is, is there anyway of having the terminal accept peacemakers user rights from the his normal user account?

If I add the account to the sudoers list like it suggests, does this again just give his account the prilvedges rather than saying supply me with the password for peacemaker.

I appreciate this is probably not really needed and he can just have his account as the main user, but coming from a windows background, he would prefer the 3 user accounts model (2 normal users, 1 admin)

Thanks

---

### Post by lloyd_b on 2010-02-06
At the command line, type "su peacemaker", and enter the admin account's password when prompted.  From this point, you should be able to "sudo" as required.  When you're done with the admin tasks, "exit" will take you back to the regular account.

("su" stands for "switch user")

Lloyd B.

---

### Post by ankspo71 on 2010-02-06
Hi,
I have only only one user account on my pc at the moment, and according to 'user settings' it has 'administer the system'  option enabled in my account automatically. My password is accepted everywhere

I just created a second user on this pc and named it 'test', and by default, the 'administer the system'  option was disabled. It said test was not in the sudoers file, so I had no choice but to enable 'administer the system' to perform a simple sudo command. (sudo apt-get update). Or switch user like the above poster mentioned. So Ubuntu (and most other Linux  distros), must assume that the first user will be the administrator.

Although... if he does choose to enable administrative privileges, then he might not have much need for the peacemaker account. 
Hope this helps.

---

### Post by DeMus on 2010-02-06
When you install Ubuntu, during installation it asks for a name. This is the full name of the person who does the installation. From that name a username is derived. Next you have to type 2 times your password to set it in the system
Now why is this all so important? The person doing the installation, the first user on the system, can have elevated privileges and act as root (administrator). To be able to do that this user has to type his/her password to proof it is really him/her. This is done in terminal (command line actions) and in GUI programs in need of root.

So, in your friends case you need 2 accounts:
[LIST]
[*]his account (with whatever username) as first account so he can become root when needed
[*]her account, which will only be a user account.
[/LIST]
There is no need to have a separate account for an administrator since the system has it already. This account is called root.

---

### Post by adenewton on 2010-02-06
> **lloyd_b said:**
> At the command line, type "su peacemaker", and enter the admin account's password when prompted.  From this point, you should be able to "sudo" as required.  When you're done with the admin tasks, "exit" will take you back to the regular account.

("su" stands for "switch user")

Lloyd B.

That's worked a treat.

Thanks

---

