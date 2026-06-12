---
title: "FYI - Symbolic links not working in Samba from Windows and Mac?"
date: 2010-04-06
forum: General Help
---

### Post by kooldino on 2010-04-06
If you have some directories shared that contain symbolic links that are NOT being resolved by the client machine, try adding these lines to your /etc/samba/smb.conf file:

```

[global]
 follow symlinks = yes
 wide symlinks = yes
 unix extensions  = no

```

---

### Post by capscrew on 2010-04-06
> **kooldino said:**
> If you have some directories shared that contain symbolic links that are NOT being resolved by the client machine, try adding these lines to your /etc/samba/smb.conf file:

```

[global]
 follow symlinks = yes
 wide symlinks = yes
 unix extensions  = no

```

In an effort for full disclosure...

Samba has changed the defaults for symlinks for security reasons.  See [**_[COLOR="Blue"]here [/COLOR]_**]("http://www.samba.org/samba/news/symlink_attack.html")for Samba's own explanation of the situation.

---

### Post by kooldino on 2010-04-06
So is this why it's always worked fine for me and all of a sudden it just stopped working?

---

### Post by capscrew on 2010-04-06
> **kooldino said:**
> So is this why it's always worked fine for me and all of a sudden it just stopped working?

Yes,  the last update (about a week ago) changed the default settings for the smbd.  You are just changing the update back to the previous settings.

My point was also to let you and other readers know that things just don't happen.  The revision was for an important reason and you should know and understand consequences of your actions.  You should never just change ( or tell others to change) your configuration until you understand what you are doing.

I did not have symlinks in shares, so the update did not affect me.  I did see this in advance, so I watched for the update.  It was explained in the update notice.

---

### Post by kooldino on 2010-04-06
I understand why it was done after you posted the links, but at the end of the day, the first post still points out the fix.

Thanks for the background info.

---

### Post by capscrew on 2010-04-06
> **kooldino said:**
> I understand why it was done after you posted the links, but at the end of the day, the first post still points out the fix.

Thanks for the background info.

I wouldn't call it a fix.  It's more a *" I don't care what the consequences are" *, but it worked for me.  That's fine for you, but you should think of others BEFORE you post anything without documentation.

---

