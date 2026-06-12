---
title: "Odd problem trying to cat files"
date: 2009-08-30
forum: General Help
---

### Post by Murdoc_of_puts on 2009-08-30
Alright fine peoples,

Here's the problem I'm having.  I'm trying to get Linux to do my work for me.  I have a really big dictionary file that I've been working on for sometime.  I recently noticed that there are alot of repeat entries in it.  So what I'm trying to do is get cat to sort through all of them, kick out the repeats, and then organize what's left  in alphabetical order, then put it in a nice txt file for me.  Steps one and two seem to be working all right, But I can't get it to write to the file it creates.  Every time it just makes a blank txt file.  I don't know what I'm doing wrong here, so I figured I'd ask for help before throwing my computer into traffic.  Thanks in advance.  Here's the command I'm using.

cat bigdic.txt | tr -cs A-Za-z '\012' | tr A-Z a-z | sort | uniq | > biggest.txt

*also trying with the >> biggest.txt  option.

---

### Post by The Cog on 2009-08-31
That last pipe shouldn't be there. Try this:
cat bigdic.txt | tr -cs A-Za-z '\012' | tr A-Z a-z | sort | uniq > biggest.txt
I haven't looked at the rest. I just saw that | > which is definitely wrong.

---

### Post by apmcd47 on 2009-08-31
"Useless use of cat"

Try:[PHP]< bigdic.txt  tr -cs A-Za-z '\012' | tr A-Z a-z | sort -u > biggest.txt[/PHP]
"<" is the reverse of ">", that is it tells the shell to send the contents of the file to the standard input of the process. As a result you don't need the cat or the initial pipe symbol.

sort -u "uniquefies" the sorted list.

As The cog says, you had an unnecessary pipe symbol there. You don't need "| >". I suspect you tried a pipe into another process (less or more) to check it looks right then changed it into a "send to file" and forgot the pipe needed deleting from your command line.

Andrew

---

### Post by Gen2ly on 2009-08-31
Off-topic, but like to know since I'm just beginning to use tr, what does 'tr -cs A-Za-z '\012'' do?  From the man page -c is complement and -s is squeeze-repeats but I don't really understand that.  I'm also guessing the \012 is an ASCII representation of a key??

---

### Post by DaithiF on 2009-08-31
in general tr set1 set2 translates characters from set1 to set2

set2 here = '\012' which is the newline character (in octal)
set1 = A-Za-z, but with the -c flag this set is complemented, which means everything that *isn't* an alphabetical character.

so first every non-alpha character gets replaced with a newline.  The -s flag then takes effect, and squeezes out repeated newlines from the result, so that the net effect is that you've created a vertical list of words, 1 word per line, and with all spaces, punctuation, numbers etc removed.

---

### Post by DaithiF on 2009-08-31
maybe thats not very clear, here are some examples to help:
given a test string consisting of punctuation, spaces, numbers and some text, like:
```
.,!5 test

```
lets try the tr command but rather than translating to newlines which we can't see, translate instead to some character we can see -- 'X', so:
first try without either the -c or -s params:
```
echo -n '.,!5 test' | tr A-Za-z X
.,!5 XXXX

```
now add the '-c' param -- instead of translating the A-Za-z chars, we'll translate everything else:
```
echo -n '.,!5 test' | tr -c A-Za-z X
XXXXXtest

```
and finally add in the -s squeeze repeats param:
```
echo -n '.,!5 test' | tr -cs A-Za-z X
Xtest
 
```
 
hope that helps

---

### Post by Gen2ly on 2009-08-31
Ohhhohoho.  Very nice.  So squeeze is being used in the case to prevent multiple newlines.  Very cool.  I'm really getting to like these tools in Linux.

Thanks DaithiF.

---

### Post by Murdoc_of_puts on 2009-09-02
Thanks so much, that'll teach me.  Any way, thanks to all of you.  Just so you know both of those lines of code produced the same document, so that's neat. And it did exactly what I wanted it to do!  I was wondering...how would I go about pulling the numerical entries out of the original bigdic.txt ?  Also, I had alot of Half numbered half lettered entries.  EX: h33lp  , is there a way to get linux to do my bidding here as well?


Edit:
Ummm....so I just answered my own question-just took out all the A-Za-z and the second tr command.  So......that's so much for all of the help!

 < bigdic.txt  tr -cs '\012'| sort -u > bigges0t.txt

---

