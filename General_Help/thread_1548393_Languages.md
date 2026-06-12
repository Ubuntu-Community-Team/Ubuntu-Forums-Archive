---
title: "Languages"
date: 2010-08-08
forum: General Help
---

### Post by Bert Mariën on 2010-08-08
I'm using Lucid GNOME.

I normally have English and Dutch installed; English as my desktop language, Dutch for numbers etc.

As of earlier today it always boots into Dutch, although I log in with English UK. (It has happened before in Lucid, but than I restored a backup.)

Somehow I can NOT adjust it with the available programs.

Can someone please point me to a file (both for root and user) where I can change it manually?
Also please tell me how I need to adjust that file?

Thank you.

---

### Post by chopinhauer on 2010-08-08
> **Bert Mariën said:**
> 
Can someone please point me to a file (both for root and user) where I can change it manually?
Also please tell me how I need to adjust that file?


What does 'locale' tell you? The XSession script in Ubuntu sources the files ~/.profile and /etc/profile (and ~/.xprofile /etc/xprofile), you can put your locale settings there. For example:
```

export LC_NUMERIC="nl_NL.utf8"

```Look at the [locale manpage]("http://manpages.ubuntu.com/manpages/lucid/en/man1/locale.1.html") for the different variables. The rules are: LC_ALL if set overwrites everything, LC_* go next, if nothing is set for the category, the value in LANG is used.

---

### Post by Bert Mariën on 2010-08-08
I can not really see at the moment, because I'm in Windows now, and I do not have anymore time today.

Just point me to the file I need to change (probably you already did) and how I need them to change to get

- English desktop
- Dutch numbers

Thank you.

---

### Post by chopinhauer on 2010-08-08
> **Bert Mariën said:**
> I can not really see at the moment, because I'm in Windows now, and I do not have anymore time today.

The manpage link I gave you is for a web page (the Ubuntu site also have all the manpages online).

> **Bert Mariën said:**
> 
Just point me to the file I need to change (probably you already did) and how I need them to change to get

- English desktop
- Dutch numbers


The file is /etc/profile or .profile in your home directory, you have to add:
```

LC_NUMERIC="nl_NL.utf8"
LANG="en_US.utf8"

```but your desktop language will be overwritten by your choice on the login screen (or the value in ~/.dmrc)

---

### Post by Bert Mariën on 2010-08-08
Thank you very much. I'll look at it tomorrow.

Thanks again.

---

### Post by Bert Mariën on 2010-08-08
Isn't the "Community" great?

I do love the Linux community. There is always somebody that helps you!

---

