---
title: "share file permission problem"
date: 2011-05-18
forum: General Help
---

### Post by rainbow99984 on 2011-05-18
Hi, I'm using ubuntu 11.04, I'm having some problem of ownership while sharing folder/files. to share i change the folder share option:1. Share this folder, then followed by 2.allow others to create and delete files in this folder3. guest access.
Now if someone in my local network edit any file and save it, it gets locked. if some one copy their file in this folder the permission is marked as "no group" "no owner". and they get unaccessible to me. i tried doing chown <user> <folder> but it says Operation not permitted.
 Now how i can possibly share my folder on local network so that they can be edited by others without getting locked down , if they copy files i can able to modify them.
Thanks.

---

### Post by Morbius1 on 2011-05-18
When a remote anonymous guest adds or edits a file on your share it will save as owner = nobody / group = no group. That is by design. There is a far more complicated way to solve this issue but since you created a guest share the simple way out is to force the remote user to look like you:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line in the [global] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to you own local login user name*[/COLOR].

[COLOR=Black]Then restart samba:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]
Wait a few minutes ( not kidding ) for the network to settle down after a samba restart and try it again. When the remote user saves a file it will save as owner = you.

Can't explain this problem:
[/COLOR]> [COLOR=Black]i tried doing chown <user> <folder> but it says Operation not permitted.[/COLOR]You do have to do that as root you know:
```
sudo chown morbius /path/to/shared/file
```

---

### Post by rainbow99984 on 2011-05-19
Thank you Morbius1, to clear things up :):KS, one other type of sharing is also having the same problem i have created a user have given login with password, no other permissions say "test" now i shared a file without guest allow and in  folder permission -> other section i have given read/write permission ,now this user can login and make changes in this folder/files but getting the same problem after edit the owner/group changes to "test".
any way so that only "test" login can do changes in particular folder shared but ownership remains to me.
Thanks for the answers, yes chown i tried with sudo and is working.

---

