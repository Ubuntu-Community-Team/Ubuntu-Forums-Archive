---
title: "Is it possible to edit the default programs the mail icon (in indicator applet)uses?"
date: 2010-05-01
forum: General Help
---

### Post by switch10 on 2010-05-01
I am looking for a way to edit the default programs the mail icon, included with the indicator applet, on the task bar uses.  More specifically, I would like a way to integrate "checkgmail" instead of evolution.

I did:

```
 locate indicator-applet 
```

and it printed several possible files, none of which look like they could be edited in this way.

Has anyone done this before?  It must be possible...

---

### Post by P4man on 2010-05-01
Not yet possible. There are experimental plugins to make it work with thunderbird, but nothing else yet that im aware off. However, consider using evolution and use it to access your gmail through IMAP.

---

### Post by switch10 on 2010-05-01
> **P4man said:**
> Not yet possible. There are experimental plugins to make it work with thunderbird, but nothing else yet that im aware off. However, consider using evolution and use it to access your gmail through IMAP.

Yes, I have moved away from desktop based email clients a few months ago, and I don't plan on going back.

Is it closed source or something?  How is it not possible?

I realize that I won't find a plugin for this, I'm thinking more along the lines of editing, or adding to the source manually.  I am just having trouble finding it...

---

### Post by P4man on 2010-05-01
> **switch10 said:**
> Yes, I have moved away from desktop based email clients a few months ago, and I don't plan on going back.

you dont have to. using gmails imap interface, evolution will be little more than a glorified checkgmail. It wont download all your mails or anything, just show the titles
> 
Is it closed source or something?  How is it not possible?

I realize that I won't find a plugin for this, I'm thinking more along the lines of editing, or adding to the source manually.  I am just having trouble finding it...

Have a look here:
[https://wiki.ubuntu.com/MessagingMenu](https://wiki.ubuntu.com/MessagingMenu)

let me know when you managed to integrate checkgmail, as Im interested too :)

---

### Post by techunit on 2010-05-01
This would be encredibly usefull

---

### Post by switch10 on 2010-05-02
got it..  here you go guys...

[http://u-bunted.blogspot.com/2010/05/how-to-integrate-gmail-notifier-to.html](http://u-bunted.blogspot.com/2010/05/how-to-integrate-gmail-notifier-to.html)

---

### Post by P4man on 2010-05-03
that looks awesome! Ill check it out. Is the source available?

---

### Post by switch10 on 2010-05-03
> **P4man said:**
> that looks awesome! Ill check it out. Is the source available?

Actually, I didn't even have to write it.  There are a few out there apparently.  

It works great with 10.04, but I cannot seem to get it to work with 9.10...

---

