---
title: "Apache Images dont load"
date: 2006-02-19
forum: General Help
---

### Post by talos452 on 2006-02-19
SO i installed ubuntu...  strictly for a web server...  website loads.....   [http://mrgerry.biz](http://mrgerry.biz)    tell me what's missing..... IMAGES..supposedly i dont have permissions... yet it's all set for read write and execute.... any ideas?    I'm really frustrated with this:evil:

---

### Post by suRoot on 2006-02-19
First, make sure the images directory has the executable attribute set for all users/groups, as this is needed to enter the directory in the first place.  Permissions should look like this on the directory:

drwxr-xr-x

if not,

```
chmod 755 images
```

Also, make sure all the images are owned by the web server user.  I don't run apache on Ubuntu, but I'm assuming the user is "nobody" (if not, it's "apache").

```
chown nobody:nobody images/*
```

---

### Post by heimo on 2006-02-19
[quote=suRoot]Also, make sure all the images are owned by the web server user.  I don't run apache on Ubuntu, but I'm assuming the user is "nobody" (if not, it's "apache").[/quote]

Actually, I believe it's *www-data *in Ubuntu. :)

---

### Post by talos452 on 2006-02-19
so yeah, did that... still don't frackin work...   when you goto load an image it still says forbidden....    and the attributes are what you said they sould be for www and for image... did the commands you tried....   anything else i can try?:confused:

---

