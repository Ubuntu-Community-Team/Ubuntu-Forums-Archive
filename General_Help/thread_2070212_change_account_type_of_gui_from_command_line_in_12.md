---
title: "change account type of gui from command line in 12.04"
date: 2012-10-12
forum: General Help
---

### Post by demol1d0r on 2012-10-12
Hi, I have a dedicated remote server that I access using x2go but I can't change the status of a user from standard to administrator. Because the unlock icon is inactive.

[IMG]http://image.torrent-invites.com/images/986usac.png[/IMG]

Can I do it using the command line?

Obs: already edited the user groups. Didn't change from standard to admin only by doing that.
Obs2: I'm accessing it with the admin account.

thanks.

---

### Post by steeldriver on 2012-10-12
Generally the user needs to log out and back in for new group memberships to take effect

It sounds like you made the group changes already but if not then yes, you can do it from the command line, either via the usermod command (usermod -aG), or with

```
sudo gpasswd --add *username* *groupname*
```In this case you would likely need to add the user to the group 'sudo' (earlier versions used group 'admin')

---

### Post by demol1d0r on 2012-10-12
> **steeldriver said:**
> Generally the user needs to log out and back in for new group memberships to take effect

It sounds like you made the group changes already but if not then yes, you can do it from the command line, either via the usermod command (usermod -aG), or with

```
sudo gpasswd --add *username* *groupname*
```In this case you would likely need to add the user to the group 'sudo' (earlier versions used group 'admin')

Hello tnks for your reply. I did this procedure already. My user is member of sudo and admin group. But didn't become administrator on gui.
I did a research and seems that this problem is related with the policykit. I'm trying to fix it right now, don't know if I'll have any lucky tho.

edit: alright I finally broke my policykit package now I don't know what to do.. when I try reinstall it says it is already newest version.

update:

Did a reinstall of policykit-1 but now "User Accounts" is not even opening anymore =DDDDDD

---

