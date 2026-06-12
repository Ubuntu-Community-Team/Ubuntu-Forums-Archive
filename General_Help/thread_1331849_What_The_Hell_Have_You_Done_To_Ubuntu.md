---
title: "What The Hell Have You Done To Ubuntu?"
date: 2009-11-19
forum: General Help
---

### Post by Mark76 on 2009-11-19
I don't know when it happened,but since it did I've been unable to make any changes to my ROX Session or to even use the logout command.

Apparently I now have to edit my sudoers file for it to work properly :mad:

---

### Post by bodhi.zazen on 2009-11-19
Have you been running gui apps as root ?

Check the permissions of your files in $HOME

```
ls -lA
```

Look for any files owned by root.

---

### Post by Giblet5 on 2009-11-19
It's discussed [here]("http://paycreate.com/perry/wharrgarbl.jpg") in some detail.

Edit: **bodhi.zazen** has mad patience skillz. I better add something constructive out of an abstract sense of guilt and shame.

To set reasonable permissions on your home directory with 'one command':

```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

That'll take awhile to run and you might get two warnings about ~/.gvfs. When it's done, your home directory will truly be your own.

---

### Post by Mark76 on 2009-11-19
> **bodhi.zazen said:**
> Have you been running gui apps as root ?



Not to my knowledge

> **Giblet5 said:**
> It's discussed [here]("http://paycreate.com/perry/wharrgarbl.jpg") in some detail.

Edit: **bodhi.zazen** has mad patience skillz. I better add something constructive out of an abstract sense of guilt and shame.

To set reasonable permissions on your home directory with 'one command':

```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

That'll take awhile to run and you might get two warnings about ~/.gvfs. When it's done, your home directory will truly be your own.

Running it now

---

### Post by Mark76 on 2009-11-19
And now ROX-Session doesn't work at all

I think I'll going back to Jaunty and wait to see if Lucid is better

---

### Post by Cheesemill on 2009-11-19
Me ???

I haven't done anything ;) !!!

---

### Post by bodhi.zazen on 2009-11-20
> **Mark76 said:**
> And now ROX-Session doesn't work at all

I think I'll going back to Jaunty and wait to see if Lucid is better

How are you running ROX-session ? are you running ROX with FLUXBOX or stand alone ?

Can you run ROX-session manually (form the console and not GDM)  and see what error messages you are getting ?

Any error messages in your logs ?

---

