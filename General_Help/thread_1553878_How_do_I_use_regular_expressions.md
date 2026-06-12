---
title: "How do I use regular expressions?"
date: 2010-08-15
forum: General Help
---

### Post by redfox1160 on 2010-08-15
I want to use regular expressions and sed to remove html tags from a text file. How would I do this? Thanks.

---

### Post by Vaphell on 2010-08-15
[http://www.unixguide.net/unix/sedoneliner.shtml](http://www.unixguide.net/unix/sedoneliner.shtml)

# remove most HTML tags (accommodates multiple-line tags)
sed -e :a -e 's/<[^<]*>/ /g;/</{N;s/\n/ /;ba;}'

redirect output to a file

---

### Post by redfox1160 on 2010-08-15
> **Vaphell said:**
> [http://www.unixguide.net/unix/sedoneliner.shtml](http://www.unixguide.net/unix/sedoneliner.shtml)

# remove most HTML tags (accommodates multiple-line tags)
sed -e :a -e 's/<[^<]*>/ /g;/</{N;s/\n/ /;ba;}'

redirect output to a file

Thanks

---

