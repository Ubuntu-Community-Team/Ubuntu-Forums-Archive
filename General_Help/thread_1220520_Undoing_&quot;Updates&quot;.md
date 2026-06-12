---
title: "Undoing &quot;Updates&quot;"
date: 2009-07-22
forum: General Help
---

### Post by Darryll83 on 2009-07-22
Undoing "Updates"
Simple question. Is there a way to roll back "updates" that I installed?

I am currently running Kubuntu 9.04. Yesterday, I installed the recommended updates that the update notifier told me about and now I am having nothing but problems.

My Collection of music in Amarok became completely scrambled. I plays songs fine, however it seems to be getting the song title, artist, album and album cover information completely wrong for EVERY song.

My second harddrive stopped booting, eventhough fdisk lists it as booting. I have gone through the process listed here twice [http://www.smorgasbord.net/how-to-in...-ubuntu-linux/](http://www.smorgasbord.net/how-to-in...-ubuntu-linux/) and I have tried other fixes listed in forums with no luck. It still doesn't boot.

My FTP server, through ProFTPD, flat out refuses to work.

I have had this problem before, but somehow in the last couple months I have completely forgotten that "updates" screws my computer up. Last time, I just completely wiped my computer and completely reinstalled. I could do that again, but I'd really prefer it to be a last resort.

Anybody have any ideas?

---

### Post by michy99 on 2009-07-22
Possibly you are running out of space on your partition. What does this command show?```
df -h
```

---

### Post by Zorael on 2009-07-23
As for the Amarok database, I had this once, and I had to manually delete the database and have it recreate a new one (indexing tags anew).


Bad advice inc (involves terminal-fu).

Downgrading *is* possible, if the old version is still available either in your apt cache, or in the repositories. For instance, if 9.04 comes with KoolApp v2.0, and then later an update hits with KoolApp v2.1, then v2.0 will still be available in the main repository, as v2.1 was probably just added to one of the *updates* repositories.

However, let's say v2.2 hits and ends up being buggy. v2.0 might still be available, but chances are v2.2 has taken v2.1's server space on the updates repo.

Of course, there are several levels of updates. I think the terminology goes "important security updates", "recommended updates", "pre-released updates" and "unsupported updates". And they all have their own repo.

Consider installing Synaptic or Adept Manager and downgrade the packages in there. If you're handy with a terminal, you can specify version numbers to aptitude to make it install a specific one. Note version numbers:
```
zorael@lethe:~$ **apt-cache policy [COLOR="RoyalBlue"]amarok[/COLOR]**
amarok:                                
  Installed: **[COLOR="Red"]2:2.1.1mysql5.1.30-jaunty~ppa1[/COLOR]**
  Candidate: [COLOR="Red"]**2:2.1.1mysql5.1.30-jaunty~ppa1**[/COLOR]
  Version table:                           
 *** **[COLOR="Red"]2:2.1.1mysql5.1.30-jaunty~ppa1[/COLOR]** 0      
        500 http://philip.magicalforest.se jaunty/extra Packages
        100 /var/lib/dpkg/status                                
     2:2.1.1mysql5.1.30-0ubuntu1~jaunty1 0                      
        500 http://se.archive.ubuntu.com jaunty-backports/main Packages
     2:2.1mysql5.1.30-0ubuntu2~jaunty2 0                               
        500 http://ppa.launchpad.net jaunty/main Packages              
     **[COLOR="Lime"]2:2.0.2mysql5.1.30-0ubuntu3[/COLOR]** 0                                     
        500 http://se.archive.ubuntu.com jaunty/main Packages          

zorael@lethe:~$ **sudo aptitude install [COLOR="RoyalBlue"]amarok[/COLOR]=[COLOR="Lime"]2:2.0.2mysql5.1.30-0ubuntu3**[/COLOR]
Reading package lists... Done                                          
Building dependency tree                                               
Reading state information... Done                                      
Reading extended state information                                     
Initializing package states... Done                                    
The following packages will be *DOWNGRADED*:
  **[COLOR="RoyalBlue"]amarok[/COLOR]**                     
0 packages upgraded, 0 newly installed, 2 downgraded, 13 to remove and 17 not upgraded.
Need to get 11.2MB of archives. After unpacking 8520kB will be freed.
Do you want to continue? [Y/n/?] **Y**
<...>
```
The only annoying part is that it will keep wanting to upgrade that package afterwards. You can *hold* the package at the current version with aptitude, though the graphical update managers don't honor that. So that's basically only an option if you only use aptitude to update.
```
$ sudo aptitude **hold** amarok
```
Likewise, if you just want to blacklist that one version and not opt out of ever getting Amarok updates (until you **unhold** the package), you can use *forbid-version*.
```
$ sudo aptitude **forbid-version** amarok=**[COLOR="Red"]2:2.1.1mysql5.1.30-jaunty~ppa1[/COLOR]**
```

All of this is possible in Synaptic too, I wager.

---

