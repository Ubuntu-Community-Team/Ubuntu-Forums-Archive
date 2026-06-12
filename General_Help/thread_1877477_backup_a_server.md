---
title: "backup a server"
date: 2011-11-08
forum: General Help
---

### Post by sajansen on 2011-11-08
hey
can someone help me with making a backup on my server? i have tried several things like dd, tar, partimage and stuff but the problem is that dd copyes the empty space as well and tar gives an error and for partimage i need to unmount the drive but then i cant run it over ssh... 

does anyone know a tool i can use over ssh without unmounting and that does not copy the empty space? and i hve to run it from commandline.

thanks in advance.

sander

---

### Post by Lars Noodén on 2011-11-08
You can use [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html).  rsync only copies the changes, so after the first time, it is very fast.

```

$ rsync -avz -e ssh sajansen@remotehost:/path/to/remote/dir /path/to/local/dir/ 

```

PS.  If you think of it as the shell or as shell scripting, then it makes a lot more sense than "command line"  :)

---

### Post by sajansen on 2011-11-08
> **Lars Noodén said:**
> You can use [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html).  rsync only copies the changes, so after the first time, it is very fast.

```

$ rsync -avz -e ssh sajansen@remotehost:/path/to/remote/dir /path/to/local/dir/ 

```

PS.  If you think of it as the shell or as shell scripting, then it makes a lot more sense than "command line"  :)

thnaks haha yea... windows user :P but ill try it!

---

### Post by sajansen on 2011-11-08
it works so far...but is it wise to use this way when making a full system backup? (inc. ubuntu itself)? well as long as it works its fine with me...

---

### Post by Lars Noodén on 2011-11-08
rsync is fine for full system backups, but you might want to add the -H option to get any hard links.

---

