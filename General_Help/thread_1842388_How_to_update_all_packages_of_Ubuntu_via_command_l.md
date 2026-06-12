---
title: "How to update all packages of Ubuntu via command line?"
date: 2011-09-11
forum: General Help
---

### Post by Shwick2 on 2011-09-11
I did some brief searches and could only find how to update the index list and upgrade the packages using apt and the command line.

I want to know how to update the packages so I stay on Ubuntu 10 but have updated software.

For example when I login through the command line I get the message: 

75 packages can be updated.
46 updates are security updates.

How to just normally update these packages, without necessarily upgrading?

---

### Post by howefield on 2011-09-11
I'm a little confused, you are asking how to update via the command line but saying you've found the answers ?

If you want to upgrade your packages via command line  do

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

---

### Post by SeijiSensei on 2011-09-11
> **howefield said:**
> I'm a little confused, you are asking how to update via the command line but saying you've found the answers ?

If you log in to a shell on some Ubuntu versions, the message-of-the-day includes the report the OP cites.  The MOTD has been changed quite a bit starting with 10.10, I believe, and doesn't have this information any longer.

---

### Post by oke on 2011-09-11
Another option to update and upgrade your packages via the command line is by using:
```
sudo aptitude update
```
and
```
sudo aptitude safe-upgrade
```
Some consider aptitude safer to use than apt-get. See [http://ubuntuforums.org/showthread.php?t=379804]("http://ubuntuforums.org/showthread.php?t=379804").

---

### Post by P05TMAN on 2011-09-11
Or you can use one command: 


sudo apt-get update && sudo apt-get upgrade

---

### Post by Frogs Hair on 2011-09-11
If you are concerned about upgrading Ubuntu to the next version open the update manger and enter settings . Under the updates tab in the section that displays release upgrades , select never . After doing this , when you update using the commands above you won't have to worry about accidentally Upgrading to the next Ubuntu version . Logout and back in as a precaution before using the commands .

---

### Post by Shwick2 on 2011-09-11
sudo apt-get update
Update the Package Index: The APT package index is essentially a database of available packages from the repositories defined in the /etc/apt/sources.list file. To update the local package index with the latest changes made in repositories, type the following:
[https://help.ubuntu.com/8.04/serverguide/C/apt-get.html](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)
also listed here, [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

From what I have read that command does not actually update the packages, it updates the package index.

Is there a command that updates the packages?

---

### Post by WorMzy on 2011-09-11
> Is there a command that updates the packages? 
The upgrade command.

```
sudo apt-get upgrade
```

---

### Post by Shwick2 on 2011-09-11
> **WorMzy said:**
> The upgrade command.

```
sudo apt-get upgrade
```

Ok, so when the motd told me there were 75 packages to update, I do that with the upgrade command? :???:

Ok understood.

I am worried that the apt-get upgrade command will, assuming the definition of the word upgrade, upgrade my system to Ubuntu 11 and beyond.

I want my system to remain at Ubuntu 10.04LTS.

Am I in danger of upgrading to the next version of Ubuntu if I use the upgrade command?

---

### Post by Frogs Hair on 2011-09-11
You are correct , it is the sudo apt-get upgrade command , that allows installation of new packages . If there are no packages to install or upgrade you will see a message in the terminal  indicating  that .  If there are packages to install you should get a message  indicating that , follow by a would you like to continue question .

---

### Post by WorMzy on 2011-09-11
To upgrade to a different release of Ubuntu, you would first need to update your sources.list file. Otherwise, Ubuntu will only install updates available in the current version's repository.

e.g. If you installed Maverick, you will only receive updates for Maverick until you change all instances of "maverick" in /etc/apt/sources.list to "natty" or "oneiric".

---

### Post by Shwick2 on 2011-09-11
> **WorMzy said:**
> To upgrade to a different release of Ubuntu, you would first need to update your sources.list file. Otherwise, Ubuntu will only install updates available in the current version's repository.

e.g. If you installed Maverick, you will only receive updates for Maverick until you change all instances of "maverick" in /etc/apt/sources.list to "natty" or "oneiric".

ah thanks for clearing that up :)

now to execute sudo apt-get upgrade

thanks for the he

---

