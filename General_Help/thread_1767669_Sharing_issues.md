---
title: "Sharing issues"
date: 2011-05-26
forum: General Help
---

### Post by pillzburry on 2011-05-26
I have my ubuntu comp setup as a media server and works fine with mythtv etc but I also want to access the files from my computers in the other rooms (most have windows 7).  I was able to share the file containing the videos easy enough by right clicking the file and checking all of the sharing options the first time.  I have been able to access all the files that i originally put in the folder and stream video to my other computers without issue.  However any new files I add to the folders I am now unable to access.  The files show up but when I click on them it says I don't have permission.  I have tried unsharing the folder and redoing it but I come to the same issue.  I am sure I am just forgetting an easy step but I can't think of what that is.  Also want to make sure that any new files I add to this folder will work instantly across the network.

Any insight would be greatly appreciated.

---

### Post by dandnsmith on 2011-05-26
As a first step look at the files you can access, and those that you cannot in a listing which shows ownership and permissions (ls -lg in a terminal window).
Somewhere in that will, probably, be the cause of the problem.

Alternatively, it might be in the samba definitions for the share - but I don't rate that as very likely.

---

### Post by Morbius1 on 2011-05-26
> I was able to share the file containing the videos easy enough by right  clicking the file and checking all of the sharing options the first  time.You created a Samba Usershare that allows guest access. When the remote guest user adds a file to the share it will save with:

owner = nobody
group = nogroup

The easiest way to fix this since your share is guest accessible is to make the remote user look like you:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own local login username*[/COLOR]

Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Everytime you restart samba you have to wait a few minutes for the network to settle down so give it a minute or so and then add a new file from the remote machine. Evey new file will save with you as owner.

---

