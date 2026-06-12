---
title: "Can't log onto Ubuntu"
date: 2009-12-18
forum: General Help
---

### Post by ainsaur on 2009-12-18
I ran into some trouble tonight when I was experimenting with "chown" and I messed something up.  I now can't log onto Ubuntu.  I get the following error message when I enter my password:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."

When I click "ok", I get another error message which states:
"Could not update ICEauthority file /home/alex/.ICEauthority".

I then click on "close" and I get "There is a problem with the configuration server. (usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)".

When I click on "close", I get "Nautilus could not create the following required folders: /home/alex/Desktop, /home/alex/.nautilus. Before running Nautilus, please create these folder, or set permissions such that Nautilus can create them". 

Then I get "There was an error starting up the screensaver: Failed o change o directory '/home/alex (Permission denied) Screensaver functionality will not work in this session."  After clicking "ok", I get a brown screen. I don't know what to do next.  I would really appreciate if someone could please steer me in the right direction (with specific instructions) as I am a noob when it comes to linux.

Thank you.

---

### Post by unmole on 2009-12-18
Try this
Select the Recovery Mode option from the Boot Menu. Then select 'drop to root prompt' and type
```

 chown -R alex:alex /home/alex
```

---

### Post by ainsaur on 2009-12-18
> **unmole said:**
> Try this
Select the Recovery Mode option from the Boot Menu. Then select 'drop to root prompt' and type
```

 chown -R alex:alex /home/alex
```
I tried it and received the same first error message: "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

When I clicked on it, I got to my desktop.  So far, so good.  Now, how do I change the permissions so that I'm at "644"?  Also, I tried logging into one of the other users on my computer and got the same series of error messages as in my original post.  Would I open a terminal from my desktop and use a command like "chown -R kyle /home/kyle"?  

Thanks again.

---

### Post by smo0th on 2009-12-18
Did you tried booting with live cd?

[LIST]
[*]Open a live cd terminal
[*]Type sudo su
[*]Change permissions
[*]Reboot
[/LIST]

Did it worked?

---

### Post by ainsaur on 2009-12-18
Do you mean to use this command:  chown -R alex:alex /home/alex
with the live CD?

I haven't tried the live CD yet. I want to confirm that I am using the correct command before I try it, however.  This is how I got myself in trouble in the first place.

---

### Post by c9-3Rr0r on 2009-12-18
```

chmod 664 /home/alex

```

---

### Post by ainsaur on 2009-12-18
I've made a small amount of progress.  I've had some other problems that I've had to solve.  The major one, other than the permissions issue, is that Ubuntu 9.10 (and 9.04) doesn't like my nvidia geoforce 7200GS videocard.  I get vertical lines when I try to run the liveCD. I was able to get to the liveCD desktop using safe graphics mode. I opened the terminal and typed in the previous two commands 'chown' and 'chmod' but I get "invalid user: alex:alex" and "chmod: cannot access '/home/alex: No such file or directory'.  So, how do I access the hard drive of my computer if I am in the live cd?  Any advice would be most welcome.

Thanks.

---

