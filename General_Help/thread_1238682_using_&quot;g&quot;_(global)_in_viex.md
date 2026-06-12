---
title: "using &quot;g&quot; (global) in vi/ex"
date: 2009-08-12
forum: General Help
---

### Post by RobertL on 2009-08-12
I need to find every occurrence of a certain text, then insert a new line containing specific text immediately after it. So if the original file is:

start
line 1
line 2
start
line 3
start
line 4
line 5

I need to change it to this:

start
new line
line 1
line 2
start
new line
line 3
start
new line
line 4
line 5

So I need to find every line containing "start" and add a line after it containing the fixed text "new line". From my reading of the ex manual I thought this would work:

:g/start/a
new line
.

but it doesn't. Instead it moves to the last line containing "start" and doesn't make any changes. I've tried all the variations I can think of, and I've tried yanking a copy of the new line manually first and then using :g/start/p    but I can't get anything to insert new lines. Of course my file is big or I could do it manually. (several thousand lines)

---

### Post by DaithiF on 2009-08-12
Hi,
i would generally recommend using sed for something like this, but you can do it in vi/ex as follows:
:g/start/normal onewline

cheers
d

---

### Post by DaithiF on 2009-08-12
and just for the record, using sed the equivalent would be:
sed '/start/anewline' somefile > newfile

or
sed -i '/start/anewline' somefile
to make the changes in-place to your file (once you're sure you know it works!)

---

