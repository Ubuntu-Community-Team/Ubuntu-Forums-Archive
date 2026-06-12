---
title: "Very long loading icons on desktop after logging"
date: 2012-03-17
forum: General Help
---

### Post by annnowik on 2012-03-17
Hi,

every time I run Ubuntu (10.10), I need to wait about 2 minutes after it displays icons on desktop. It looks like: I type my user name and pass, click ok and I see my panels with all addons (like clock, date, shortcuts), I see my wallpaper but not icons. It's annoying. During waiting my harddisc is working hard till showing icons. It's not the matter of amout - I reduced all unimportant ones. And one thing else - when I want to shut the system down or restart it during loading (before icons are visible), I see the popup which says: File manager is not responding, and asks what to do (cancel or continue).

I will appreciate every reply.
Thanks
An

---

### Post by matt_symes on 2012-03-17
Hi

See if cleaning out your thumbnail cache helps. What version of Ubuntu are you using ?

Kind regards

---

### Post by annnowik on 2012-03-17
So.. I've just try it and it absolutely doesn't work (deleting .thumbnails folder).

And my version is, as I mentioned above, 10.10.

Anyway, thanks for advice.

---

### Post by matt_symes on 2012-03-17
Hi

Anything in the ~/.xsession-errors file just after you have opened Nautilus ?

Open a terminal and type

```
tail -f ~/.xsession-errors
```

then open Nautilus.

EDIT:

Also start up Nautilus and go to Edit->Preferences->Preview and disable every preview option (set to never). Restart Nautilus. Any speed change ?

Kind regards

---

### Post by annnowik on 2012-03-18
I typed tail -f ~/.xsession-errors, that's the result:

[HTML]** (nm-applet:1584): DEBUG: old state indicates that this was not a disconnect 1
** (nm-applet:1584): DEBUG: old state indicates that this was not a disconnect 1
** (nm-applet:1584): DEBUG: old state indicates that this was not a disconnect 2
** (nm-applet:1584): DEBUG: foo_client_state_changed_cb
** (nm-applet:1584): DEBUG: foo_client_state_changed_cb

(nautilus:1587): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1587): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
[/HTML]

Then I disabled displaying preview in places you pointed.

Still no changes.

---

### Post by annnowik on 2012-03-18
Oh, I forgot to say that I check autorun apps out - there are only few needed things there and no other stuff which would cause problem with icons.

---

### Post by matt_symes on 2012-03-18
Hi

> (nautilus:1587): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1587): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

This may or may not be problematic. I will look into this for you and see what i find.

In the meantime, do you have any Nautilus extensions or plugins installed (such as Dropbox, Ubutunu one) ? Try disabling them.

EDIT:

>  there are only few needed things there

What are they ?

Kind regards

---

### Post by annnowik on 2012-03-18
> I will look into this for you and see what i find.

Thanks a lot!

And...

No Dropbox. Ubuntu One removed - no changes.

In autorun - just basic parts of Ubuntu which were always there.
I remember time when my Ubuntu was ready to use after few second from logging.

---

### Post by matt_symes on 2012-03-18
Hi

> (nautilus:1587): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' fai

I don't think this is the cause of your problem.

Do you have any network shares you use via Nautilus ?

Kind regards

---

### Post by annnowik on 2012-03-18
I don't have any (if I understood properly what you mean).

My Ubuntu automatically make a connection to my wifi network.
I'm gonna show you my startup apps, but all these thing I use from the first day with Ubuntu and all was working right.

---

### Post by matt_symes on 2012-03-18
Hi

Your start up applications look fine as far as i can tell. I will double check later.

It's an odd one this one.

Create a new user and put some icons on that users desktop. Log in as that user from a cold start.

Does it take an age for that users icons to be displayed ? That will at least show if it's your settings or system settings.

Kind regards

---

### Post by annnowik on 2012-03-19
The new one user account is incredibly fast. No hard disc working, icons after 2 second ;) So I will try to change my settings. 

Thanks so much for your help! I guess I will handle with it, eventually I will move to the new account ;)

---

### Post by matt_symes on 2012-03-19
Hi

> **annnowik said:**
> The new one user account is incredibly fast. No hard disc working, icons after 2 second ;) So I will try to change my settings. 

Thanks so much for your help! I guess I will handle with it, eventually I will move to the new account ;)


If the worst comes to the worst you can do that.

Resetting all gnome Nautilus settings would be my next step.

Kind regards

---

