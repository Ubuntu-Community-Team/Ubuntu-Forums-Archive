---
title: "Find &amp; Replace !!!"
date: 2012-07-04
forum: General Help
---

### Post by Peterinall on 2012-07-04
Greeting everyone,

          I am working on a project where i edit old web pages to post them in out new site.
& for that i have to replace many phrases those have the same pattern but not identical. i.e.
```

</font><font color="#800000">&nbsp;<a name="1"></a>
</font><font color="#800000">&nbsp;<a name="2"></a>
</font><font color="#800000">&nbsp;<a name="3"></a>
</font><font color="#800000">&nbsp;<a name="4"></a>
So on.....

```I am using bluefish for the job & it also has a decent find & replace integrated but i have to change the numbers every time & i have more than few](*,) thousand pages. 

So i am wandering if there are any wildcard entries for bluefish or any other program that can do it for me in batch process.

Thanks in advance,
Peter.

---

### Post by SlugSlug on 2012-07-04
sed maybe able to help, what are you finding and replacing??

---

### Post by sudodus on 2012-07-04
You can edit the file in a plain text editor for example ***gedit***

select Search -- Replace
or use the hotkey ***ctrl +h***

or you can use the stream editor ***sed***

```
sed 's/original-pattern/new-pattern/' < original-file > edited-file

```

---

### Post by Peterinall on 2012-07-04
> **SlugSlug said:**
> sed maybe able to help, what are you finding and replacing??
I have given some examples of what i want to replce i.e.
</font><font color="#800000">&nbsp;<a name="1"></a> </font><font color="#800000">&nbsp;<a name="2"></a> </font><font color="#800000">&nbsp;<a name="3"></a> </font><font color="#800000">&nbsp;<a name="4"></a> So on..... with nothing.

the main problems are numbers which varies. from 1 to 50

---

### Post by SlugSlug on 2012-07-04
So you have

```
</font><font color="#800000">&nbsp;<a name="1"></a>
```

Now what do you want to replace it WITH?

---

### Post by Peterinall on 2012-07-04
> **sudodus said:**
> You can edit the file in a plain text editor for example ***gedit***

select Search -- Replace
or use the hotkey ***ctrl +h***

or you can use the stream editor ***sed***

```
sed 's/original-pattern/new-pattern/' < original-file > edited-file

```

Thank you for the quick reply,
I am really new to these thing, so what should be command look like if i want to replace all : </font><font color="#800000">&nbsp;<a name=[COLOR=Blue]"1"[/COLOR]></a>
[FONT=monospace]with different numbers from 1- 50.
```
sed 's/</font><font color="#800000">&nbsp;<a name="[COLOR=Blue]
[*][/COLOR]"></a>/ /' <original-file >edited-file
```

or sum thing else.

Regards.


[/FONT]

---

### Post by Peterinall on 2012-07-04
> **SlugSlug said:**
> So you have

```
</font><font color="#800000">&nbsp;<a name="[FONT=Arial Black][SIZE=3]1[/SIZE][/FONT]"></a>
```Now what do you want to replace it WITH?

Thank you for ur time & quick reply,
I have the pattern with different numbers 1-50. & wanna delete it or i can say replace with nothing.

---

### Post by SlugSlug on 2012-07-04
ahh ok so you want to delete the whole line?

so you could just search for 
```
</font><font color="#800000">&nbsp;<a nam
```and delete any line beginning with that ??


[COLOR=Red]**backup first!!**[/COLOR]

 ```
sed '/</font><font color="#800000">&nbsp;<a name/d'  FILE.html 
```(or *.html to do all html files in current dir)

---

### Post by Peterinall on 2012-07-04
> **SlugSlug said:**
> ahh ok so you want to delete the whole line?

so you could just search for 
```
</font><font color="#800000">&nbsp;<a nam
```and delete any line beginning with that ??


[COLOR=Red]**backup first!!**[/COLOR]

 ```
sed '/</font><font color="#800000">&nbsp;<a name/d'  FILE.html 
```(or *.html to do all html files in current dir)
Thank you very much,
So here is the result
```
ubuntu:~/Desktop$ sed '/</font><font color="#800000">&nbsp;<a name/d' *.htm
sed: -e expression #1, char 4: unknown command: `f'
```
Withou any change in file.

Regards

---

### Post by Peterinall on 2012-07-04
The whole lines look somthing like
```
**********0ff">&nbsp;Chorea.<br></font>[SIZE=3][COLOR=Red]<font color="#800000">&nbsp;<a name="2"></a>[/COLOR][/SIZE]&nbsp;&nbsp;</p>*********
```
& I only want to delete the colored part.
Regards

---

### Post by SlugSlug on 2012-07-04
> **Peterinall said:**
> Thank you very much,
So here is the result
```
ubuntu:~/Desktop$ sed '/</font><font color="#800000">&nbsp;<a name/d' *.htm
sed: -e expression #1, char 4: unknown command: `f'
```Withou any change in file.

Regards

ok try this one
sed '/"</font><font color="#800000">&nbsp;<a name"/d' *.htm
or this one
sed '/<\/font><font color="#800000">&nbsp;<a name/d' *.htm

---

### Post by Peterinall on 2012-07-04
I tried with a greater-than mark before input file & the error is
```
ubuntu:~/Desktop$ sed '/</font><font color="#800000">&nbsp;<a name/d' <*.htm
bash: *.htm: ambiguous redirect
```

Regards.

---

### Post by SlugSlug on 2012-07-04
> **Peterinall said:**
> The whole lines look somthing like
```
**********0ff">&nbsp;Chorea.<br></font>[SIZE=3][COLOR=Red]<font color="#800000">&nbsp;<a name="2"></a>[/COLOR][/SIZE]&nbsp;&nbsp;</p>*********
```& I only want to delete the colored part.
Regards


ahh ok no dont use that sed command as it will do whole line, you'll mostlikey need grep with -v



```
 grep -v "<font color="#800000">&nbsp;<a name="[0-50]"></a>" old.html > new.html

```

---

### Post by Peterinall on 2012-07-04
> or this one
sed '/<\/font><font color="#800000">&nbsp;<a name/d' *.htm

This one dose somthing with showing all my file texts in terminal but the input files are as before. 

Thanks & regards,
Peter

---

### Post by SlugSlug on 2012-07-04
> **Peterinall said:**
> This one dose somthing with showing all my file texts in terminal but the input files are as before. 

Thanks & regards,
Peter


Dont use that sed command as it will delete whole line, try that grep but am unsure on the wildcard [1-50]  just googleing now

---

### Post by zero2xiii on 2012-07-04
Hay,

Just redirect the output:

```
sed '/<\/font><font color="#800000">&nbsp;<a name/d' *.htm >*.new.htm
```

If used in a script you can use a variable to save to the same name of the original file with a prefix for example:

$name --> new_$name

Cherz

EDIT: This will delete the whole line. As pointed out by some folks. Try:

```
sed 's_</font><font color="#800000">&nbsp;<a name__g' *.htm >*.new.htm
```
with / as breaks
```
sed 's/<\/font><font color="#800000">&nbsp;<a name//g' *.htm >*.new.htm
```

Something that works for me:
```
echo '<font color="#800000">&nbsp;<a name="5"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9]"></a>'_nothing_g
echo '<font color="#800000">&nbsp;<a name="25"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>'_nothing_g
```

The first line works for all values of **name="5"** up to 9, and then the second line works for all values of name="25" up to 99
and replaces that line with the word "nothing"

---

### Post by Peterinall on 2012-07-04
> **SlugSlug said:**
> Dont use that sed command as it will delete whole line, try that grep but am unsure on the wildcard [1-50]  just googleing now
Thanks for ur time & kindness dear,

I have earlier searched for some tools & came to know about "kfilereplace" but the problem never ends with those different numbers.

Thanks & regards.

---

### Post by SlugSlug on 2012-07-04
did that grep fail?

try adding some quotes or backticks  around the [1-50]

eg
"[1-50]"
`[1-50]`

---

### Post by Peterinall on 2012-07-04
> **zero2xiii said:**
> Hay,

Just redirect the output:

```
sed '/<\/font><font color="#800000">&nbsp;<a name/d' *.htm >*.new.htm
```If used in a script you can use a variable to save to the same name of the original file with a prefix for example:

$name --> new_$name

Cherz

EDIT: This will delete the whole line. As pointed out by some folks. Try:

```
sed 's_</font><font color="#800000">&nbsp;<a name__g' *.htm >*.new.htm
```with / as breaks
```
sed 's/<\/font><font color="#800000">&nbsp;<a name//g' *.htm >*.new.htm
```Something that works for me:
```
echo '<font color="#800000">&nbsp;<a name="5"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9]"></a>'_nothing_g
echo '<font color="#800000">&nbsp;<a name="25"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>'_nothing_g
```The first line works for all values of **name="5"** up to 9, and then the second line works for all values of name="25" up to 99
and replaces that line with the word "nothing"

Thank you for the reply,
  The last two commands do delete the line mentioned but still leaving the final & important part i.e. "[FONT=monospace]="2"></a>"[/FONT] & also not working in all lines.

Regards.

---

### Post by Peterinall on 2012-07-04
> **SlugSlug said:**
> did that grep fail?

try adding some quotes or backticks  around the [1-50]

eg
"[1-50]"
`[1-50]`

I tried ```
ubuntu:~/Desktop$ grep -v "<font color="#800000">&nbsp;<a name="[0-50]"></a>" *.htm > new.htm
ubuntu:~/Desktop$ grep -v "<font color="#800000">&nbsp;<a name="[0-50]*"></a>" *.htm > new.htm
ubuntu:~/Desktop$ grep -v "<font color="#800000">&nbsp;<a name="'[0-50]'"></a>" *.htm > new.htm
```Without any success .

Even a specific ```
ubuntu:~/Desktop$ grep -v "<font color="#800000">&nbsp;<a name="2"></a>" *.htm > new.htm
``` is of no help.
Regards.

---

### Post by steeldriver on 2012-07-04
'sed' is a bit tricky with html because of all the characters that look 'special' - it helps to use different separators (rather than the usual forward slashes) so you don't need to escape those

If you want to replace the "1" with another number (I'm still not clear this is what you want to do - first rule of sed - DEFINE YOUR REQUIREMENT) then you can use the (...) syntax to group the line into sub-expression and then just replace the <a name ="1"> using a regex "[0-9]+" (meaning "one or more consecutive digits") with another number (I used <a name="50"> below) then:

```
sed -r 's|(</font><font color="#800000">&nbsp;)(<a name="[0-9]+">)(</a>)|\1<a name="50">\3|' *yourfile* > *newfile*
```or if you are old school and don't want to / can't use 'sed -r' then you need to escape the (, ), and + characters

```
sed sed 's|\(</font><font color="#800000">&nbsp;\)\(<a name="[0-9]\+">\)\(</a>\)|\1<a name="50">\3|' *yourfile* > *newfile*
```There are other tools that are easier for working with html - someone posted a few in a recent similar thread so have a search

---

### Post by Peterinall on 2012-07-04
> **zero2xiii said:**
> Hay,

Something that works for me:
```
echo '<font color="#800000">&nbsp;<a name="5"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9]"></a>'_nothing_g
echo '<font color="#800000">&nbsp;<a name="25"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>'_nothing_g
```The first line works for all values of **name="5"** up to 9, and then the second line works for all values of name="25" up to 99
and replaces that line with the word "nothing"
**[COLOR=Red]Thisone is doing the trick. how do i just delete it not replace with any thing.[/COLOR]**

Regards.

---

### Post by Peterinall on 2012-07-04
> **steeldriver said:**
> 'sed' is a bit tricky with html because of all the characters that look 'special' - it helps to use different separators (rather than the usual forward slashes) so you don't need to escape those

If you want to replace the "1" with another number (I'm still not clear this is what you want to do - first rule of sed - DEFINE YOUR REQUIREMENT) then you can use the (...) syntax to group the line into sub-expression and then just replace the <a name ="1"> using a regex "[0-9]+" (meaning "one or more consecutive digits") with another number (I used <a name="50"> below) then:

```
sed -r 's|(</font><font color="#800000">&nbsp;)(<a name="[0-9]+">)(</a>)|\1<a name="50">\3|' *yourfile* > *newfile*
```or if you are old school and don't want to / can't use 'sed -r' then you need to escape the (, ), and + characters

```
sed sed 's|\(</font><font color="#800000">&nbsp;\)\(<a name="[0-9]\+">\)\(</a>\)|\1<a name="50">\3|' *yourfile* > *newfile*
```There are other tools that are easier for working with html - someone posted a few in a recent similar thread so have a search

I JUST WANT TO DELETE"<font color="#800000">&nbsp;<a name="[SIZE=4][COLOR=Red][0-50][/COLOR][/SIZE]"></a>"  [0-50]  WHERE EACH HAVE A NO BETWEEN 0 TO 50

REGARDS.

---

### Post by mainmeister on 2012-07-04
I am not familiar with the bluefish editor but, does it support grep type search and replace (as an option?). Otherwise you could use an external command like sed to process a grep like search and replace on a group of files.

---

### Post by Peterinall on 2012-07-04
> **mainmeister said:**
> I am not familiar with the bluefish editor but, does it support grep type search and replace (as an option?). Otherwise you could use an external command like sed to process a grep like search and replace on a group of files.
Though i am using ubuntu from 11.04 but not familier with it's advance & powerful commands.

---

### Post by Peterinall on 2012-07-04
> **zero2xiii said:**
> Hay,

Something that works for me:
```
echo '<font color="#800000">&nbsp;<a name="5"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9]"></a>'_nothing_g
echo '<font color="#800000">&nbsp;<a name="25"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>'_nothing_g
```The first line works for all values of **name="5"** up to 9, and then the second line works for all values of name="25" up to 99
and replaces that line with the word "nothing"
  **_[COLOR=Red]This does the trick[/COLOR]_** but i just want to delete the line not replace it with "nothing".
So how can i do so ?

Regards.

---

### Post by Peterinall on 2012-07-04
Thank you folks, Great helping hands here !!!
[SIZE=4][COLOR=Red]SOLVED[/COLOR][/SIZE]

```
echo '<font color="#800000">&nbsp;<a name="5"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9]"></a>'_' '_g
 echo '<font color="#800000">&nbsp;<a name="25"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>'_' '_g
``` This does the trick.

Any more help or a bash script will be of much help & greatly appreciated .

Have a nice day guys,
Peter.

---

### Post by zero2xiii on 2012-07-04
Hay,

Haha sorry. Just remove the word 'nothing' lolz and keep the two underscores right next to each other:

```
echo '<font color="#800000">&nbsp;<a name="5"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9]"></a>__g'
 echo '<font color="#800000">&nbsp;<a name="25"></a>' | sed s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>__g'
```

As far as a batch script goes:

```

#!/bin/sh

for file in **./*.html**
	do echo $file
	sed -e 's_<font color="#800000">&nbsp;<a name="[0-9]"></a>'__g -e s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>__g' "$file" >"$file"_new
	done

exit

```

This does exactly what you want. Run it IN the directory containing the files. This will duplicate the files, and the edited files will be apended with _new. Also note this looks for *.html file. edit the bold line to contain the correct extention for your files.

Cherz

---

### Post by Peterinall on 2012-07-05
hahahaha.... that's a newbi's crooked output hahaha.....
Thank you zero2xiii for ur time & excellent help.
 By the way still there is a bit confusion . I tried to apply ur command to remove 
```
[1-50] [<a href="#top">som text</a>]
```
Where [0-50] again are the same pattern 1 to 50 with out any success but the output file is just a messed upo file with out any related content with input file, why ?

& how the script would look like which execute both commands with a single out put ?

Thanks again for ur kind help,
Have a nice time,
Regards,
Peter.

---

### Post by Vaphell on 2012-07-05
regular expressions don't understand numbers, all they see is characters
[1-50] is not numbers from 1 to 50 but a character from the set 1,2,3,4,5,0 (1-5, 0)

1- or 2-digit number would be [0-9]?[0-9] or [0-9]{1,2}

```
$ echo $'abc=12\ndef=2'
abc=12
def=2
$ echo $'abc=12\ndef=2' | sed -r 's_[0-9]?[0-9]_X_'
abc=X
def=X
$ echo $'abc=12\ndef=2' | sed -r 's_[0-9]{1,2}_X_'
abc=X
def=X
```

---

### Post by zero2xiii on 2012-07-05
> **Peterinall said:**
> hahahaha.... that's a newbi's crooked output hahaha.....
Thank you zero2xiii for ur time & excellent help.
 By the way still there is a bit confusion . I tried to apply ur command to remove 
```
[1-50] [<a href="#top">som text</a>]
```
Where [0-50] again are the same pattern 1 to 50 with out any success but the output file is just a messed upo file with out any related content with input file, why ?

& how the script would look like which execute both commands with a single out put ?

Thanks again for ur kind help,
Have a nice time,
Regards,
Peter.


Hay,

Can you please give a few lines of example input, and then the desired output. +1 for Vaphell. That is why I used two seperate sed statements. I forgot about the ? thing. I remember it is something to do with wildcards, but only on a specific place and only one character per ?... If I remember correctly (damn, haven't used it in some time)

Also what do you mean with:
> By the way still there is a bit confusion . I tried to apply ur command to remove 
```
[1-50] [<a href="#top">som text</a>]
```
Where [0-50] again are the same pattern 1 to 50 with out any success but the output file is just a messed upo file with out any related content with input file, why ?

Can you please elaborate more on precisely what you did, tried? That script works perfectly for me with generated input. Oh maybe you are copy/pasting it to terminal. You need to create a file (say edit.sh) and copy that code in it. Then go to terminal and make the file executable (chmod +x ./edit.sh) and then run it with ./edit.sh ... Thats how one uses a script.

Cherz

---

### Post by Vaphell on 2012-07-05
> I remember it is something to do with wildcards, but only on a specific place and only one character per ?... If I remember correctly (damn, haven't used it in some time)

in regular expressions ? (0-1), + (1-) and * (0-) can be used with char groups too, not only with ordinary chars (a? = optional 'a') and chars from given sets ( [abc]? = optional 'a' or 'b' or 'c' )
 
```
$ echo $'abcdefghi\nabc'
abcdefghi
abc
$ echo $'abcdefghi\nabc' | sed -r 's/abc**(def)?**/X/'  # abc with optional def
Xghi
X
$ echo $'abcdefghi\nabc' | sed -r 's/**([a-z]{4})+**/X/'  # multiples of 4 letters (1 or more 4-letter combos)
Xi
abc
```

---

### Post by Peterinall on 2012-07-05
> **zero2xiii said:**
> Hay,

Can you please give a few lines of example input, and then the desired output. +1 for Vaphell. That is why I used two seperate sed statements. I forgot about the ? thing. I remember it is something to do with wildcards, but only on a specific place and only one character per ?... If I remember correctly (damn, haven't used it in some time)

Also what do you mean with:


Can you please elaborate more on precisely what you did, tried? That script works perfectly for me with generated input. Oh maybe you are copy/pasting it to terminal. You need to create a file (say edit.sh) and copy that code in it. Then go to terminal and make the file executable (chmod +x ./edit.sh) and then run it with ./edit.sh ... Thats how one uses a script.

Cherz

Sorry for delay in replying 

Here is a full sentence  where colored parts have to be removed the blue ones were removed by ur previous bash script but with the same command only replacing what i want to delete in red below did not work(I am giving this example coz it was the shortest one :)
```
[COLOR=Red] [22] [<a href="#top">crtc</a>][/COLOR]<br></font></b>Increased sexual desire.<br>Stitches in right testicle and spermatic cord.<br>Stitches in testicles while sitting.<br><b><font color="#0000ff">Gleet&nbsp;; burning&nbsp;; green discharge.<br>Red itching eruption on glans *****.<br></font>[COLOR=Blue]<font color="#800000">&nbsp;<a name="23"></a>[/COLOR]&nbsp;&nbsp;</p>
```Thank you very very much,
Regards.

---

### Post by Peterinall on 2012-07-05
> **Vaphell said:**
> in regular expressions ? (0-1), + (1-) and * (0-) can be used with char groups too, not only with ordinary chars (a? = optional 'a') and chars from given sets ( [abc]? = optional 'a' or 'b' or 'c' )
 
```
$ echo $'abcdefghi\nabc'
abcdefghi
abc
$ echo $'abcdefghi\nabc' | sed -r 's/abc**(def)?**/X/'  # abc with optional def
Xghi
X
$ echo $'abcdefghi\nabc' | sed -r 's/**([a-z]{4})+**/X/'  # multiples of 4 letters (1 or more 4-letter combos)
Xi
abc
```

I am just looking at these things like i look at aeroplanes going over my head they are so high above my head.:( I wish i could get all these things. linux is awesome .

Regards

---

### Post by zero2xiii on 2012-07-05
Hay,

The square brackets in the statement is what is giving the issue, so we escape them using the backslash \. This means we tell bash to ignore the character following the backslash.

so this works again:
```
echo '[8] [<a href="#top">crtc</a>]' | sed s_'\[[1-9]\]\ \[<a href="#top">crtc</a>\]'_nothing_g
nothing
echo '[22] [<a href="#top">crtc</a>]' | sed s_'\[[1-9][1-9]\]\ \[<a href="#top">crtc</a>\]'_nothing_g
nothing

```

To use it in the script I gave you earlier, just add this to after the last sed statement:

```
-e 's_\[[1-9]\]\ \[<a href="#top">crtc</a>\]__g' -e 's_\[[1-9][1-9]\]\ \[<a href="#top">crtc</a>\]__g'
```

Just look at the script how the other two lines are combined to form only one sed command and add that line after the second statement.

Cherz

---

### Post by zero2xiii on 2012-07-05
Just for clarity:

```
#!/bin/sh

for file in ./*.html
	do echo $file
	sed -e 's_<font color="#800000">&nbsp;<a name="[0-9]"></a>'__g -e s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>__g' "$file" >"$file"_new
	done

exit
```

Becomes:

```
#!/bin/sh

for file in ./*.html
	do echo $file
	sed -e 's_<font color="#800000">&nbsp;<a name="[0-9]"></a>'__g -e s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>__g' -e 's_\[[1-9]\]\ \[<a href="#top">crtc</a>\]__g' -e 's_\[[1-9][1-9]\]\ \[<a href="#top">crtc</a>\]__g' "$file" >"$file"_new
	done

exit
```

You can do it with four sed statements, but then you would have to create 4 new files, with the forth file being the last, fully changed document. It causes unnecessary disk writing and adds time to the process not needed (especially if you are working with a few hundred or thousand files)

Cherz

Just to explain what happens, as I see you actualy tried to use some initiative:


In sed you can spesify a range for a value using square brackets.
So [1-5] will match, 1, 2, 3, 4 or 5
However it is NOT a numeral range so [5-10] will NOT match 5, 6, 7, 8, 9, **10**.. It will Match 0, 1, 5, 6, 7, 8, 9.
Typing [12345] and [1-5] is synonymous. 

In the given statement there are already square brackets:
[25] so we need to tell sed to KEEP the brackets, and give it a patern range, so we escape the last set of square brackets:
\[[1-5]\]. This tells sed to match [1], [2], [3], [4], [5].

To match dubble digtits, like 10, 12, 55 etc, we need to give 2 ranges (one for each number):
So [1-2][1-2] will match: 11, 12, 21, 22.

To understand that, play with echo and a range {1..9} in terminal and see how it works:

```
echo {1..9}
echo {1..9}{1..9}
```

You will note however you can simply say
```
echo {11..99}
```
To have the same result as the second echo in the first example. But the value range in sed does not follow the same behaviour. If it is possible to have a range in sed similar to {1..99}, then I am unaware of HOW to do it.

Hope this clears things up a bit ;)

Cherz

---

### Post by Vaphell on 2012-07-05
> 
```
echo {1..9}{1..9}
```
You will note however you can simply say
```
echo {1..99}
```
To have the same result as the second echo in the first example.
not really :)
{1..9}{1..9} produces all combinations of [1-9][1-9] while 1..99 gives all numbers in 1-99 range.

```
$ echo {1..9}{1..9}
11 12 13 14 15 16 17 18 19 21 22 23 24 25 26 27 28 29 31 32 33 34 35 36 37 38 39 41 42 43 44 45 46 47 48 49 51 52 53 54 55 56 57 58 59 61 62 63 64 65 66 67 68 69 71 72 73 74 75 76 77 78 79 81 82 83 84 85 86 87 88 89 91 92 93 94 95 96 97 98 99
$ echo {1..99}
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99
```

if you said {0..9}{0..9} and {00..99} then yes, they would be more or less equivalent ;-) (bash ranges support padding with 0s to produce fixed width output)

range can be achieved using alternative 
1-50 -> ([1-9]|[1-4][0-9]|50) = [1-9] or [1-4][0-9] or 50
0-50 including 0X -> ([0-4]?[0-9]|50)

---

### Post by zero2xiii on 2012-07-05
> **Vaphell said:**
> not really :)
{1..9}{1..9} produces all combinations of [1-9][1-9] while 1..99 gives all numbers in 1-99 range.

if you said {0..9}{0..9} and {00..99} then yes, they would be equivalent ;-) (bash ranges support padding with 0s to produce fixed width output)



Haha yea sorry, had a Typo there, meant to type 11..99 not 1..99 cause 00..99 will also include 00, 01, 02, 03 and so forth. Unless you said {0..9}{0..9}, but still a typo on my side hahahaha.... 

Also, I lost the part on the range you gave?:

> range can be achieved using alternative 
1-50 -> ([1-9]|[1-4][0-9]|50) = [1-9] or [1-4][0-9] or 50
0-50 including 0X -> ([0-4]?[0-9]|50)

Does this work inside SED parameters? Cause I know the use of the above, but does it work in sed? That could make 4 arguments into 2 in the above script.

Cherz

---

### Post by Vaphell on 2012-07-05
> Haha yea sorry, had a Typo there, meant to type 11..99 not 1..99 cause 00..99 will also include 00, 01, 02, 03 and so forth. Unless you said {0..9}{0..9}, but still a typo on my side hahahaha....
again, not really ;-)
11..99 is normal number range of 11-99 and will include 20, which is not the case with {1..9}{1..9}

> Does this work inside SED parameters?

Sure
```
$ echo \"{0..99}\" | sed -r 's/"([1-9]|[1-4][0-9]|50)"/(\1)/g'
"0" (1) (2) (3) (4) (5) (6) (7) (8) (9)
(10) (11) (12) (13) (14) (15) (16) (17) (18) (19)
(20) (21) (22) (23) (24) (25) (26) (27) (28) (29)
(30) (31) (32) (33) (34) (35) (36) (37) (38) (39)
(40) (41) (42) (43) (44) (45) (46) (47) (48) (49)
(50) "51" "52" "53" "54" "55" "56" "57" "58" "59"
"60" "61" "62" "63" "64" "65" "66" "67" "68" "69"
"70" "71" "72" "73" "74" "75" "76" "77" "78" "79"
"80" "81" "82" "83" "84" "85" "86" "87" "88" "89"
"90" "91" "92" "93" "94" "95" "96" "97" "98" "99"
```

---

### Post by Peterinall on 2012-07-06
> **zero2xiii said:**
> Just for clarity:

```
#!/bin/sh

for file in ./*.html
    do echo $file
    sed -e 's_<font color="#800000">&nbsp;<a name="[0-9]"></a>'__g -e s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>__g' "$file" >"$file"_new
    done

exit
```Becomes:

```
#!/bin/sh

for file in ./*.html
    do echo $file
    sed -e 's_<font color="#800000">&nbsp;<a name="[0-9]"></a>'__g -e s_'<font color="#800000">&nbsp;<a name="[0-9][0-9]"></a>__g' -e 's_\[[1-9]\]\ \[<a href="#top">crtc</a>\]__g' -e 's_\[[1-9][1-9]\]\ \[<a href="#top">crtc</a>\]__g' "$file" >"$file"_new
    done

exit
```

Hello great folks,
Sorry for such unwanted delay but work work work...

Thanks Zero 2xii for ur help but the later script does not seem to removing the second one ```
e 's_\[[1-9]\]\ \[<a href="#top">crtc</a>\]__g' -e  's_\[[1-9][1-9]\]\ \[<a href="#top">crtc</a>\]__g' "$file"  >"$file"_new
```

i am really glad to realize that ubuntu community guys r so awesome.

Regards
Peter.

---

### Post by dargaud on 2012-07-06
For replacing things in multiple files I usually prefer perl as it is MUCH faster than looping on sed (and also it maintains the permissions).

Here are two examples:```
perl -pi -w -e 's/^Vertical.*\n//;' *.dat
``` will remove all the lines starting with 'Vertical' in all the dat files. ```
perl -pi -w -e 's/Ã/A/g;' *
``` will replace a character by another in all the files.

Be aware that replacement happens IN the files so make a backup of your files before as if you screw up your regex, you are screwed.

---

### Post by Vaphell on 2012-07-06
try this sed:
```
sed -r 's_[COLOR="Blue"]<font color="#800000">&nbsp;<a name="([1-9]|[1-4][0-9]|50)"></a>[/COLOR]|[COLOR="DarkGreen"]\[([1-9]|[1-4][0-9]|50)\] \[<a href="#top">crtc</a>\][/COLOR]__g'
```

it's only 1 expression with patterns for numbers 1-50, not a chain of -e '...' -e '...'
it should work, i tested it on
```
$ echo $'1<font color="#800000">&nbsp;<a name="3"></a>1\n2<font color="#800000">&nbsp;<a name="33"></a>2\n3[3] [<a href="#top">crtc</a>]3\n4[33] [<a href="#top">crtc</a>]4'
1<font color="#800000">&nbsp;<a name="3"></a>1
2<font color="#800000">&nbsp;<a name="33"></a>2
3[3] [<a href="#top">crtc</a>]3
4[33] [<a href="#top">crtc</a>]4

$ echo $'1<font color="#800000">&nbsp;<a name="3"></a>1\n2<font color="#800000">&nbsp;<a name="33"></a>2\n3[3] [<a href="#top">crtc</a>]3\n4[33] [<a href="#top">crtc</a>]4' | sed -r 's_<font color="#800000">&nbsp;<a name="([1-9]|[1-4][0-9]|50)"></a>|\[([1-9]|[1-4][0-9]|50)\] \[<a href="#top">crtc</a>\]__g'
11
22
33
44

```
btw, is that 'crtc' a fixed string or are other combinations possible? if so, then 'crtc' in sed pattern should be replaced by let's say **[a-z]+** (if it's one or more lowercase letters, etc).


while perl is generally more powerful, i don't see much difference here - expressions would be almost identical and sed can work with files in place too (sed -i ... *.txt). Looping and output redirection make sure that original data won't get destroyed by some unfortunate accident.

---

### Post by Peterinall on 2012-07-06
> **Vaphell said:**
> try this sed:
```
sed -r 's_[COLOR=Blue]<font color="#800000">&nbsp;<a name="([1-9]|[1-4][0-9]|50)"></a>[/COLOR]|[COLOR=DarkGreen]\[([1-9]|[1-4][0-9]|50)\] \[<a href="#top">crtc</a>\][/COLOR]__g'
```

[SIZE=3][COLOR=DarkRed]it worked like a charm.[/COLOR][/SIZE]


> **Vaphell said:**
> 
btw, is that 'crtc' a fixed string or are other combinations possible?  if so, then 'crtc' in sed pattern should be replaced by let's say **[a-z]+** (if it's one or more lowercase letters, etc).

Indeed ! as i was testing on single file in a new directory, i have totally forgotten abt it. That part contain both capital & small letter as well as dot"." and space too. like "Crot. che." thank you for raising the matter, how could i address that ?

Regards,
Peter.

---

### Post by Vaphell on 2012-07-06
replace crtc with ```
[A-Za-z. ]+
```

---

### Post by Peterinall on 2012-07-07
> **Vaphell said:**
> replace crtc with ```
[A-Za-z. ]+
```

Thanks Vaphell, It is doing miracles for me.:guitar:\\:D/
You guys just save my hundreds of hours. & all-hail "LINUX" :)

I would like to know more about this "sed" command, Can any one plz redirect me to a tutorial made for newbies like me. I have found som in google but they r too advanced according to me.

Again very very thank you to all ubuntu community., Have a great time
Love & regards,
Peter.

---

### Post by zero2xiii on 2012-07-07
> **Peterinall said:**
> 

I would like to know more about this "sed" command, Can any one plz redirect me to a tutorial made for newbies like me. I have found som in google but they r too advanced according to me.


Sed is very mysterious hahaha. There are no "Easy" tutorial matter availible.

The Nature of sed makes it very confusing. And the syntax does not exactly help...

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
This is one of my personal opinion best starting points and general reference.

[http://www.ceri.memphis.edu/computer/docs/unix/sed.htm](http://www.ceri.memphis.edu/computer/docs/unix/sed.htm)
This one is somewhat more syntax orientated (such as HOW to form the sed arguments), but also a good read for starting out.

[http://www.sedtutorial.com/](http://www.sedtutorial.com/)
This is very comprehensive and follows a "How To" style. I find it somewhat to complicated for anyone new to linux and redirecting output and piping and that kind of stuff, but it is VERY good material and covers a decent spectrum. 

[http://www.panix.com/~elflord/unix/sed.html](http://www.panix.com/~elflord/unix/sed.html)
Is very introductory, and it gives a somewhat better overview of regular expressions and ranges inside sed.

Good luck with the journey :)
Cherz

---

