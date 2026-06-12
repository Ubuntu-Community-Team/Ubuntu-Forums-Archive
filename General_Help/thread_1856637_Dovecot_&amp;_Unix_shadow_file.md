---
title: "Dovecot &amp; Unix shadow file"
date: 2011-10-08
forum: General Help
---

### Post by AlexBooton on 2011-10-08
Hi,

I've been having a great deal of trouble getting dovecot to allow users to get mail.  (There is another thread on this that never got a reply.)

Anyway, I tried setting dovecot's password authentication source from "Unix _passwd_ file" to "Unix _shadow_ file".

I did this via webmin but I think the change to the config file is this:

  passdb shadow {
  }

THIS SEEMS TO WORK!  :)

But I don't understand the meaning of what I did.  What is the shadow file and why didn't the other method work?

The Unix passwd file setting was, or appears to be, the default.  I know I didn't change it.

If I fell into this trap, I'd think many others did too.  Yet my attempts to google for an answer were unproductive.

Can anyone shed some light on this?

Thanks in advance.

---

### Post by dcstar on 2011-10-08
> **AlexBooton said:**
> Hi,

I've been having a great deal of trouble getting dovecot to allow users to get mail.  (There is another thread on this that never got a reply.)

Anyway, I tried setting dovecot's password authentication source from "Unix _passwd_ file" to "Unix _shadow_ file".

I did this via webmin but I think the change to the config file is this:

  passdb shadow {
  }

THIS SEEMS TO WORK!  :)

But I don't understand the meaning of what I did.  What is the shadow file and why didn't the other method work?

The Unix passwd file setting was, or appears to be, the default.  I know I didn't change it.

If I fell into this trap, I'd think many others did too.  Yet my attempts to google for an answer were unproductive.

Can anyone shed some light on this?

Thanks in advance.
```
man shadow
man 5 passwd
```

The shadow file contains the Encrypted passwords, the passwd file may not. If your application requires access to the Encrypted passwords and they are only in the shadow file then you have to use it.

---

### Post by AlexBooton on 2011-10-09
> **dcstar said:**
> 
The shadow file contains the Encrypted passwords, the passwd file may not. If your application requires access to the Encrypted passwords and they are only in the shadow file then you have to use it.

Thanks for the feedback.  That explains the need for the shadow file.

But if Dovecot requires the shadow file; why isn't it set as the default?  This caused me several days of frustration.

---

