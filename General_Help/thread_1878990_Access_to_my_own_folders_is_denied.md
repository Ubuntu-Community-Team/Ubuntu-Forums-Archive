---
title: "Access to my own folders is denied"
date: 2011-11-10
forum: General Help
---

### Post by AJEllisuk on 2011-11-10
Hi 

After much searching with Google and the search facility for this forum, I've not been able to find a solution to this problem:

When I try to save a document to my own folder I get the following error message:

Error saving the document xxxx:

Access to /home/andrew/xxxx/xxxx is denied.

The folders did show a lock symbol on them so I used the following command to unlock them:

sudo chown -R username:username folder-name

However this does not appear to solve the problem. Could someone please give me some advice on how to fix this.

Thanks in advance

Andrew

---

### Post by Miljet on 2011-11-10
Open a terminal and type ```
ls -l /home/andrew/xxxx/xxxx 
```

You should get something that looks like this: ```
drwxr-xr-x 3 jack jack 4096 2011-11-04 22:19 Blake Shelton
drwxr-xr-x 3 jack jack 4096 2011-11-04 22:19 Conway Twitty
drwxr-xr-x 3 jack jack 4096 2011-11-04 22:19 Faron Young 
```

Each directory needs to belong to you and each must be executable. In other words, each entry should be drwxr-xr-x. If it is not, have a look here.
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by SeijiSensei on 2011-11-11
> **AJEllisuk said:**
> sudo chown -R username:username folder-name

Good try, Andrew.  How about:

```
sudo chown -R andrew:andrew /home/andrew
```

Does that fix the problem?

---

### Post by AJEllisuk on 2011-11-11
> **Miljet said:**
> Open a terminal and type ```
ls -l /home/andrew/xxxx/xxxx 
```

You should get something that looks like this: ```
drwxr-xr-x 3 jack jack 4096 2011-11-04 22:19 Blake Shelton
drwxr-xr-x 3 jack jack 4096 2011-11-04 22:19 Conway Twitty
drwxr-xr-x 3 jack jack 4096 2011-11-04 22:19 Faron Young 
```

Each directory needs to belong to you and each must be executable. In other words, each entry should be drwxr-xr-x. If it is not, have a look here.
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

Thanks Miljet

I was able to solve the problem by following the link you provided.

---

### Post by Miljet on 2011-11-11
Glad to be of help. Have a good day.

---

