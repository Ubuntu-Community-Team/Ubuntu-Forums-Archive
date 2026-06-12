---
title: "How to undo chown -R   ?"
date: 2009-09-23
forum: General Help
---

### Post by robertson-lee on 2009-09-23
[http://ubuntuforums.org/showthread.php?t=496546](http://ubuntuforums.org/showthread.php?t=496546)

The above link is where I referred to. I couldn't post there for some privilege reason..

Anyway, I just want to undo / reverse back to how it used to be after doing this:

chown -R <user> <folder>

What should I type?

Please it is important..Thanks. 

:)

---

### Post by doas777 on 2009-09-23
well I don't think there is a good way to do that unless the files were all owned by the same entity. in that case, just use chown to put them back the way they were.

what did you chown?

---

### Post by robertson-lee on 2009-09-23
> **doas777 said:**
> well I don't think there is a good way to do that unless the files were all owned by the same entity. in that case, just use chown to put them back the way they were.

what did you chown?

How to use chown to put them back the way they are? that's my question.. :)

Now, it seems that the folder is loose. It used to be that; I have to chmod each time, which I prefer, if I want to change permissions. Now, I can just do on the windows panel, SFTP client..

Help to chown back to the way it was?

---

### Post by doas777 on 2009-09-23
well, you just use the opposite command.

if I had a dir ~/a that contained files owned by root:root
and ran this cmd:
```
sudo chown -R MyUser:users ~/a 
```then i could return it to how it was before with:
```

sudo chown -R root:root ~/a

```what was the exact command you ran?

the real question is do you know who owned the files previously, and was there only one user/group that owned them all?
if so then you can reverse it, as long as you know who had them previously. otherwise you may be screwed.

please answer, what did you chown?

---

### Post by 3L33T on 2009-09-23
> **robertson-lee said:**
> How to use chown to put them back the way they are? that's my question.. :)

Now, it seems that the folder is loose. It used to be that; I have to chmod each time, which I prefer, if I want to change permissions. Now, I can just do on the windows panel, SFTP client..

Help to chown back to the way it was?


Look for "umask" in /etc/profile.  By default, in Ubuntu umask for a file is "022" or "rw-r--r--".  I believe the default perms for a folder in Ubuntu is the "drwxr-xr-x".

---

### Post by philinux on 2009-09-23
> **robertson-lee said:**
> [http://ubuntuforums.org/showthread.php?t=496546](http://ubuntuforums.org/showthread.php?t=496546)

The above link is where I referred to. I couldn't post there for some privilege reason..

Anyway, I just want to undo / reverse back to how it used to be after doing this:

chown -R <user> <folder>

What should I type?

Please it is important..Thanks. 

:)

Use this command and look back at exactly what you did. 

```
gedit ~/.bash_history
```

---

### Post by robertson-lee on 2009-09-24
> **doas777 said:**
> well, you just use the opposite command.

if I had a dir ~/a that contained files owned by root:root
and ran this cmd:
```
sudo chown -R MyUser:users ~/a 
```then i could return it to how it was before with:
```

sudo chown -R root:root ~/a

```what was the exact command you ran?

the real question is do you know who owned the files previously, and was there only one user/group that owned them all?
if so then you can reverse it, as long as you know who had them previously. otherwise you may be screwed.

please answer, what did you chown?
Sorry, I am late, I was going to sleep that time of my post and busy with other things.
```

sudo chown -R root:root ~/a

```
The above did it. Solved. Thanks for your patience. You were asking what I chown? I thought I have already posted in my first post, it was: 
```

chown -R <username> <some_folder>


```
Anyway, it is solved. :)
3L33T, philinux,

Thanks for your posts as well, as it adds up to my ubuntu knowledge. Gonna use them when I need to, in the near future..

Thank you, guys.

---

