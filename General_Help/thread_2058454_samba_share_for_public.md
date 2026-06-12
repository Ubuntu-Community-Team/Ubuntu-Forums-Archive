---
title: "samba share for public?"
date: 2012-09-15
forum: General Help
---

### Post by reach on 2012-09-15
Hi there!
I'm more a novice in Linux, but I managed to setup my 12.04 server with Apache, Samba, sshd, Twonky pretty well so far.

What I'm struggeling with is said the topic.
I'd like to have a samba share where ALL (typically Windows) users in the network have full access.
I have followed this tutorial: [http://micheljansen.org/blog/entry/182](http://micheljansen.org/blog/entry/182)    
but it just doesn't work. A PC with a windows user which doesn't exist on my server can read the folder, but not write it. 

I know this is not comprehensive information. If you'd kindly tell me which sort of additional info you might need, I'm happy to share it.

BTW: I'm wondering why this tutorial isn't referring to the needed folder owner and permissions. Mine is owned by my default user (which is apparently kinda root in Ubuntu) with permissions 775


Thx!
reach

---

### Post by Morbius1 on 2012-09-15
You created a share that looks like this:
> 
[public]         
comment = Public Shares         
browsable = yes         
path = /data/pub         
public = yes         
writable = no         
write list = dawuss         
guest ok = yesSo the only user that has write access is dawuss. 

Of course this HowTo like all the other bad samba howto's out there never mentions that Linux file permissions have to be in sync with samba authorizations so despite everyone saying how wonderful it is in the comments it simply won't work. Everyone including whoever dawuss is will only have read access unless dawuss is the owner of /data/pub.

If you want to have a pure public share where everyone can have write access then change your share definition to this. 
> 
[public]         
comment = Public Shares         
browsable = yes         
path = /data/pub         
public = yes         
writable = yes
guest ok = yesAnd then change the darn permissions:
```
sudo chmod 0777 /data/pub
```If you also want everyone to have the ability to edit all the files in that share and you don't care about who the original owner is then change it to this. All new files will be owned by the user nobody so every file will be editable by everyone else:
> [QUOTE]
[public]         
comment = Public Shares         
browsable = yes         
path = /data/pub         
public = yes         
writable = yes
[COLOR=Blue]**force user = nobody**[/COLOR]
guest ok = yes[/QUOTE]If this is not a Server with a big "S" but your own personal machine then change the force user to you:
> [QUOTE]
[public]         
comment = Public Shares         
browsable = yes         
path = /data/pub         
public = yes         
writable = yes
[COLOR=Blue]**force user = morbius**[/COLOR]
guest ok = yes[/QUOTE]And don't forget to restart samba:
```
sudo service smbd restart
```

---

