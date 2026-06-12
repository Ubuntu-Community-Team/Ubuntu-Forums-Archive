---
title: "Hello.  Ubuntu newbie needing some help"
date: 2009-10-25
forum: General Help
---

### Post by G-Com on 2009-10-25
My first post. :)   

I burned the Ubuntu Live DVD and booted into it on my Dell Inspiron laptop.  Even running off the disc, It's definitely peppier than Vista.  I was concerned about not being able to connect via WLAN, but it worked like a charm.

My other issue is that I have a USB external hard drive formatted in the Macintosh (HFS) file system.  I bought an app that let me move files back and forth, and it sort of works in Ubuntu except I can't get in movie and pictures folders.  I think it says I don't have proper  permission.

Ubuntu might have just saved me a load of cash, because I was going to by Windows 7.  I like the look and feel of Ubuntu,  but I need access to my movies (nearly 450 GB of them!) and pictures.

Thanks for bearing with me and I look forward to your responses. :)

---

### Post by rockstarrem on 2009-10-25
I cannot assure you this will work, but try this:

```

sudo aptitude install hfsplus

```

If not, there are alternate ways to switch the filesystem I believe. I'm not sure you can install things with the live CD though.

---

### Post by P4man on 2009-10-25
May I ask which program you bought? HFS as far as I know, can be mounted in ubuntu by default. Have a look here:
[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

as for the problem with the permissions, try opening a file manager with root permission. press alf+f2 and then type

```
gksu nautilus
```

Then you can probably access those files and copy them, and after that, change the permissions and ownership so your own account owns them. you could do that on the nfs volume as well I suppose, but im guessing you dont want to mess with that so it keeps working on your apple ?

---

### Post by G-Com on 2009-10-25
> **P4man said:**
> May I ask which program you bought? HFS as far as I know, can be mounted in ubuntu by default. Have a look here:
[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

MacDrive.




> **P4man said:**
>  as for the problem with the permissions, try opening a file manager with root permission. press alf+f2 and then type

```
gksu nautilus
```Then you can probably access those files and copy them, and after that, change the permissions and ownership so your own account owns them. you could do that on the nfs volume as well I suppose, but im guessing you dont want to mess with that so it keeps working on your apple ?
Ah... Thank you. :)

---

### Post by G-Com on 2009-10-25
> **rockstarrem said:**
> I cannot assure you this will work, but try this:

```

sudo aptitude install hfsplus

```If not, there are alternate ways to switch the filesystem I believe. I'm not sure you can install things with the live CD though.
Other folders aren't marked with an "X." Only movies and pictures.

I might do an install after I get back from Mass.

Thanks for the responses. :)

---

### Post by rockstarrem on 2009-10-25
Ah cool, didn't know it was supported by default now.

---

### Post by P4man on 2009-10-25
> **rockstarrem said:**
> Ah cool, didn't know it was supported by default now.

Me neither :) Its read only by default according to the wiki. And it might not be included in the live environment. Either way, it should be fixable.

---

