---
title: "How do I unlink dependencies via aptitude?"
date: 2012-08-03
forum: General Help
---

### Post by Saner on 2012-08-03
I have a problem.

I have a custom build of Ubuntu (yaVDR for anyone who is interested) and I want to upgrade some of the software on it.

However as it is all tied together if I try and remove XBMC via

apt-get remove xbmc

It wants to remove the whole vdr side of things and that I dont want.

Obviously xbmc is installed with the dependence on vdr when its not needed. 

> 
root@VL-MC:~# apt-get remove xbmc
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vdr-p < snip >  < / snip > libxine2
Use 'apt-get autoremove' to remove them.
[B]The following packages will be REMOVED
  xbmc yavdr-essential[/B]
0 upgraded, 0 newly installed, 2 to remove and 5 not upgraded.
After this operation, 39.5 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
  

How can I unlink xbmc and yavdr-essentials, so I can just remove xbmc and keep the rest. 


I am pretty sure it is possible because I did it before, but I cant for the life of me remember how I did it.

Cheers in advance.

S.

---

### Post by Paqman on 2012-08-03
I would be very wary of trying to over-rule the dependency system, dependencies are generally declared for a good reason (ie: stuff will break).

If XBMC is a core component of the yaVDR system, why are you trying to uninstall it? You mentioned you were trying to upgrade some software?

---

### Post by Saner on 2012-08-03
> **Paqman said:**
> 

If XBMC is a core component of the yaVDR system, why are you trying to uninstall it? You mentioned you were trying to upgrade some software?

I have no idea why they have linked the two, I am guessing because it is possible to run XBMC-Pvr as a front end for VDR.


Anyway its xbmc I want to upgrade, I have done it before and as long as you are not using xbmc as a frontend you can rip it out and it harms nothing.

but as I cannot remove it without destroying the whole vdr side of things because of this bloody dependency link I am stuck until someone can point me in the direction of unlinking it or I find the post I read before about doing it. 

I want to remove the link so I can purge xbmc and put my own custom build that is up to date as I use the system mainly as a media centre and less for vdr so I want to be able to update xbmc on my choosing (eg the build with the latest yavdr is already nigh on 4 months old and has the old audio engine) 

All I need to do is remove that link between yavdr-essential and xbmc and then I can do the rest with ease. 

urgh :rolleyes:

---

### Post by Saner on 2012-08-03
Found the old post.

Its a yaVDR specific command

> 
untie-packages is a script that ships with yaVDR and that you call on the command line. It installs all packages that are in the dependency list of yavdr-essential manually. Afterwards, it uninstalls the package yavdr-essential. The script offers you the opportunity to deinstall packages that are enforced to be installed witihn the yaVDR standard setup.

Cheers,
hepi


So I have it sorted. It would also explain why I knew I could bloody do it but was having a nightmare finding the command. 

:)

---

