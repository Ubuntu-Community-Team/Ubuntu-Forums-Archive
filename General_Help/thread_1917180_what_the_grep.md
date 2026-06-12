---
title: "what the grep?"
date: 2012-01-29
forum: General Help
---

### Post by conradin on 2012-01-29
Hi All!
Im trying to write a regular expression to match money in a document. Nothing too complex, no negatives money. I do want cents, but nothing like $4.567. I only want matches like $4.56 but Im confused about specifying only 2 numbers after a period. What I have is:
```
grep '\$[1-9]\..[0-9]' <filename>
```
but that returns both:
$1.00
$3.090
which is what I don't want.
Im reading some books on grep but I haven't found anything helpful yet. Do any of the knowledgeable Ubuntu forum users have any insights?

---

### Post by jim_deadlock on 2012-01-29
With perl regexes the $ sign represents end of line, the same probably applies here so try sticking $ on the end.

```
grep '\$[1-9]\..[0-9]$' <filename>
```

---

### Post by sanderd17 on 2012-01-29
Grep will in any case return all lines that have such a regex in it. The string "$3.090" does contain your 1 digit, followed by a point and two digits. So grep returns that line.

I don't know what the EOL symbol is in grep, I only explained why Jim_deadlock would want to add an EOL.

---

### Post by jim_deadlock on 2012-01-29
If you have prices in the middle of sentences then the EOL won't work, as sanderd17 says, so try this:

```
grep '\$[1-9]*\.[0-9]{2}[^0-9]' <filename>
```

It will return $n.nn only if it's followed by a non-digit character. It would help to see a sample block of text that you're trying to extract your regex from.

---

### Post by conradin on 2012-01-29
Hey Thanks Jim!
That does almost what I want, but  still fails at  items like:
$23.54. 
$23.55. $23.56
where there are muliple values on the same line, or at the end of a line.

---

### Post by conradin on 2012-01-29
> **jim_deadlock said:**
> If you have prices in the middle of sentences then the EOL won't work, as sanderd17 says, so try this:

```
grep '\$[1-9]*\.[0-9]{2}[^0-9]' <filename>
```

It will return $n.nn only if it's followed by a non-digit character. It would help to see a sample block of text that you're trying to extract your regex from.

Um that didnt work at all. Here are the contents of my test file:
0000000000
1111111111
2222222222
3333333333
$000000000
5555555555
0.5
$1.00 stuff
123$
$2,2
$3.090  $3
$123
Blah blah $23.54. 
$23.55. $23.56


Im starting to wish there was a gui, or grep compiler for making regular expressions.

---

### Post by Lars Noodén on 2012-01-29
If you need fancier regular expressions, you could use Perl.  That's one of perl's specialties.  There's also egrep.

---

### Post by Slim Odds on 2012-01-29
> **conradin said:**
> Um that didnt work at all. Here are the contents of my test file:
0000000000
1111111111
2222222222
3333333333
$000000000
5555555555
0.5
$1.00 stuff
123$
$2,2
$3.090  $3
$123
Blah blah $23.54. 
$23.55. $23.56


Im starting to wish there was a gui, or grep compiler for making regular expressions.

Learning regular expression might just drive you crazy. The can be quite complex and there are many different implementations depending on the language that you use.

In you case, this might help:
```
grep '\$[1-9]*\.[0-9]{2}[^0-9.]' <filename>
```You can add other characters that you don't want at the end.

Note also that grep is line oriented. You might want use sed or awk instead. Or some combination.

Personally, I'd write a little Ruby program to do it.

---

### Post by conradin on 2012-01-29
I see the insanity mounting. Im trying multiple items with grep, and Im not really sure how to use scripting to get things like this done. Though python has been recommended to me. The mind job for me currently is that there are things that according to the help Ive received, and the books Ive been reading seem like should work, but then return nothing.

---

### Post by Vaphell on 2012-01-29
try this
```
egrep '(^|[[:space:]])[$][0-9]+[.][0-9]{2}([[:space:]]|$)'
```
(start-of-line or space)$9+.9{2}(space or end-of-line). If you allow some chars like . after digits then add them to the ending part.

---

### Post by conradin on 2012-01-29
With this:
egrep '\$[0-9]*\.[0-9][0-9]\b'

I get: (notice that last line. I haven't figured that one out 
$.55
$0.00
$1.10
$2.20
$3.30
$4.40
$5.50
$6.60
$8.80
$66660.10
$66660.10 $66660.10 $66660.10
$9.90
$12.120 $13.13

---

### Post by lswb on 2012-01-29
You can also use "\<" and "\>" in your regex to match the beginning and end of a word, for those cases where the target word is in the middle of a sentence.

---

### Post by jim_deadlock on 2012-01-30
This is how to do it with perl. Paste this into a file called myscript:

```
#!/usr/bin/perl

foreach $in (@ARGV) {
   open (O,$in);
   $_ = join('',<O>);
   while ($_ =~ /(\$\d+\.\d\d)[^\d]/g) { $OUT{$in} .= "$1\n"; }
}
foreach (sort keys %OUT) { print "=== $_ ===\n$OUT{$_}\n"; }
```

...then make it executable and run it:

```
chmod 755 myscript
./myscript inputfile1 inputfile2 inputfile3
```

---

### Post by Vaphell on 2012-01-30
grep prints out whole lines so that non-matching part is printed out either way
you can change that with -w and -o parameters (match words, print only matches)

```
$ echo 'some $12.345 stuff
$.20
$12.333 $1.12' | grep -Ewo '\$[0-9]*\.[0-9]{2}'

$.20
$1.12
```
note that $.20 is in the results. * from your almost working expression should be replaced with +, * matches any-number-including-zero, while + at-least-one. This is a source of many problems, people happily throw .* around forgetting that 'nothing' is perfectly fine result of that :)

---

