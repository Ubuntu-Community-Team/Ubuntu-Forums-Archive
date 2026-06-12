---
title: "How to install Lingua::LinkParser in perl?"
date: 2010-03-26
forum: General Help
---

### Post by Xavier Oddmon on 2010-03-26
Hello! I am (nearly literally) pulling my hair out trying to figure out how to get the Lingua::LinkParser module in perl. Google has been a phenomenal lack of help. 

I read about it here: [http://www.foo.be/docs/tpj/issues/vol5_3/tpj0503-0010.html](http://www.foo.be/docs/tpj/issues/vol5_3/tpj0503-0010.html)

They link to a web page which appears to host the project, but I can't figure out what to get from there that will work in perl. I found version 1.4 on a yahoo pages site of all places, which won't compile. I have liblink-grammar4 and liblink-grammar4-dev installed. 

I honestly don't know what to do, any help at all would be greatly appreciated!

Also, i'm not really sure where to put this post, but it sounded pretty general to me.

---

### Post by Xavier Oddmon on 2010-03-26
...how does this always happen? I spend an hour and forty five minutes searching around the internet. I post my issue, I go to the next page, bingo, problem solved. Sorry about that.

For anyone else who is interested: you need to compile link-grammar from the abisource svn. It appears you can't build lingua::linkparser with the link-grammar packages from the repositories. After building those, you can build Lingua-LinkParser-1.14 (which can be obtained from cpan.org) in a straightforward manner.

---

### Post by luigi_mb on 2010-03-26
> **Xavier Oddmon said:**
> ...how does this always happen? I spend an hour and forty five minutes searching around the internet. I post my issue, I go to the next page, bingo, problem solved. Sorry about that.

For anyone else who is interested: you need to compile link-grammar from the abisource svn. It appears you can't build lingua::linkparser with the link-grammar packages from the repositories. After building those, you can build Lingua-LinkParser-1.14 (which can be obtained from cpan.org) in a straightforward manner.

Try

```

$ sudo perl -MCPAN -e shell
$ cpan> install lingua::linkparser

```

/luigi

---

