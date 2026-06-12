---
title: "prepending *and* appending text to each line in a file"
date: 2012-08-29
forum: General Help
---

### Post by gamblor01 on 2012-08-29
Ok this is getting really annoying.  I could write something in Java to open a file with a BufferedReader, loop through each line, and then output a bunch of strings concatenated together, but I know I have done this sort of thing in the past with awk...so I should be able to do it again!!

I have some parameters for an equation that I basically want to wrap as an insert statement for a DB table.  So I want to concatenate a string to the beginning of each line, and concatenate a different string to the end of each line.  My file has lines like this:

```

$cat modelParams.txt
10	7.495362712	-3.971771483
11	7.826826256	-4.681102507

```


So I want to generate statements such as:

```

insert into foo(a,b,c) values (10,7.495362712,-3.971771483);
insert into foo(a,b,c) values (11,7.826826256,-4.681102507);

```


For now I have been trying to just wrap these strings with "hello" on the front and "world" on the end.  Once I get the syntax right I can change it to the appropriate insert syntax.  I'm trying all sorts of stuff with awk, sed, and even perl -- but I'm clearly missing something really basic.

Here is what I am trying and sample output I'm getting (which is obviously wrong):

```

$ awk '{print "hello " $0 " world"}' modelParams.txt
 world10	7.495362712	-3.971771483
 world11	7.826826256	-4.681102507

```

Where did the "hello " at the front of the string go?  Why did " world" get moved to the front when it should be concatenated to the end?


```

$ awk '{print "hello ",$0," world"}' modelParams.txt
  world10	7.495362712	-3.971771483
  world11	7.826826256	-4.681102507

```

Same problem as first example.

```

$ sed 's/.*/hello & world/' modelParams.txt 
 world10	7.495362712	-3.971771483
 world11	7.826826256	-4.681102507

```

sed seems to exhibit the same behavior.

```

$ awk '{print "a " $1 " b " $2 " c " $3 " d"}' modelParams.txt 
 d10 b 7.495362712 c -3.971771483
 d11 b 7.826826256 c -4.681102507

```

This almost works but again " d" somehow gets placed at the beginning and "a " disappears completely.


```

$ cat foo
#!/usr/bin/perl

open(MYFILE, 'modelParams.txt');

my $first = "hello ";
my $last = " world";

while (<MYFILE>)
{
  chomp;
  my $output = join "", $first , $_ , $last;
  print $output . "\n";
}

close(MYFILE);
$ ./foo
 world10	7.495362712	-3.971771483
 world11	7.826826256	-4.681102507

```


And now perl does the same thing even though it should be concatenating the strings?!??!?!




I'm lost and I'm obviously missing something here.  Can anyone knock some sense into me?  Thanks!

---

### Post by cortman on 2012-08-29
```
awk '{print "prefix" $0 "suffix"}'
```

Works for me.

---

### Post by SeijiSensei on 2012-08-29
Well, I'd use probably use sed.  If the values are separated by tabs, you could use something like:

```
sed 's/^/insert into foo(a,b,c) values ('/g' < file | sed "s/\t/,/g" | sed 's/$/);/g' > file2
```

Sed matches on regular expressions, so you can use ^ to represent the beginning of the line and $ to represent the end.

---

### Post by gamblor01 on 2012-08-29
> **cortman said:**
> ```
awk '{print "prefix" $0 "suffix"}'
```

Works for me.

And I thought that was the syntax I had used in the past as well.  I wound up just writing a little printf statement and doing it in Java which worked beautifully, however I was still perplexed so I decided to redirect output to a file instead of stdout...

It really helps to print this crap to a file -- the guy that sent it to me copied/pasted the info from Excel on Windows.  Once I printed the nonsense to a file I could see exactly what the problem was:

```

$ awk '{print "a ",$1," b ",$2," c ",$3," d"}' modelParams.txt > asdf.sql
$ cat asdf.sql
a  10  b  7.495362712  c  -3.971771483^M  d
a  11  b  7.826826256  c  -4.681102507^M  d

```

It's those pesky ^M characters again!  Simply running fromdos on the file resolves the issue.  I knew I was missing something.  Thanks for the replies.

:)

---

