---
title: "terminal navigation problem - ampersand in pathname"
date: 2010-01-13
forum: General Help
---

### Post by oygle on 2010-01-13
If I want to go to a path like /bold and beautiful/ , the terminal navigation is

```

cd /bold\ and\ beautiful

```

but , if the pathname is /bold & beautiful/ , using the backslash doesn't work ??

That is, this ..

```

cd /bold\ &\ beautiful

```

doesn't work ??

Oygle

---

### Post by blueridgedog on 2010-01-13
How about:

cd /bold\ \&\ beautiful

or single or double quotes around the name.

---

### Post by oygle on 2010-01-13
The first one didn't work, however single quotes around the whole pathname worked fine. No doubt if I move or copy files that are in paths containing ampersands, then the single quote will be needed.

Thanks very much.  :)

---

### Post by blueridgedog on 2010-01-13
Great.  I suggest that you stay away from such names as a mater of form.

---

### Post by oygle on 2010-01-13
Yes, when I make a path, I will usually use an underscore if 2 names. Just that these names are 'inherited' in Kmail, from a pegasus Mail import. So, we have folders like /Fred & Martha/ .

Thanks.  :D

---

