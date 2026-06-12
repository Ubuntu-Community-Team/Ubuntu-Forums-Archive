---
title: "Trouble updating"
date: 2011-09-04
forum: General Help
---

### Post by cosners on 2011-09-04
Whenever I run sudo apt-get update it gives me this: 
```

Err http://apt.wxwidgets.org ubuntu-wx/main Sources                            
  404  Not Found
Err http://apt.wxwidgets.org ubuntu-wx/main i386 Packages                      
  404  Not Found

```
I looked into it and turns out it shouldn't be linking to ubuntu-wx, it should be natty-wx. How do I go about getting rid of the broken links and putting in the ones that should let it update? Sorry if this has been asked already, I did run a search but didn't find any instructions on how to replace broken links with working ones. Also if I am using wrong terminology, please correct me; I may be new but I'm willing to learn. Thanks!

---

### Post by TeoBigusGeekus on 2011-09-04
```
gksu gedit /etc/apt/sources.list
```
Change the necessary lines, save and exit.

---

### Post by Towlie on 2011-09-04
Someone should correct me if I'm wrong (I'm on my windows partition right now so I can't check but will switch in a minute) but there is a file in the /etc/apt/ folder called "Sources.list" that contains the sources that are checked every time you run "sudo apt-get update". If you (within the terminal) cd to the folder I mentioned eariler, then type in "ls -l" to check what files are there, and it is there, then you can type "sudo gedit sources.list" to edit it as root and either edit the two sources giving you an error or delete them entirely. 

Sorry I didn't display the commands as code, I'm new to this forum and I'm still figuring everything out in this forum post editor.

Edit: Didn't realize that TeoBigusGeekus posted a reply before me, so this information is redundant seeing as his code and advice are correct as well.

---

### Post by cosners on 2011-09-04
Awesome, it worked! Thanks. :)

---

### Post by TeoBigusGeekus on 2011-09-04
Brilliant; don't forget to mark the thread as solved.

---

