---
title: "How to get back universe and multiverse to software sources"
date: 2012-01-15
forum: General Help
---

### Post by Aleksandar222 on 2012-01-15
I think I deleted my universe and multiverse repos so now I cannot install any software.
Also why does this happen when doing sudo apt-get update :

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

I have deleted the independent repo in software sources but this error showed again.
In the process I also accidentally removed universe and multiverse!
 
NOTE to devs : Add are you sure message box when deleting ppas and repos,please.

EDIT 1:

To clarify the USC part better.Whenever I enter an app description screen I got a button saying use this source and source name before it.
When I press use this source a message box pops up with this text :
W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I also looked at sources.list and everything is in there restriced,main,universe and multiverse.

Edit 2 :
 I used this : [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)
  and now when I try to install vlc it complains about package dependencies which do not resolve
but stellarium installs just fine

Edit 3 :
It seems that applications such as vlc or audacious depend on an older version of some lib(eg libc or libgtk2) and refuse to use the newer version of that lib installed on my PC.
The only cause I can think of such behaviur is when maverick to natty upgrade stopped at 1 minute and the os froze so I had to restart and later I did a partial upgrade.
Hopefully such apps will in future (ubuntu 12.04) use the new version of such libs I have installed.

Okay It seems to be normal now.The problem just went away magically with an upgrade from upgrade manager.Please smbody mark this as solved because I see no option to do so.

---

### Post by kc1di on 2012-01-15
Hi Aleksandar222,

Go To menu > system > synaptic 
Enter you passwd when asked.
click on settings in the toolbar the repositories
When the dialogue box appears make sure that (Universe) and (Multi-Universe have a check mark in their respective boxes. (Note: Universe should be the second one on the list and Multi the fourth.

should look like this [IMG]http://dl.dropbox.com/u/44046502/Screenshot%20-%2001152012%20-%2006%3A01%3A08%20AM.png[/IMG]

---

### Post by Aleksandar222 on 2012-01-15
> **kc1di said:**
> Hi Aleksandar222,

Go To menu > system > synaptic 
Enter you passwd when asked.
click on settings in the toolbar the repositories
When the dialogue box appears make sure that (Universe) and (Multi-Universe have a check mark in their respective boxes. (Note: Universe should be the second one on the list and Multi the fourth.

should look like this [IMG]http://dl.dropbox.com/u/44046502/Screenshot%20-%2001152012%20-%2006%3A01%3A08%20AM.png[/IMG]
Thank you.I have solved that that problem.All 4 repos are checked but now some apps like vlc complain about unresolved dependencies while others like Geany,Stellarium or Marble Arena 2 install without problem. :)

---

### Post by kc1di on 2012-01-15
make sure you refresh the repositories in synaptic.

---

### Post by bluexrider on 2012-01-15
> **Aleksandar222 said:**
> 

Okay It seems to be normal now.The problem just went away magically with an upgrade from upgrade manager.Please smbody mark this as solved because I see no option to do so.

Please use the Thread Tools in the upper right to mark this solved

---

