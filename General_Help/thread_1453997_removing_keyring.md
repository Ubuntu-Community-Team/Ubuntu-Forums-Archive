---
title: "removing keyring"
date: 2010-04-14
forum: General Help
---

### Post by luvgirl12345 on 2010-04-14
I want to remove/disable keyring. I want it to still save my passwords but not ask for a master password on boot. 

Thanks for any help that might come.
luvgirl12345

[SIZE="1"]p.s. im using 10.4 but it probably works the same...[/SIZE]

---

### Post by lordjubblydave on 2010-04-14
Just set the keyring password to nothing.
When it asks you to type in a new password for the keyring, don't type anything.
Just click ok.
Ubuntu will then advise you that what you have done is not secure, click continue.
Hey presto no more keyring password.

---

### Post by luvgirl12345 on 2010-04-14
How do i reset the password?

---

### Post by mcduck on 2010-04-14
Applications/Accessories/Passwords and Encryption Keys, right-click on the "Passwords:login"-keyring and select "Change Password".

---

### Post by luvgirl12345 on 2010-04-14
if i click use unsafe storage it just asks me for a new password again and doesn't remove it... i will now try deleting the settings in gnome2 and try again. will report back in 10 minutes

---

### Post by philinux on 2010-04-14
> **luvgirl12345 said:**
> if i click use unsafe storage it just asks me for a new password again and doesn't remove it... i will now try deleting the settings in gnome2 and try again. will report back in 10 minutes

When it asks for a new password leave it blank.

---

### Post by mcduck on 2010-04-14
> **luvgirl12345 said:**
> if i click use unsafe storage it just asks me for a new password again and doesn't remove it... i will now try deleting the settings in gnome2 and try again. will report back in 10 minutes

It asks for a new password, but you can just leave the fields for the new password empty.

---

### Post by luvgirl12345 on 2010-04-14
thats what i did... it didn't take it so i deleted all settings and made a new one and then it worked!! i relogged and typed all pw in... until now everythings good lets see if i reboot again. if it works il mark as solved. :lolflag:


edit: SOLVED thanks guys!! you guys are so damn cool xD <snip>

---

### Post by luvgirl12345 on 2010-04-14
nevermind it asked me for the keyring pw again... could someone help? why does it reset to the last pw i had... how does it still know it if deleted all files in /.gnome2/keyring??

**edit:** omfg im sooo dumb... I cant read sorry guys!! it says old password. thats why it couldn't change it... omfg sorry guys and thanks for your help!

---

