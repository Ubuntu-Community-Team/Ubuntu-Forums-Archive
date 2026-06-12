---
title: "Generating file with fixed size and random content"
date: 2010-08-03
forum: General Help
---

### Post by 7raTEYdCql on 2010-08-03
How do I generate files say 10MiB in size filled with random content.

I thought of using dd, haven't found good enough documentation for it.
Can someone please help.

---

### Post by sisco311 on 2010-08-04
```
dd if=/dev/random of=./file bs=1M count=10
```
**count=10** means, we want the file to contain 10 blocks of **bs=1M**, which means block size = 1 mebibyte (1 048 576 bytes).

For more info, check out the man page and for some examples:
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD)

EDIT:
Oh, /dev/random is a special file that serves as a pseudorandom number generator.
[http://en.wikipedia.org/wiki//dev/random](http://en.wikipedia.org/wiki//dev/random)

---

### Post by 7raTEYdCql on 2010-08-04
Sheesh.. that was pretty simple. Thanks though.

---

### Post by sisco311 on 2010-08-04
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

### Post by 7raTEYdCql on 2010-08-04
Done.

---

### Post by mcduck on 2010-08-04
As an extra tip, you might want to use /dev/urandom instead of /dev/random if you need anything more than a very small amount of random data, and you don't need extremely high quality randomness (for some important cryptography task or something like that)

/dev/random us very strict about the size of the entropy pool, and will block if it thinks the entropy level isn't high enough. Which *will* happen over and over again when using it to create large amounts of data, slowing whatever you are doing while /dev/random waits for the entropy pool to fill. 

/dev/urandom doesn't have the blocking problem, and the generated random data is still good enough even for most cryptography tasks.

So, if you are creating an important cryptography key, use /dev/random. For pretty much everything else you'll want to use /dev/urandom for much better performance.

---

