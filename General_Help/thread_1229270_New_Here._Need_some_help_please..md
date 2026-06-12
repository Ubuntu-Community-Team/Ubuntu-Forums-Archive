---
title: "New Here. Need some help please."
date: 2009-08-01
forum: General Help
---

### Post by Darth TNFAT on 2009-08-01
Hello.

I have been running Ubuntu for about a year now. I can usually work my way around problems, but this time I am stuck and need some more experienced help.

I ran an update tonight and after I rebooted both firefox and opera will not play any streaming videos. Youtube, facebook, etc...All that I get is a silver box with the play triangle in a circle.

I have attached a picture of a youtube page as an example of what I see.

I am wondering if there is a way to fix this or undo (roll back) the update?

Has anyone else seen this?

Could it be an Invidia issue, Flash?

Some help would really be apperciated.

Thanks.
Scott.

---

### Post by adamitj on 2009-08-01
You are probably using Macromedia Flash plugin, right?

If so, try out:

```
$ sudo aptitude reinstall flashplugin-nonfree
```

---

### Post by Darth TNFAT on 2009-08-01
Thanks for the quick reply.

I reinstalled the flash plugin as you suggested.
I am still a no go.

Thanks again.

---

### Post by yabbadabbadont on 2009-08-01
You could try uninstalling the one from the repositories and downloading and installing flash directly from Adobe.

---

### Post by cdwillis on 2009-08-01
My roommate had the same problem earlier. I went to synaptic, removed (completely) all the results that came up when searching 'flash', then reinstalled ubuntu-restricted-extras. Everything worked fine for him, but YMMV.

---

### Post by Darth TNFAT on 2009-08-01
> **cdwillis said:**
> My roommate had the same problem earlier. I went to synaptic, removed (completely) all the results that came up when searching 'flash', then reinstalled ubuntu-restricted-extras. Everything worked fine for him, but YMMV.

I tried it and it worked.

Thanks very much to all for the help.

It really is appreciated!

Have a great weekend everyone!

Cheers!

Scott.

---

