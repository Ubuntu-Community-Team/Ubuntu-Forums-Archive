---
title: "I think I broke something in update manager"
date: 2012-04-02
forum: General Help
---

### Post by xeddog on 2012-04-02
I have been running Maverick (10.10) since somewhere around the Alpha2 release and have never had any significant problems until now.  In the last few days I have not been able to run the update manager.  When I try, I get a small dialog that says "Failed to lock the package manager".  When I look at the details it says "The package indexes are currently changed by apt-get."  

So in a terminal I get:

```
sudo apt-get update
[sudo] password for twoblues: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
twoblues@Stealth:~$ cd /var/lib/apt/lists
twoblues@Stealth:/var/lib/apt/lists$ ls -l l*
-rw-r----- 1 root root 0 2010-10-07 08:58 lock
twoblues@Stealth:/var/lib/apt/lists$ sudo cat ./lock
[sudo] password for twoblues: 
twoblues@Stealth:/var/lib/apt/lists$

```

When I list the files in /var/lib/apt/lists, everything looks ok to me except these three:  

```
Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Beta%20amd64%20(20120301)_dists_precise_main_binary-amd64_Packages
Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Beta%20amd64%20(20120301)_dists_precise_Release
Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Beta%20amd64%20(20120301)_dists_precise_restricted_binary-amd64_Packages
```

I know how they got there.  I am running Precise (12.04) as a guest machine in VirtualBox on my Maverick host.  A few days ago, I mounted a new beta cd for Precise, and Maverick mounted and started it.  It asked me if I wanted to install and I cancelled the dialog, but it must have done something anyway.  Or more likely I THOUGHT I cancelled it.

Anyway, How can I fix this?

Thanks,

Wayne

---

### Post by CynicRus on 2012-04-02
Try dpkg --configure -a

---

### Post by jerrrys on 2012-04-02
Have you checked your sources.list for Precise sources?

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

may yield something useful

---

### Post by xeddog on 2012-04-02
Well, I got the cahones to move the Precise files to the /tmp directory.  I then tried running update manager again and instead of 10 updates there was then only two.  Update manager applied those two, but when it went to refresh the repositories it wanted to mount the Precise beta cd again.  I ended update manager and used Synaptic to remove the precise entry, refreshed, and now all is right with the world again.

Thanks,

Wayne

OK, now to figure out how to mark this as solved . . . .

---

