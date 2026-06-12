---
title: "Quick QUESTION on permissions..."
date: 2010-06-07
forum: General Help
---

### Post by OSXniCKels on 2010-06-07
Hi.

I figure this is a simple question and could get a simple answer.  I hope someone can help me.  I'm sure many other questions are more important than this one, but here goes:

What is the difference between 0750 and 750?  Not the specific numbers but the format of them.  I know the difference between 750, 755, 777, 600, etc, but is there a functional difference between using a preceding zero and not using one?

Thank you for your help.

--OSXniCKels

---

### Post by Smart Viking on 2010-06-07
I think the zero have something to do with root or whatever, anyway i never use it, i don't see a point in making the command 1 character longer when it does not do anything. :)

---

### Post by SlidingHorn on 2010-06-07
found a pretty good explanation here: [http://forums.whirlpool.net.au/forum-replies.cfm?r=19208847#r19208847](http://forums.whirlpool.net.au/forum-replies.cfm?r=19208847#r19208847)

> The three digits don't mean "read", "write", "execute" individually. They're the bitmasks for "owner", "group" and "others".

711 would mean the file's owner can read, write and execute it the file, and all other users can only execute it.

gwmbox, to answer your original question: the value is represented in "octal", ie with the digits 0 through 7 only. In C-based programming languages, octal numbers are usually written with a leading 0, so:

04777

would be interpreted not as the decimal number 4777, but as an octal number (it would actually be equal to the decimal number 2559).

The command-line chmod utility provides two shortcuts: you can leave off the leading 0, or you can leave off the leading 0 and the first bitmask digit (since it represents permission bits that are rarely specified).

In your particular case, one of these rarely specified bits has been set. It's the "set user ID" bit.

---

### Post by OSXniCKels on 2010-06-07
Wow, thank you both very much.  My problem was I didn't really know how to word my question in a google-friendly format.

Anyhow, Ubuntu Forums to the rescue once again!

Thank you so much.

--OSXniCKels

---

### Post by capscrew on 2010-06-08
> **OSXniCKels said:**
> Wow, thank you both very much.  My problem was I didn't really know how to word my question in a google-friendly format.

Anyhow, Ubuntu Forums to the rescue once again!

Thank you so much.

--OSXniCKels

Unfortunately, THIS DOESN'T CORRECTLY ANSWER THE QUESTION!

The attributes you are referring to are known as **advanced file permissions.**  See [**_here_**]("http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php") for a basic overview.

Or you can look at the a Google search on the term [**_here _**]("http://www.google.com/search?hl=en&q=advanced++file+permission+linux&aq=f&aqi=&aql=&oq=&gs_rfai=").

---

