---
title: "Grep expert?"
date: 2009-07-01
forum: General Help
---

### Post by stereomuffin on 2009-07-01
I would like to use grep or any other tool to copy all text in between "bold" tags from this html code to a new file

```

<b>test</b><span class=font52><b>test2</b><span class=font52><b>test3</b></span></div>

<b>test4</b><span class=font52><b>test5</b><span class=font52><b>test6</b></span>a)
```

So the resulting file should look like this:

test
test2
test3
test4
test5
test6

Anyone can help me out? :)

After that is done i need to make a script that can use that new file as an input to match with a huge html document and if it finds a matching word from the input file it needs to create an anchor for it in the html file.

Anyone who can help me out would be.. well.. helpfull ;)

---

### Post by WRDN on 2009-07-01
```
grep -o '<[Bb]>[Aa0-Zz9]*</[Bb]>' inputFile > grepOutput && sed 's/...\(.*\)..../\1/' grepOutput > sedOutput && rm grepOutput
```

Grep grabs all text between the bold tags (upper or lower case). The text is either uppercase characters, lowercase characters or numbers. It outputs it to grepOutput. Sed then removes the first 3 characters from the start of each line, and the last 4 from the end of each line. Finally, it removes the output from grep (but not sed). To avoid these, just remove "&& rm grepOutput" from the end.

---

### Post by benrb on 2009-07-01
This little perl script will also do what you want:

```

#!/usr/bin/perl
open (INFILE, "htmlfile");
open (OUTFILE, ">outfile");
$line = <INFILE>;
while ($line) {
    while ($line =~ /\>(\w[^\<]*)/g) {
        print OUTFILE ("$1\n") if ($1 !~ /^\n/);
    }
    $line = <INFILE>;
}

```

---

### Post by ghostdog74 on 2009-07-02
```

awk 'BEGIN{ RS="</[bB]>"}/<[bB]>/{ gsub(/.*<[bB]>/,"") print }' file

```

---

### Post by stereomuffin on 2009-07-03
Thank you all!!! Really helpful... :p

---

### Post by stereomuffin on 2009-07-03
> **WRDN said:**
> ```
grep -o '<[Bb]>[Aa0-Zz9]*</[Bb]>' inputFile > grepOutput && sed 's/...\(.*\)..../\1/' grepOutput > sedOutput && rm grepOutput
```

Grep grabs all text between the bold tags (upper or lower case). The text is either uppercase characters, lowercase characters or numbers. It outputs it to grepOutput. Sed then removes the first 3 characters from the start of each line, and the last 4 from the end of each line. Finally, it removes the output from grep (but not sed). To avoid these, just remove "&& rm grepOutput" from the end.

Your solution seems to be working out really well, i have one problem though.. there are also many lines in which the text between the bold tags include a comma (,)

Like this:
```

<b>test, yadayada</b>

```

How would i include that in the command aswell? 
Oh and what does (.*\) and \1/ mean exactly?

---

### Post by KeyserSoze93 on 2009-07-03
> **stereomuffin said:**
> Your solution seems to be working out really well, i have one problem though.. there are also many lines in which the text between the bold tags include a comma (,)

Like this:
```

<b>test, yadayada</b>

```

How would i include that in the command aswell? 
Oh and what does (.*\) and \1/ mean exactly?

grep -o '<[Bb]>[^<]*</[Bb]>' < input | sed 's/<\/*[bB]>//g' > output

---

