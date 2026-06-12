---
title: "Problems updating!!!!!!!"
date: 2010-01-11
forum: General Help
---

### Post by kwboom on 2010-01-11
Hi there I am having problems updating I am getting errors and it will not update....


this is copied from the error......

[B][I]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E: Problem parsing dependency Recommends, E:Error occurred while processing webcamstudio (NewVersion1), E: Problem with MergeList /var/lib/apt/lists/apt.dolphinaura.studenthotspot.net_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/I][/B]

I must have a problem with Webcamstudio so I tried to uninstall it by using sudo apt-get remove webcamstudio, but it came with about the same error.... Please help I have no clue what is going on......

---

### Post by warfacegod on 2010-01-11
Try:

```
sudo apt-get purge webcamstudio
```

---

### Post by kwboom on 2010-01-11
I just tried that and this is the error I get.....

[B][I]mike@DAD:~$ sudo apt-get purge webcamstudio
[sudo] password for mike: 
Reading package lists... Error!
E: Problem parsing dependency Recommends
E: Error occurred while processing webcamstudio (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/apt.dolphinaura.studenthotspot.net_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
mike@DAD:~$[/I][/B]

---

### Post by slakkie on 2010-01-11
Could you run sudo apt-get update and try again? Or remove the conflicting file and run apt-get update and then try again?

Perhaps share the logs:
/var/log/dist-upgrades/

/var/log/apt/history.log
/var/log/apt/term.log

---

### Post by kwboom on 2010-01-11
Well after I did that I ran

```
sudo atp-get update
```

and it updated just fine.......    


Just for future reference what was or could have been the problem???? Just for my own sanity :D

---

### Post by kwboom on 2010-01-11
By the way .......


***_[SIZE="6"]THANK YOU FOR THE HELP [/SIZE]_***

---

### Post by slakkie on 2010-01-11
> **kwboom said:**
> Well after I did that I ran

```
sudo atp-get update
```

and it updated just fine.......    


Just for future reference what was or could have been the problem???? Just for my own sanity :D

See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=468751](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=468751)

> 
If the package lists can't be read in "aptitude update", download
       new ones instead of crashing.  (Closes: #468751)


---

