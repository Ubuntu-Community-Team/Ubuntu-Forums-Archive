---
title: "Firefox gives &quot;The bookmarks and history system will not be functional"
date: 2011-01-25
forum: General Help
---

### Post by CNBarnes on 2011-01-25
OS: Ubuntu 10.4 
 
I performed a routine "apt-get update", which apparently upgraded   firefox to 3.6.14.   If I start FF from the root account, everything   works just fine.   However, if I start FF from any normal user account,   I get the error message:[INDENT]"The bookmarks and history system  will not be functional because one of  Firefox's files is in use by  another application. Some security [[COLOR=blue][COLOR=blue ! important][FONT=inherit ! important][COLOR=blue ! important][FONT=inherit ! important]software[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#")  can cause this problem" 
 [/INDENT]Running FF from root does not give the error (but then, who runs FF as root?).
 
 
 
 
I looked at link at [COLOR=Blue]_support.mozilla.com/en-US/kb/The%20bookmarks%20and%20history%20system%20will%20  not%20be%20functional_[/COLOR]
 
And renamed the places.sqlite to places.sqlite.old as instructed. 
 
 
Same error. 
 
So I quit FF and completely wiped out the .mozilla folder.  FF dutifully   created a new .mozilla folder, then promptly gave me the exact same   error message again.   This **STRONGLY** indicates that it is not a  permissions issue (besides, I looked at the permissions and everything  in the .mozilla folder is owned by the user with at least rwx------  permissions... 
 
 
Now I give up on this version of FF (3.6.14pre (Namoroka)) and apt-get  remove it, then issue apt-get install firefox-3.5.   It re-installed  apt-get install firefox-3.5...   [IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG]
(the /etc/apt/sources.list file is attached).
 
 
I posed this question on the mozilla news server, but those folks seem somewhat *nix clueless.

---

### Post by Smart Viking on 2011-01-25
Dude, why do you run firefox as root..

How did you uninstall it? If you used "apt-get remove", use "apt-get purge" instead to get ridd of configuration files as well, should fix it.

Do you have write permissions in /tmp?

---

### Post by asmoore82 on 2011-01-25
Ordinary files should never have rwx permissions, they need to be rw- or r--.

Try this cleanup and see if it helps
```
sudo chown -R $UID:$UID $HOME/.mozilla
sudo chmod -R 755 $HOME/.mozilla
find $HOME/.mozilla -type f -print0 | xargs -0 chmod -x
```

---

### Post by CNBarnes on 2011-01-25
> **Smart Viking said:**
> Dude, why do you run firefox as root..


Dude, I ran it as a test after it failed as a normal user.   It's not something I normally do. 




> 
How did you uninstall it? If you used "apt-get remove", use "apt-get purge" instead to get ridd of configuration files as well, should fix it.I didn't originally - but I just now tried it.   Ie

apt-get purge firefox   - results: removed
apt-get install firefox-3.5 - results: 3.6.14pre installed  (wtf??? :o )

tested:  same error.  ](*,)


I would REALLY love to install the old version of FF (3.5), not the beta (3.6.14pre).  I currently believe this is the root (pun) of all my problems.



> Do you have write permissions in /tmp?

Yes.

---

### Post by CNBarnes on 2011-01-25
> **asmoore82 said:**
> Ordinary files should never have rwx permissions, they need to be rw- or r--.

Try this cleanup and see if it helps
```
sudo chown -R $UID:$UID $HOME/.mozilla
sudo chmod -R 755 $HOME/.mozilla
find $HOME/.mozilla -type f -print0 | xargs -0 chmod -x
```


Did all that.  Nothing changed.


BUT.....   

as a test, I ran Firefox (as the normal user) from the command line.   I still got the same error message.   But this part might be helpful:

When I clicked on the "Bookmarks" menu option in FF, the command line window spit out:

```
lock:  No locks available
```


:idea:

---

### Post by CNBarnes on 2011-01-25
> **CNBarnes said:**
> Did all that.  Nothing changed.


BUT.....   

as a test, I ran Firefox (as the normal user) from the command line.   I still got the same error message.   But this part might be helpful:

When I clicked on the "Bookmarks" menu option in FF, the command line window spit out:

```
lock:  No locks available
```
:idea:



This last bit of information was what I needed in order to **[SIZE=5]SOLVE THE PROBLEM[/SIZE]**!  :P


Googling the lock issue resulting in virtually every hit talking about NFS.  Well... it turns out we are NFS mounting the users  /home  from another server.    Now recall that I said we ran upgrades.... 
 
Apparently now the new kernel of Ubuntu now wants to attempt to do file locking w/ NFS.
 
 
Modifying the /etc/fstab on the client workstations from :[INDENT][FONT=Courier New]server:/home/users    /home/users    nfs     rw,auto,nosuid,nodev 0  0[/FONT]
 [/INDENT]to [INDENT][FONT=Courier New]server:/home/users    /home/users    nfs     rw,[SIZE=5]**nolock**[/SIZE],auto,nosuid,nodev 0  0[/FONT]
 [/INDENT]SOLVED the problem.

---

