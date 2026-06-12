---
title: "What mean the indicators &quot;v&quot; and &quot;p&quot; in &quot;aptitude search&quot; results?"
date: 2010-09-29
forum: General Help
---

### Post by pstein on 2010-09-29
When I type in an aptitude search command like
 
aptitude search mailx
 
then the result list contains lines with a preceeding "v" and other with a "p".
 
Whats the difference?
 
Does "aptitiude search" use only local repository information or does it retrieve remote information?
 
Is it recommended/reuqired to do at first an
 
sudo apt-get update
 
?
 
Peter

---

### Post by oldos2er on 2010-09-29
From **man aptitude**:  Each search result is listed on a separate line. The first character of each line indicates the current state of the package: the most common states are p, meaning that no trace of the package exists on the system, c, meaning that the package was deleted but
its configuration files remain on the system, i, meaning that the    package is installed, and v, meaning that the package is virtual.     The second character indicates the stored action (if any; otherwise a blank space is displayed) to be performed on the package, with the most common actions being i, meaning that the package will be installed, d, meaning that the package will be deleted, and p, meaning that the package and its configuration files will be removed. If the third character is A, the package was automatically installed.

---

### Post by pstein on 2010-09-30
Ok, thank you.
But what means "virtual package"?
 
How can I install such a virtual package?
 
I git the following command sequence so far.
 
[EMAIL="user@ubuntu1004:/tmp$"]user@ubuntu1004:/tmp$[/EMAIL] aptitude search mailx
p   bsd-mailx                       - simple mail user agent                    
p   heirloom-mailx                  - feature-rich BSD mail(1)                  
v   mailx                           -                                           
[EMAIL="user@ubuntu1004:/tmp$"]user@ubuntu1004:/tmp$[/EMAIL] sudo apt-get install mailx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mailx is a virtual package provided by:
  mailutils 1:2.1+dfsg1-4ubuntu1
  heirloom-mailx 12.4-1.1
  bsd-mailx 8.1.2-0.20090911cvs-2ubuntu1
You should explicitly select one to install.
E: Package mailx has no installation candidate
[EMAIL="user@ubuntu1004:/tmp$"]user@ubuntu1004:/tmp$[/EMAIL] 

 
How do I "select one" as suggested by the command outpiut above?
 
Peter

---

### Post by pstein on 2011-02-10
...no answer?

---

### Post by timgood on 2011-02-10
It means that mailx (the program) is provided by the listed virtual packages which may also contain other programs. So you could install it by selecting the virtual package 'mailutils'(for example) and install it by

```
sudo apt-get install mailutils
```

Hope this helps.

---

