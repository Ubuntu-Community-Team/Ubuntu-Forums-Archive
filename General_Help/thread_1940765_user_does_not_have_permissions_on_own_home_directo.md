---
title: "user does not have permissions on own home directory?"
date: 2012-03-14
forum: General Help
---

### Post by hoylemd on 2012-03-14
Hello forums,

I've been using ubuntu desktop for a few years, so I figured i'd be ok installing it on my linode.  Unfortunately, I don't actually know what I'm doing.  I added a user (my non-root account) via command line, but that user doesn't appear to have write access to it's home directory.  Whenever I run irssi, i get 

```
** ERROR **: Couldn't create /home/username/.irssi directory
abroting...
Aborted
```

Does anyone know what I did wrong and/or what I need to do to fix it?  I don't really know what I'm doing so please try to keep things simple.

---

### Post by jerome1232 on 2012-03-14
What command did you use to create the user? It's possible you didn't even create it's home directory.

Use the command adduser as opposed to useradd, ie

```
sudo adduser joeshmuck
```


If the home directory exists what are your permissions set to?
```
ls -ldh ~/
```

mine were set to
```
drwxr-xr-x
```

---

### Post by hoylemd on 2012-03-14
there is a directory, and the permissions look similar. this is the output:

```
drwxr-xr-x 3 root root 4.0K 2012-03-06 20:23 /home/username
```

The "root root" makes me think those are root's permissions and not usernames though.

edit:

Would it just be easiest to remove the user and re-make it with adduser?  If so, how would I do that if I'd used useradd? (I think I used useradd)

---

### Post by jerome1232 on 2012-03-14
> **hoylemd said:**
> 
Would it just be easiest to remove the user and re-make it with adduser?  If so, how would I do that if I'd used useradd? (I think I used useradd)

Maybe, adduser is an easier way to addusers but a simple chown might do the trick (from a sudo user)
```
sudo chown -R username:username /home/username
```

To remove a user use (if that's the route you want to go)

```
sudo deluser --remove-home username
```

---

### Post by hoylemd on 2012-03-14
Success! thanks!

---

### Post by dcstar on 2012-03-15
> **hoylemd said:**
> Hello forums,

I've been using ubuntu desktop for a few years, so I figured i'd be ok installing it on my linode.  Unfortunately, I don't actually know what I'm doing.  I added a user (my non-root account) via command line
.........

And what is wrong with using the simple GUI tools provided to do this job?

---

