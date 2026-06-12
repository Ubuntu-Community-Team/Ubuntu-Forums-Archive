---
title: "svn error after installation..."
date: 2006-01-31
forum: General Help
---

### Post by Vegettex on 2006-01-31
Hi there!

I used this HOWTO to install svn:

[http://ubuntuforums.org/showthread.php?t=51753](http://ubuntuforums.org/showthread.php?t=51753)

It worked great but after that i got stuck... :(

Everything from your tutorial went fine and to continue I went to this site ( [http://www.cbcb.duke.edu/~faheem/svn_tutorial/svn.en.html](http://www.cbcb.duke.edu/~faheem/svn_tutorial/svn.en.html) ) and I skipped the first section (since the installation was already done).

I followed the steps there just aswel but here it goes wrong:
> Observe that subversion does not currently know about the test directory.

[faheem@local] ~/wc/test$  cd ..; svn st
?      test

I get the error: 
> svn: '.' is not a working copy


Anybody can put a thought on this?

Thanks in advance!

Greetz,

 - Vegettex

---

### Post by mvaniersel on 2006-01-31
It means the directory wc is not a working copy... Did something go wrong at the svn co step? You could try removing the wc directory completely and doing the checkout (co) again.

---

