---
title: "perl regex returning more than expected"
date: 2010-03-05
forum: General Help
---

### Post by edpatterson on 2010-03-05
I have tried everything except the correct syntax :)

I am trying to pull **** the domain name out of a list of domains & domain/resource... It works if there is only one / on the line but returns everything except the last \/.*

I am expecting 5 lines with just patterson.com.
```

while(<DATA>){
  if($_ =~ m/^(.*)\/.*/){
    print "$1\n";
  } else {
    print;
  }
}
__DATA__
patterson.com
patterson.com/ed
patterson.com/ed/work
patterson.com/ed/work/hours
patterson.com/ed/work/hours/project

```

---

### Post by cjhabs on 2010-03-05
> **edpatterson said:**
> I have tried everything except the correct syntax :)

I am trying to pull **** the domain name out of a list of domains & domain/resource... It works if there is only one / on the line but returns everything except the last \/.*

I am expecting 5 lines with just patterson.com.
```

while(<DATA>){
  if($_ =~ m/^(.*)\/.*/){
    print "$1\n";
  } else {
    print;
  }
}
__DATA__
patterson.com
patterson.com/ed
patterson.com/ed/work
patterson.com/ed/work/hours
patterson.com/ed/work/hours/project

```
Try this
```

#!/usr/bin/perl

while(<DATA>){
  if($_ =~ m|([^/]*).*|) {
    print "$1\n";
  } else {
    print;
  }
}
__DATA__
patterson.com
patterson.com/ed
patterson.com/ed/work
patterson.com/ed/work/hours
patterson.com/ed/work/hours/project

```

---

### Post by edpatterson on 2010-03-05
> **cjhabs said:**
> Try this
```

#!/usr/bin/perl

while(<DATA>){
  if($_ =~ m|([^/]*).*|) {
    print "$1\n";
  } else {
    print;
  }
}
__DATA__
patterson.com
patterson.com/ed
patterson.com/ed/work
patterson.com/ed/work/hours
patterson.com/ed/work/hours/project

```

skips the patterson.com/ed line
Actually it did not skip the patterson.ed line, it simply printer the extra \n. I added a chomp; to the start of the script to fix it.

Thanks a million! Back to my Mastering Regular Expressions book to see what I missed.

---

