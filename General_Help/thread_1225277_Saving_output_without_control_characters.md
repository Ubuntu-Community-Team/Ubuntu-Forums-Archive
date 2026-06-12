---
title: "Saving output without control characters"
date: 2009-07-28
forum: General Help
---

### Post by damianpfister on 2009-07-28
I have a text log file which has a copy of everything typed on the console. When I cat this file it will show me the likes of:

[COLOR=Red]server1:>ls
server1:>who
server1:>top[/COLOR]

...and so on.

Now if I either cat -v or simply vi this file I get the following:

[COLOR=Red]server1:>ll^Hs^M
server1:>which^H^H^H^H^Hwho^M
server1:>tap^H^Hop^M[/COLOR]

Now it is obvious that the ^H is the control character for BACKSPACE and ^M for RETURN - both of which are actually translated by cat so that the final command executed is shown and not all the errors (plus backspaces/enters).

It is easy enough to get rid of the ^M through sed or tr, but how do you get around all those ^H characters?

If I type in:

[COLOR=Red]server1:>grep top outputfile.txt[/COLOR] 

(where outputfile.txt has the above 3 commands in it), it does not show me the last line of** server1:>top** since the actual output was **server1:>tap^H^Hop^M**

This makes it difficult to manipulate the data in this text file since the file is not "true" text but a combination of text and control characters:

[COLOR=Red]server1:>file outputfile.txt
outputfile.txt: ASCII text, with CRLF line terminators, with overstriking[/COLOR]

Is there any way I can do a cat of this file and then redirect that to a file, with that file looking the same as it would to STDOUT (console/xterm)? 

If I currently try to do:

[COLOR=Red]server1:>cat outputfile.txt > newfile.txt[/COLOR]

I am left with all those original control characters, which makes for viewing in vi or parsing with grep difficult. Somewhere between cat and the console those control characters are actually interpreted rather than simply displayed....something I just cannot seem to replicate!

Any suggestions?

---

### Post by kjohri on 2009-07-28
Try

col -b <input_file

---

### Post by sedawk on 2009-07-28
No beautiful solution comes to my mind, but what you can try is this:

```

sed -e "s/[a-zA-Z0-9]^H//" <outputfile.txt >tmp1.txt
sed -e "s/[a-zA-Z0-9]^H//" <tmp1.txt >tmp2.txt
...

```
Do this until tmp(n).txt and tmp(n+1).txt do not differ
anymore. Then check for remaining ^H character (the sed
command might not have eleminated all existing pairs, e.g.
pairs with a whitespace coming first are not deleted by that
version.)

Another solution would be to send every line through some
tool that correctly eleminates the special characters before
creating some output (instead of deleting the backspace character
which creates wrong results ...).
A first try could be to use "echo" or "eval+echo" but that
might be completely nonsense:
[CODE]
cat outputfile.txt |while read LINE;do echo $LINE;done 
#or
cat outputfile.txt |while read LINE;do eval echo $LINE;done 
[CODE]

---

### Post by DaithiF on 2009-07-28
Hi,
@sedawk:  why wouldn't you want to eliminate space + backspace  pairs, or punctuation + backspace pairs too?  ie. why restrict to the [a-zA-Z0-9] characters?

if you match & eliminate  *any* character + backspace:
```
sed 's/.^H//g' inputfile 
```

it may get closer to the end goal, and no need to do multiple passes.

---

### Post by sedawk on 2009-07-29
> **DaithiF said:**
> Hi,
@sedawk:  why wouldn't you want to eliminate space + backspace  pairs, or punctuation + backspace pairs too?  ie. why restrict to the [a-zA-Z0-9] characters?

if you match & eliminate  *any* character + backspace:
```
sed 's/.^H//g' inputfile 
```

it may get closer to the end goal, and no need to do multiple passes.

Because this will also kill pairs of "^H^H" and therefore 
create wrong results. The best solution would be to
eleminate pairs of "not-^H" and "^H" but I'm not sure that
? [^^H] ? works (in sed). Even then you still have to deal with 
"overmotivated" ^H characters at the beginning of a line.

---

### Post by DaithiF on 2009-07-29
> **sedawk said:**
> Because this will also kill pairs of "^H^H" and therefore 
create wrong results. The best solution would be to
eleminate pairs of "not-^H" and "^H" but I'm not sure that
? [^^H] ? works (in sed). Even then you still have to deal with 
"overmotivated" ^H characters at the beginning of a line.

I think it mostly works ok ... if the input was abc^H^H, (leaving a net result of a) the .^H expression will first match & eliminate c^H, leaving ab^H, and next match & eliminate b^H, leaving a, the correct result.  When someone (fruitlessly) has entered backspaces at the start of a line, then we would match and eliminate most of them, only if an odd-number of backspaces were entered at the start of a line would 1 be left in the output.

---

### Post by damianpfister on 2009-07-30
I have tried the col -b option and it appears to work!
 
cat file.txt
 **Hello World!**
 
cat -v file.txt
 **Hello everyone^H^H^H^H^H^H^H^Hworld!^M**
 
col -b < file.txt > newfile.txt
 **Hello World!**
 
cat -v newfile.txt
 **Hello World!**
 
So essentially col -b acts as a filter of sorts, "interpreting" the backspace characters and only showing the final output not the initially deleted word nor the backspaces themselves.

Thanks for that piece of advice kjohri!

---

### Post by damianpfister on 2009-07-30
I have just tested your suggestions on 's/.^H//g' and it also works great!
Just shows how little I know my regular expressions.... :confused:

Thanks again guys!
:popcorn:

---

