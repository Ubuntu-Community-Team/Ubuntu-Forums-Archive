---
title: "This error message. I can't open software centre either"
date: 2011-06-08
forum: General Help
---

### Post by Tee-Tee on 2011-06-08
I'm rather new to ubuntu. My computer crashed awhile and lost windows. so my friends downloaded ubunbu 10.10 for me. from the get go i had this little red "do not enter" like sign at the top. it says 

An unresolvable problem occured while initiallizing package information. then went on a bit. blash blah blah and had this error message.



'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

i tried the right click, like it suggested. didn't work. i don't know what wrong. i need it for school so i can download adobe so i cant watch videos on stuff to catch up.........PLEASE help!

---

### Post by wojox on 2011-06-08
Open your terminal Ctrl+Alt+T and run copy and paste these three commands:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update
```

---

### Post by Tee-Tee on 2011-06-08
> **wojox said:**
> Open your terminal Ctrl+Alt+T and run copy and paste these three commands:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update
```


I LOVE you!. it can open now!! :D thank u thank u thank u!!!!!!!!

---

### Post by wojox on 2011-06-09
Your welcome. :p

---

