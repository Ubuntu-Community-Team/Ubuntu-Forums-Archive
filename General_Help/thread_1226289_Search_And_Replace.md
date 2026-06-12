---
title: "Search And Replace"
date: 2009-07-29
forum: General Help
---

### Post by Chamillionaire2 on 2009-07-29
What's Up?

OK, So i ran into some techinal problems with the SED command, so what other way can i replace text via terminal without the use of SED?

Thanks Bye.

---

### Post by kaibob on 2009-07-29
> **Chamillionaire2 said:**
> What's Up?

OK, So i ran into some techinal problems with the SED command, so what other way can i replace text via terminal without the use of SED?

Thanks Bye.

You can use awk. See, for example, item 31 and later in the following site:

[http://www.catonmat.net/blog/awk-one-liners-explained-part-two/](http://www.catonmat.net/blog/awk-one-liners-explained-part-two/)

---

### Post by Chamillionaire2 on 2009-07-29
> **kaibob said:**
> You can use awk. See, for example, item 31 and later in the following site:

[http://www.catonmat.net/blog/awk-one-liners-explained-part-two/](http://www.catonmat.net/blog/awk-one-liners-explained-part-two/)

Ah thanks, i tried using the search and replace command, but i need to be able to change the character "/" and when you use that with the awk command it doesnt work. i have tried this with SED but it ran into some techinal issues.

Anyway around that?

---

### Post by kaibob on 2009-07-29
> **Chamillionaire2 said:**
> Ah thanks, i tried using the search and replace command, but i need to be able to change the character "/" and when you use that with the awk command it doesnt work. i have tried this with SED but it ran into some techinal issues.

Anyway around that?

You can escape the forward slash with a back slash. For example:

```
awk '{ sub(/\//,"slash"); print }' file
```

> kaibob@dell:~$ cat file.txt
test / one
test / two
test / three
kaibob@dell:~$ awk '{ sub(/\//,"slash"); print }' file.txt
test slash one
test slash two
test slash three

This is essentially the same solution as that provided by sisco311 in your other thread on this topic.

---

### Post by ratcheer on 2009-07-29
If you don't want to use sed or awk, do you know perl? It is a little easier to understand, but with a bit more overhead.

Tim

---

