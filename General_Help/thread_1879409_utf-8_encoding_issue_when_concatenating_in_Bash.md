---
title: "utf-8 encoding issue when concatenating in Bash"
date: 2011-11-11
forum: General Help
---

### Post by mme oscar on 2011-11-11
Hi,

I'm experiencing the following problem: I want to concatenate multiple UTF-8 (Russian) files together, but when I did it the resulting file was not a valid UTF-8 file. This is basically what happens:

```

cat file1.txt >all.txt
cat file2.txt >>all.txt
file *
```Result:
```

all.txt:   Non-ISO extended-ASCII text, with LF, NEL line terminators
file1.txt: UTF-8 Unicode text
file2.txt: UTF-8 Unicode text
```I tested the same operation with the following perl script:

```

 #!/usr/bin/perl

use strict;
use warnings;
use encoding "utf-8";

while (my $filename = shift) {
    open(FILE, "<:encoding(utf-8)", $filename) or die("can not open file $filename");
    while (<FILE>) {
    print "$_";
    }
    close(FILE);
}

```and this time everything works fine:

```

concat.pl file1.txt file2.txt > all-perl.txt
file *
``````

 all-perl.txt:      UTF-8 Unicode text

```Besides "wc -c" also says that there is not the same number of characters in both files:
```

 4119 all-perl.txt
 4120 all.txt
 2051 file1.txt
 2069 file2.txt

```... although according to this the final size should be 4120, which is the size of the invalid file (??)

So my question is: what do you think is wrong with the "cat" command? Do you think it is a bug or a configuration problem?

Thanks!

---

### Post by dcstar on 2011-11-11
> **mme oscar said:**
> Hi,

I'm experiencing the following problem: I want to concatenate multiple UTF-8 (Russian) files together, but when I did it the resulting file was not a valid UTF-8 file. This is basically what happens:

```

cat file1.txt >all.txt
cat file2.txt >>all.txt
file *
```Result:
```

all.txt:   Non-ISO extended-ASCII text, with LF, NEL line terminators
file1.txt: UTF-8 Unicode text
file2.txt: UTF-8 Unicode text
```I tested the same operation with the following perl script:

```

 #!/usr/bin/perl

use strict;
use warnings;
use encoding "utf-8";

while (my $filename = shift) {
    open(FILE, "<:encoding(utf-8)", $filename) or die("can not open file $filename");
    while (<FILE>) {
    print "$_";
    }
    close(FILE);
}

```and this time everything works fine:

```

concat.pl file1.txt file2.txt > all-perl.txt
file *
``````

 all-perl.txt:      UTF-8 Unicode text

```Besides "wc -c" also says that there is not the same number of characters in both files:
```

 4119 all-perl.txt
 4120 all.txt
 2051 file1.txt
 2069 file2.txt

```... although according to this the final size should be 4120, which is the size of the invalid file (??)

So my question is: what do you think is wrong with the "cat" command? Do you think it is a bug or a configuration problem?

Thanks!

Try:
```
cat -Up8
```
[http://www.mkssoftware.com/docs/man1/cat.1.asp](http://www.mkssoftware.com/docs/man1/cat.1.asp)

---

### Post by mme oscar on 2011-11-12
Hi David,

thanks for your answer but my version of cat (the standard one)  doesn't have such an option: the link you gave is about a special "MKS" version of cat, isn't it?

```
cat --version
cat (GNU coreutils) 8.5

```

---

