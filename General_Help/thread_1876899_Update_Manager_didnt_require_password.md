---
title: "Update Manager didnt require password"
date: 2011-11-07
forum: General Help
---

### Post by whatthefunk on 2011-11-07
I just updated my computer (Lubuntu 11.10) with Update Manager but did the whole thing without having to enter in my password.  It normally asks for my password when I click the Update button.  This is more than a little worrying...  I have made absolutely no system changes lately.  A couple questions:
1. What logs should I look at to see what is going on?
2. How can I correct this situation?
3. How did this happen in the first place?

---

### Post by bluexrider on 2011-11-07
sure you didn't update from a Root Terminal

---

### Post by Rodney9 on 2011-11-07
Update Manager has never asked me for my password in Lubuntu.

Rodney

---

### Post by Elfy on 2011-11-07
That is how it works now apparently.

There was a change so that password was not needed to update packages that were already installed.

Tried to find the report I saw, will try again later.

---

### Post by whatthefunk on 2011-11-07
> **forestpiskie said:**
> That is how it works now apparently.

There was a change so that password was not needed to update packages that were already installed.

Tried to find the report I saw, will try again later.

Just googled and this now appears to be a feature to make it more user friendly.  Wouldnt this be a security risk?  Since Update Manger now has a free pass to do what it wants without requiring a password, what would prevent a somebody from using it to "update" an installed program to include malicious software?  I really dont like how there now exists a program on my computer that has root access without requiring a root password....  Any way to have it require the password?

---

### Post by Elfy on 2011-11-07
Not that I know of.

I've seen a few threads along the same lines here - maybe see if there's an answer in one of those. 

I didn't take much notice I'm afraid.

Edit - looks like bugs reported against this will be marked won't fix - [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/814331](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/814331)

---

### Post by raja.genupula on 2011-11-07
> **forestpiskie said:**
> Not that I know of.

I've seen a few threads along the same lines here - maybe see if there's an answer in one of those. 

I didn't take much notice I'm afraid.

Edit - looks like bugs reported against this will be marked won't fix - [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/814331](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/814331)
yeah this is the sencond time i am watching similar post like this . Once again i am suggesting that please go with terminal for updates and upgrades 

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by whatthefunk on 2011-11-07
But using the terminal when you update doesnt change the fact that a program with a free pass exists on your computer.  There must be a way to force it to ask for the password...  Would it be possible to place the entire update program in sudo thus requiring a password to start the program?

---

### Post by Elfy on 2011-11-07
Digging I found this 

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)
> 
For environments where this change is deemed not appropriate, this functionality can be disabled by the administrator via PolicyKit or by creating users that are not in the admin group (a recommended practice to begin with). 


[https://lists.ubuntu.com/archives/oneiric-changes/2011-June/003881.html](https://lists.ubuntu.com/archives/oneiric-changes/2011-June/003881.html)

---

