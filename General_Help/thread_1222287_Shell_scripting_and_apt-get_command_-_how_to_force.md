---
title: "Shell scripting and apt-get command - how to force &quot;Yes&quot; ( when installing pckgs ) ?"
date: 2009-07-24
forum: General Help
---

### Post by credobyte on 2009-07-24
Does anybody know how to force "Yes" command when installing something via apt-get ( example below ) ? What I should add/change in my shell script so it wouldn't ask me to confirm new package installation ?

installer.sh
```
echo "Installing RecordMyDesktop"
sudo apt-get install gtk-recordmydesktop
```

output ..
```
dainis@credobyte:~/Desktop$ ./installer.sh
Installing RecordMyDesktop ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bind9utils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  recordmydesktop
The following NEW packages will be installed:
  gtk-recordmydesktop recordmydesktop
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 135kB of archives.
After this operation, 733kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by kk0sse54 on 2009-07-24
Might want to check out the 'yes' command perhaps. You can pipe it's output by typing "yes | sudo apt-get install <package>" or "yes | ./installer.sh"

Edit: I don't use Ubuntu but just checked the man page for apt-get and there's an argument for forcing yes "-y". So instead you could just run the command ```
sudo apt-get -y install <package>
```

---

### Post by wojox on 2009-07-24
Try:

```
apt-get --force-yes install gtk-recordmydesktop
```

---

### Post by ftabor on 2009-07-24
> **credobyte said:**
> Does anybody know how to force "Yes" command when installing something via apt-get ( example below ) ? What I should add/change in my shell script so it wouldn't ask me to confirm new package installation ?

installer.sh
```
echo "Installing RecordMyDesktop"
sudo apt-get install gtk-recordmydesktop
```

output ..
```
dainis@credobyte:~/Desktop$ ./installer.sh
Installing RecordMyDesktop ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bind9utils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  recordmydesktop
The following NEW packages will be installed:
  gtk-recordmydesktop recordmydesktop
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 135kB of archives.
After this operation, 733kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

```
echo "Installing RecordMyDesktop"
sudo apt-get install -y gtk-recordmydesktop
```

---

### Post by dharvell on 2009-07-24
If you check out the man page for apt-get, you will see that there is an option for forcing a "yes".

> -y, --yes, --assume-yes
Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively.  If an undesirable situation, such as changing a held package, trying to install a unauthenticated package or removing an essential package occurs then apt-get will abort.  Configuration Item: APT::Get::Assume-Yes.

EDIT:  Looks like other people beat me to it...

---

### Post by credobyte on 2009-07-24
Thanks to everyone - while trying to find a solution, it was already posted here :) Thnx, --yes parameter does it's job pretty well !

---

