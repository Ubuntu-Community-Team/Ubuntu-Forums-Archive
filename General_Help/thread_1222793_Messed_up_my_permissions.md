---
title: "Messed up my permissions"
date: 2009-07-25
forum: General Help
---

### Post by robrom78 on 2009-07-25
I'm a noob to ubuntu, and I'm migrating from windows.  I can understand some things about how linux works, from what I use at my job, but I can't wrap my head around this one & I don't know where I went wrong.

Last night everything was fine with permissions, groups, etc, etc.  I was coding in eclipse, and reading some wiki's on coding at the same time.  When I power my maching on in the am, and go to users and groups, I'm rejeted hard core.  I've spent some time trying to find the correction, but i'm confused.  Do I use chown or chmod, and what is the correct syntax to put all the permissions to default?  

Thanks in advance for the help!

---

### Post by ptn107 on 2009-07-25
If you're just trying to fix your home folder and its contents you can do these in a terminal (just copy/paste):

To fix files:
```
find . -type f -exec chmod 644 {} \;
```

To fix folders:
```
find . -type d -exec chmod 755 {} \;
```

---

### Post by robrom78 on 2009-07-25
Thanks for the reply, but its still a no go.  I cannot access Users and Groups from my regular (non-root) account.

---

### Post by michy99 on 2009-07-25
Is it possible that you have removed yourself from the admin group somehow?

This command in the terminal will show what groups you are a member of:```
groups
```

---

### Post by sisco311 on 2009-07-25
> **michy99 said:**
> Is it possible that you have removed yourself from the admin group somehow?

This command in the terminal will show what groups you are a member of:```
groups
```

+1

OP, try this: [http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

