---
title: "No interpreter found - php"
date: 2010-08-22
forum: General Help
---

### Post by NertSkull on 2010-08-22
I don't know if this should be here or server stuff.

I'm trying to get php5 to work through a script, but I get the following error

```
-bash: ./test_file.php: /user/bin/php^M: bad interpreter: No such file or directory
```

I have installed php5 and php5-cli

If I do whereis php5 I get

```
php5: /usr/bin/php5 /etc/php5 /usr/lib/php5 /usr/share/php5 /usr/share/man/man1/php5.1.gz
```

or whereis php gives me
```
php: /usr/bin/php /usr/share/man/man1/php.1.gz
```

So I'm pretty sure I have things installed right.

I've tried all sorts of file permissions and I can't get it to run.

My script starts with 
#!/usr/bin/php

But I've tried 
#!/usr/bin/php5

and neither work.

I also tried making sure I don't have any weird carriage returns (the ^M made me think of that) but I can't find any using nano or vim.  

I've had this working before (a year ago, this is a fresh install) and I can't remember for the life of me what I have forgotten to do.  Thanks everyone

UPDATE:

So I wanted to make sure on that trailing character issue.  So I did the following command to be sure

```
tr -d '\r' < test_file.php > temp.php ; mv temp.php test_file.php
```

And now I get this error (basically the same)

```
-bash: ./test_file.php: /user/bin/php5: bad interpreter: No such file or directory
```

So basically the same thing, but without the ^M.  So those are gone, but still it claims it can't find the interpreter, when it clearly is there.  I'm lost....

---

