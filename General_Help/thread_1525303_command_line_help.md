---
title: "command line help"
date: 2010-07-06
forum: General Help
---

### Post by GlideKensington on 2010-07-06
After I use the 'find' command line tool to find a file, how can I redirect the result to another tool?

Example:
> find . -name blah.txt
Result: ./SomeDirectory/blah.txt

I would like to send that result to vim so I wouldn't have to type out "vim ./SomeDirectory/blah.txt"

Thanks.

---

### Post by Muttley99 on 2010-07-06
[HTML]find / -name xxxx | nano[/HTML]

---

### Post by GlideKensington on 2010-07-06
> **Muttley99 said:**
> [HTML]find / -name xxxx | nano[/HTML]

When I tried doing that, it said....

```
Received SIGHUP or SIGTERM

Buffer written to nano.save
```

When I tried to pipe it to vim it said...

```
Vim: Warning: Input is not from a terminal
Vim: Error reading input, exiting...

Vim: Finished.
```

---

### Post by Leppie on 2010-07-06
try like this:
```
find . -name blah.txt -exec vim {} \;
```

---

### Post by Leppie on 2010-07-06
> **Muttley99 said:**
> ```
find / -name xxxx | nano
```
the normal pipeline , e.g. "|" does not work with find.

---

### Post by GlideKensington on 2010-07-06
> **Leppie said:**
> the normal pipeline , e.g. "|" does not work with find.


Thanks, that worked! 

Is there a reason why the normal pipeline doesn't work with find?

---

### Post by geirha on 2010-07-06
Editors don't expect to get a list of filenames on stdin, they expect them as arguments, that's why find ... | vim  fails.

```
find . -type f -name "*foo*.txt" -exec vim {} +
```

You can use a pipe too if you use xargs, which turns stdin into arguments, but it's pointless, as -exec + already passes the files on as arguments. If you do use xargs, always use \0 as delimiter otherwise you'll have problems with filenames containing certain characters, like newlines and quotes.

```
find . -type f -name "*foo*.txt" -print0 | xargs -0 vim
```

See [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by Muttley99 on 2010-07-07
> **GlideKensington said:**
> Thanks, that worked! 

Is there a reason why the normal pipeline doesn't work with find?

Just tried it, worked for me! outputted to my home directory.

---

