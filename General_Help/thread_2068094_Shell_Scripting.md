---
title: "Shell Scripting"
date: 2012-10-08
forum: General Help
---

### Post by rohit verma on 2012-10-08
how to replace Alt+Enter from within text file .

sample input book2.txt is below..

1212||sdfsdfsdf fgkdjfkgljlsdfg||sdfsdf
4454||"sadfsdfg
sdfgsdfg
sdf"||sdfgdfg
4454||ds gkdkjfhgskjfsdhkjg||sdfsdf

in above data, each line start with number. and is "||" delimited, but the 3rd record is broken into 3 lines due to alt+enter.

sed cntrl+J not helped ):P

Regards
Rohit

---

### Post by Habitual on 2012-10-08
replace it with what?

---

### Post by The Cog on 2012-10-08
Sorry, I don't understand. What are you trying to replace, and what are you trying to put there instead?

---

### Post by rohit verma on 2012-10-08
Thanks buddies for response..

i need to replace Alt+enter  with any character...
Blank space / abc any thing


regards 
Rohit:)

---

### Post by The Cog on 2012-10-08
I don't know what you mean by Alt-Enter. Can you provide before and after examples? Printouts of commands like:
> hd before-file
hd after-file
would be great.

Are you trying to merge all the lines together as one long line?

---

### Post by rohit verma on 2012-10-08
hi the cog,

sample input u can build by following below steps.
1>open ms excel (on windows :) ).
2>fill 2 to 3 cells in 2 or more row.
3>while editing any cell , hit Alt + Enter  and u will see new line in same cell, write few more text in new line.
4>save file as tab delimited .txt file .
5> open the same in any text editor..
6> you will find line on which you used (alt + enter) is broken..


hope i am not confusing you all.. Sorry if so.

---

### Post by rohit verma on 2012-10-08
Input ::
1212||sdfsdfsdf fgkdjfkgljlsdfg||sdfsdf
4454||"sadfsdfg
sdfgsdfg
sdf"||sdfgdfg
4454||ds gkdkjfhgskjfsdhkjg||sdfsdf


Output:::
1212||sdfsdfsdf fgkdjfkgljlsdfg||sdfsdf
4454||"sadfsdfg sdfgsdfg sdf"||sdfgdfg
4454||ds gkdkjfhgskjfsdhkjg||sdfsdf

---

### Post by steeldriver on 2012-10-08
If you just want to strip all occurrences of a particular character you could just use 'tr'

However if the character occurs elsewhere and you only want to replace it in this particular context, you could try modifying this standard sed one-liner:

>  # if a line begins with an equal sign, append it to the previous line  # and replace the "=" with a single space  
sed -e :a -e '$!N;s/\n=/ /;ta' -e 'P;D'so that it joins lines when the following line does NOT begin with a digit, e.g.

```
sed -e :a -e '$!N;s/\n\([^0-9]\)/\1/;ta' -e 'P;D'
```If the separating character really is something other than newline (\n) you should be able to specify it via its ASCII hex value e.g. for \n you could also write (substitute your \x value as appropriate)

```
sed -e :a -e '$!N;s/\xA\([^0-9]\)/\1/;ta' -e 'P;D'
```

---

### Post by The Cog on 2012-10-08
Hmm. Not as easy as it looks, I think.
I like the look of the first answer here:
[http://stackoverflow.com/questions/8219502/how-could-i-remove-newlines-from-all-quoted-pieces-of-text-in-a-file](http://stackoverflow.com/questions/8219502/how-could-i-remove-newlines-from-all-quoted-pieces-of-text-in-a-file)

---

### Post by The Cog on 2012-10-08
Hmm. Not as easy as it looks, I think.
I like the look of the first answer here:
[http://stackoverflow.com/questions/8219502/how-could-i-remove-newlines-from-all-quoted-pieces-of-text-in-a-file](http://stackoverflow.com/questions/8219502/how-could-i-remove-newlines-from-all-quoted-pieces-of-text-in-a-file)

---

### Post by Lars Noodén on 2012-10-08
> **rohit verma said:**
> Input ::
1212||sdfsdfsdf fgkdjfkgljlsdfg||sdfsdf
4454||"sadfsdfg
sdfgsdfg
sdf"||sdfgdfg
4454||ds gkdkjfhgskjfsdhkjg||sdfsdf


Output:::
1212||sdfsdfsdf fgkdjfkgljlsdfg||sdfsdf
4454||"sadfsdfg sdfgsdfg sdf"||sdfgdfg
4454||ds gkdkjfhgskjfsdhkjg||sdfsdf

It's still a guess at precisely what you are trying.  But if you want to print out the rows that have numbers in the first column, you can do it with [awk](http://manpages.ubuntu.com/manpages/precise/en/man1/awk.1posix.html)

```

awk -F '\|\|' '$1 ~ /[0-9]+/ {print $0}' < inputfile.txt

```

---

### Post by Vaphell on 2012-10-08
```
awk -F '\\|\\|' 'NF==3 { x=0; print $0 }
                 NF==1 { printf("%s ", $0); }
                 NF==2 { x++; if( x==2 ) printf("%s\n",$0); else printf("%s ",$0); }' file.txt
```
test

```
$ echo '1212||sdfsdfsdf fgkdjfkgljlsdfg||sdfsdf
4454||"sadfsdfg
sdfgsdfg
sdf"||sdfgdfg
4454||ds gkdkjfhgskjfsdhkjg||sdfsdf'  | awk -F '\\|\\|' 'NF==3 { x=0; print $0 } NF==1 { printf("%s ", $0); } NF==2 { x++; if( x==2 ) printf("%s\n",$0); else printf("%s ",$0); }'

1212||sdfsdfsdf fgkdjfkgljlsdfg||sdfsdf
4454||"sadfsdfg sdfgsdfg sdf"||sdfgdfg
4454||ds gkdkjfhgskjfsdhkjg||sdfsdf
```

---

