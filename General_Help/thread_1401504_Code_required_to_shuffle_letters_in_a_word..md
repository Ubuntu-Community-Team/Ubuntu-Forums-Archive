---
title: "Code required to shuffle letters in a word."
date: 2010-02-08
forum: General Help
---

### Post by Rytron on 2010-02-08
Hi.
Does someone have code or a program that will randomly shuffle letters in a word?
For example: Hamill turns into Limahl

---

### Post by lotharmat on 2010-02-08
> **Rytron said:**
> Hi.
Does someone have code or a program that will randomly shuffle letters in a word?
For example: Hamill turns into Limahl


an is a good anagram generator

```
sudo apt-get-install an
```

---

### Post by Rytron on 2010-02-08
Hi lotharmat. Its not an anagram that I want though. The output word doesn't**** have to be a normal word. I just need to have the letters shuffled and still have just one word. Something akin to [here]("http://www.maxi-pedia.com/word+letter+mixer+disorganizer") (unfortunately the first and last letters don't get shuffled!).

---

### Post by gmargo on 2010-02-08
Here's a simple perl script, which I called "shuffle.pl".  Comment out the first print to only print the shuffled word:

```

#!/usr/bin/perl -w
use strict;
use warnings;

use List::Util qw(shuffle);

foreach my $word (@ARGV)
{
    print "$word  ==>  ";
    print join("", shuffle(split("",$word)))."\n";
}

```Here's an example of it running:
```

$ shuffle.pl Hello World
Hello  ==>  lolHe
World  ==>  lrWdo

```

---

### Post by Rytron on 2010-02-08
Thank you gmargo. Perfect. :P

Edit: Should the above say:
```
**perl** shuffle.pl Hello World
Hello  ==>  lolHe
World  ==>  lrWdo
```

---

