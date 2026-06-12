---
title: "Directory permissions problem"
date: 2010-09-29
forum: General Help
---

### Post by nachtbarjunge on 2010-09-29
Hi,

I wanted to give NFS a try. So I established a connection to my server via ssh. I created some directories:
```
/exports/usr/myUser
/exports/public

```

I wanted the myUser directory to be only usable by myUser. I set its permissions like this;
```
drwx------
```

Now I can't even enter the directory. If I grant the read permission to "others", I can enter the directory. 

Why is this? 
What can I do to make the directory only usable by myUser?

I use the same username on my client machine and the server. When I login I am only asked for the password. How does linux map the users of the to systems? Are they considered to be the same? Does this has anything to do with the problem?

Thanks in advance.

---

### Post by 5PUTN|K on 2010-09-29
well this is not realy a solution but if all you want to do is access ur folders u can try using this command in a terminal window

sudo nautilus /home/USRNAME/Desktop/blah/blah/blah

that will grant nautilus (that is ur default folder browsing application) sudo privilages so u can access and edit that folder

---

### Post by nachtbarjunge on 2010-09-29
Thanks for your answer. To clarify: I am able to change the permissions of the diretory in any situation with sudo or sudo -i. So even if I set the permissions that way, that I can't access the directory anymore, I can use sudo to grant the execute permission for "others". After that I can access the directory again.

The question is:
If I am logged in as "myUser" and the owner of the directory is "myUser", too, and only the owner has permissions to access the directory, why can't I access the directoy?

Maybe this is more an owner related issue than an permissions related issue. When I am logged in at my client system with "myUser". Now I connect to the server via SSH. The server somehow recognizes my username. I must only input my password and not the username at this point. So I am logged in as "myUser". The owner of the directory is "myUser", too. Why can't I access the directoy? Or is "myUser" != "myUser" in this case of SSH login?

Any suggestions? Thanks in advance again.

---

### Post by nachtbarjunge on 2010-09-29
Forget it. The directory was exactly names as "myUser". I mixed up the name of the directory with its owner, So owner was root and a sime chown fixed the problem. 

:-\"

---

