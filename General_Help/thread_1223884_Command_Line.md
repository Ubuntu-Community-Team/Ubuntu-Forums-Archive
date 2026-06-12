---
title: "Command Line"
date: 2009-07-26
forum: General Help
---

### Post by GreenDance on 2009-07-26
Hi, I'm creating a script, my first to be exact :D, is it possible to get the script to open a file, find a line and replace it with something else?

for example, on line 7 of a file says "lets have fun", i would like my script to open the text file, find "lets have fun" and replace it with "party time", I would also like to do this for other lines as well, is this possible?

many thanks

---

### Post by SKeaLoT on 2009-07-26
this should help
[Link]("http://www.linuxquestions.org/questions/programming-9/bash-replace-a-line-in-text-file-631208/")

---

### Post by GreenDance on 2009-07-27
Hi, I've got this in my script

 sed '3s/.*/This text here will replace whatever is on line 3/' test.doc

But it does not work :(, any ideas?
thank you

---

### Post by TuckLive on 2009-07-27
This [[COLOR="Blue"]link[/COLOR]]("http://www.grymoire.com/Unix/Sed.html#uh-8") was inside the link SKeaLoT gave you.  It looks like you need to do 

```
sed '3s/.*/This text here will replace whatever is on line 3/' <oldtest.doc>newtest.doc
```

---

### Post by GreenDance on 2009-07-27
> **TuckLive said:**
> This [[COLOR="Blue"]link[/COLOR]]("http://www.grymoire.com/Unix/Sed.html#uh-8") was inside the link SKeaLoT gave you.  It looks like you need to do 

```
sed '3s/.*/This text here will replace whatever is on line 3/' <oldtest.doc>newtest.doc
```

Hi, I've tried that but it emptys the file :(

---

### Post by nikhilk on 2009-07-27
> **GreenDance said:**
> Hi, I've got this in my script

 sed '3s/.*/This text here will replace whatever is on line 3/' test.doc

But it does not work :(, any ideas?
thank you

Have you just named the plain text file .doc or is it actually a MS Word document. I ask because Word documents are binary files and sed/awk are text utilities and are not intended to be used on binary data.

---

### Post by GreenDance on 2009-07-27
> **nikhilk said:**
> Have you just named the plain text file .doc or is it actually a MS Word document. I ask because Word documents are binary files and sed/awk are text utilities and are not intended to be used on binary data.

hi, sorry it's a .ini file i meant.

the sed command still doesn't work :(, it just emptys the file.

---

### Post by GreenDance on 2009-07-27
I've been searching around google and nothing has turned up :(

---

### Post by nikhilk on 2009-07-27
> **GreenDance said:**
> hi, sorry it's a .ini file i meant.

the sed command still doesn't work :(, it just emptys the file.

If you want to replace "lets have fun" at the start of a line with "party time" use
```
sed 's/^lets have fun/party time/' test.doc
```
If you want to replace "lets have fun" anywhere in a file with "party time" use
```
sed 's/lets have fun/party time/' test.doc
```

Note that the actual contents of the file are NOT changed by the above commands. The result is just displayed on the terminal. You can redirect it to a file once you are sure that the output is correct.

---

### Post by GreenDance on 2009-07-27
> **nikhilk said:**
> If you want to replace "lets have fun" at the start of a line with "party time" use
```
sed 's/^lets have fun/party time/' test.doc
```
If you want to replace "lets have fun" anywhere in a file with "party time" use
```
sed 's/lets have fun/party time/' test.doc
```

Note that the actual contents of the file are NOT changed by the above commands. The result is just displayed on the terminal. You can redirect it to a file once you are sure that the output is correct.

Hi, how do i get it to write to the file please :)

---

### Post by nikhilk on 2009-07-27
> **GreenDance said:**
> Hi, how do i get it to write to the file please :)

You can redirect the output to a file like this
```
sed 's/lets have fun/party time/' test.doc > newtest.doc
```
The file newtest.doc will contain the new,replaced content.

---

### Post by GreenDance on 2009-07-27
> **nikhilk said:**
> You can redirect the output to a file like this
```
sed 's/lets have fun/party time/' test.doc > newtest.doc
```
The file newtest.doc will contain the new,replaced content.

Thank You, 1 more question please, can I replace the file instead of creating a new file, thank you

---

### Post by nikhilk on 2009-07-27
> **GreenDance said:**
> Thank You, 1 more question please, can I replace the file instead of creating a new file, thank you

A simple solution is to rename the file and then redirect to a file with the desired name.
For simple one file editing this will suffice
```
mv test.doc test.doc.old
sed 's/lets have fun/party time/' test.doc.old > test.doc
rm -f test.doc.old
```
For batch editing of multiple files something more elaborate will be required.

---

### Post by GreenDance on 2009-07-27
> **nikhilk said:**
> A simple solution is to rename the file and then redirect to a file with the desired name.
For simple one file editing this will suffice
```
mv test.doc test.doc.old
sed 's/lets have fun/party time/' test.doc.old > test.doc
rm -f test.doc.old
```
For batch editing of multiple files something more elaborate will be required.

Hi, works great, thank you,

1 more question, sorry this is really the last question as i forgot to ask...

to edit more than 1 line, is this right?

do i continue the edits on the same line, for example 's/lets have fun/party time/' 's/one day/party time/' 's/all together/party time/'

many thanks for your help :)

---

### Post by theozzlives on 2009-07-27
I may be out of line but it seems easier to just edit the file as opposed to going through the trouble of writing a script.

---

### Post by nikhilk on 2009-07-27
> **GreenDance said:**
> Hi, works great, thank you,

1 more question, sorry this is really the last question as i forgot to ask...

to edit more than 1 line, is this right?

do i continue the edits on the same line, for example 's/lets have fun/party time/' 's/one day/party time/' 's/all together/party time/'

many thanks for your help :)

You can add multiple substitution commands to a file and tell sed to execute all of them. e.g If want to replace all occurrences of "abc" with "lmn" and "pqr" with "xyz" then put the substitution commands one on each line in a file say "sub"
```
s/abc/lmn/
s/pqr/xyz/
```
Then tell sed to use this file with
```
sed -f sub test.doc.old > test.doc
```
You are welcome :)

---

### Post by Arand on 2009-07-27
If you do want to contain all edits in one line use the -e (or --experssion=, does not matter which) flag before each expression, like so:```
 sed -e 's/lets have fun/party time/' --expression='s/one day/party time/' -e 's/all together/party time/' test.txt
```

---

### Post by GreenDance on 2009-07-27
> **Arand said:**
> If you do want to contain all edits in one line use the -e (or --experssion=, does not matter which) flag before each expression, like so:```
 sed -e 's/lets have fun/party time/' --expression='s/one day/party time/' -e 's/all together/party time/' test.txt
```

Hi, that works great but how can i do that on separate lines please

---

### Post by gastly on 2009-07-27
You want the command in seperate lines? Like this?
```

sed -e 's/lets have fun/party time/' \
--expression='s/one day/party time/' \
-e 's/all together/party time/' test.txt

```

---

### Post by GreenDance on 2009-07-27
> **gastly said:**
> You want the command in seperate lines? Like this?
```

sed -e 's/lets have fun/party time/' \
--expression='s/one day/party time/' \
-e 's/all together/party time/' test.txt

```

Brilliant, Thanks Very Much :)

---

### Post by paul.maddox on 2009-07-27
You want the -i flag for sed for inline replacements...

eg:

sed -i 's/paul/dave/g' /etc/passwd

Would change *all* occurences (the /g makes it match all) of 'paul' to 'dave' in the /etc/passwd file.

---

### Post by m4tic on 2009-07-27
I hope we're not raising maicious programmers here

---

### Post by GreenDance on 2009-07-27
Hi, I'm getting Permission Denied on a file I'm trying to **mv** :(, what can I do to fix this, thank you! :)

---

### Post by benj1 on 2009-07-27
> **GreenDance said:**
> Hi, I'm getting Permission Denied on a file I'm trying to **mv** :(, what can I do to fix this, thank you! :)

sudo


if youre wanting to learn bash scripting read this
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

also 
> man *command*
for details of how to use a command

---

### Post by GreenDance on 2009-07-27
I've fixed my problem...

but now I have a new problem :(

inside of the '/word here/' i need to include a / but that breaks the script, does anyone know how i can fix this please? thank you :)

---

### Post by Arand on 2009-07-27
```
\/
```use \ before any special character to treat it as just a "normal" character.

---

### Post by decoherence on 2009-07-27
> **GreenDance said:**
> I've fixed my problem...

but now I have a new problem :(

inside of the '/word here/' i need to include a / but that breaks the script, does anyone know how i can fix this please? thank you :)

You can use any character you like as a delimiter, as long as it is consistent and doesn't appear in the pattern (or you escape it, as above)

sed 's/bingo/bango/g'

is the same as

sed 's!bingo!bango!g'

or

sed 's+bingo+bango+g'

---

### Post by benj1 on 2009-07-28
> **decoherence said:**
> You can use any character you like as a delimiter, as long as it is consistent and doesn't appear in the pattern (or you escape it, as above)

sed 's/bingo/bango/g'

is the same as

sed 's!bingo!bango!g'

or

sed 's+bingo+bango+g'

thats funky
you learn something new every day

---

