---
title: "can't use ! on the command line"
date: 2009-11-12
forum: General Help
---

### Post by elj4176 on 2009-11-12
I'm trying to mount a windows share from the command line and there is an ! in the users credentials. When the command is run it appears to be inserting the last used command in place of the ! so the credentials are wrong.
So if the users password is J!mmy and the last used command was ls -la it seems to be inserting the ls -la in place of the ! so the command is Jls -lammy
How do I turn this off?

---

### Post by samuelhug on 2009-11-12
have you tried putting a backslash before the ! like this?  J\!mmy

---

### Post by tuwe on 2009-11-12
> **elj4176 said:**
> I'm trying to mount a windows share from the command line and there is an ! in the users credentials. When the command is run it appears to be inserting the last used command in place of the ! so the credentials are wrong.
So if the users password is J!mmy and the last used command was ls -la it seems to be inserting the ls -la in place of the ! so the command is Jls -lammy
How do I turn this off?

You have to escape the ! character. Try J\!mmy instead of J!mmy.

---

### Post by elj4176 on 2009-11-12
That works! I know to escape the space but did not think to  try it for this. I did get it to work by putting the command in a script and running the script.

Thanks\!

---

