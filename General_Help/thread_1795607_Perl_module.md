---
title: "Perl module"
date: 2011-07-03
forum: General Help
---

### Post by Bobscrachy on 2011-07-03
How do I use a perl module? Am I suppose to call it from the terminal?

---

### Post by Bobscrachy on 2011-07-03
Is this a stupid question, or is there just nobody answering these threads here anymore?

---

### Post by gmargo on 2011-07-03
I guess the question is confusing, because to "use" a Perl module, you must **use** it from a program or another module.  

Here's a simple example.  The "List::Util" module is **use**d, and the "shuffle" function name is pulled into the current namespace.  Note that other functions in a **use**d module are accessible with the full module/function name.

```

#!/usr/bin/perl -w
use strict;
use warnings;
use List::Util qw (shuffle);

my @strs = ( "Hello", "There", "Fine", "World" );

print "orig=".join(' ', @strs)."\n";
print "shuf=".join(' ', shuffle @strs )."\n";
print "maxs=".join(' ', List::Util::maxstr @strs )."\n";

``````

$ ./perltest1.pl
orig=Hello There Fine World
shuf=There World Fine Hello
maxs=World

```

---

