---
title: "Need to Generate an Output File From Alternate Bytes of Input File"
date: 2010-07-14
forum: General Help
---

### Post by SillySod on 2010-07-14
I need to be able to create a file which takes every other byte from an existing file and writes them to the new file, beginning with the first byte.

So if the existing file contains these bytes:

00 00 48 00 75 00 67 00 6F

I want the output file to give me:

00 48 75 67 6F

Can this be done?

---

### Post by CannibalZerg on 2010-07-15
```

#!/usr/bin/perl

$srcfile = "/home/user_name/bin_in";
$dstfile = "/home/user_name/bin_out";

open(FILE, $srcfile) or die "can't open $srcfile: $!";
open(DST,">".$dstfile) or die "can't open $dstfile: $!";

binmode(FILE);
binmode(DST);
$even_flag = 0;
while (read(FILE, $buff, 8*1024)) {
    foreach (split(//, $buff)) {
        if($even_flag){
             print DST $_;
        }
        $even_flag = !$even_flag;
    }
}

close(FILE);
close(DST);


```

---

### Post by SillySod on 2010-07-15
Thanks ever so much, just the job, although I had to change $even_flag = 0; to $even_flag = 1; otherwise it was keeping all the null bytes instead of the ones I wanted.

Next question - when I've finished editing my new file and I want to write a file back which re-inserts the null byte at every other byte, how would I do this?  The bytes to be inserted will always be 0, although it probably doesn't matter since they will be ignored whatever they contain.

---

### Post by CannibalZerg on 2010-07-15
Are you trying to convert text file from UTF-16 to UTF-8 and vice versa?
```

  iconv -f UTF-16BE -t UTF-8 text16.txt > text8.txt
  iconv -f UTF-8 -t UTF-16BE text8.txt > newtext16.txt

```If first command produce wrong output then try to change "UTF-16BE" to "UTF-16"

---

### Post by SillySod on 2010-07-19
Not exactly, the file I have is a dump of a compact flash card connected via USB, which I made using the dd command.

The card is used in an old 8-bit system, so it discards the second byte of every 16-bit word the card sends to it.

What I need to be able to do is get the data from the card, strip out all the bytes I don't need, so that it's in a readable format, and so that it can be used in other utilities which are expecting 8-bit data.

When I've finished doing this, I need to put all the alternate zero bytes back in so that I can write back to the card with dd.

---

### Post by CannibalZerg on 2010-07-19
```
#!/usr/bin/perl

$srcfile = "/home/user_name/bin_out";
$dstfile = "/home/user_name/bin_in1";

open(FILE, $srcfile) or die "can't open $srcfile: $!";
open(DST,">".$dstfile) or die "can't open $dstfile: $!";

binmode(FILE);
binmode(DST);
while (read(FILE, $buff, 8*1024)) {
    foreach (split(//, $buff)) {
        printf(DST"%c",0x00);
        print DST $_;
    }
}

close(FILE);
close(DST);


```

---

