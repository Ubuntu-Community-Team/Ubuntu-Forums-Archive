---
title: "Quick help with tiny script?"
date: 2009-12-12
forum: General Help
---

### Post by six30two on 2009-12-12
I need to write a really quick script that will read a log file and filter out only failed login attempts.

Can I get any help with this? It doesn't need to be fancy - it just needs to be written in bash.

I have something like this:

#! /bin/bash
cat < $file > results 2> /dev/null

This so far will read the $file from top to bottom, copying it into the "results" file, and sending any errors to the trash.

But how do I tell it to only copy over lines that say something about a failed login, and ignore the rest?

---

### Post by kmac on 2009-12-12
> **six30two said:**
> I need to write a really quick script that will read a log file and filter out only failed login attempts.

Can I get any help with this? It doesn't need to be fancy - it just needs to be written in bash.

I have something like this:

#! /bin/bash
cat < $file > results 2> /dev/null

This so far will read the $file from top to bottom, copying it into the "results" file, and sending any errors to the trash.

But how do I tell it to only copy over lines that say something about a failed login, and ignore the rest?

cat < $file > | grep fail > ~/failedlog.txt

---

### Post by six30two on 2009-12-12
> **kmac said:**
> cat < $file > | grep fail > ~/failedlog.txt

... :(

Thank you. I keep forgetting grep. I must have missed that class,

---

