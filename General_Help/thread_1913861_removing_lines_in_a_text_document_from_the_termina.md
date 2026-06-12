---
title: "removing lines in a text document from the terminal"
date: 2012-01-23
forum: General Help
---

### Post by Canaryguy on 2012-01-23
Hello,

Does anybody know how to remove specific lines from a text document using the terminal? I can watch the lines I want to remove with the command grep but I want to create another document where these lines don't appear.

Thanks.

---

### Post by DiscoKiller on 2012-01-23
try using sudo gedit /filename which opens the document in a graphical text editor rather than in a terminal. 
 
DK

---

### Post by cookie1980 on 2012-01-23
You should have a look at ["sed"]("http://en.wikipedia.org/wiki/Sed").

---

### Post by sisco311 on 2012-01-23
```
grep -v PATTERN file > new_file
```

---

### Post by haqking on 2012-01-23
> **DiscoKiller said:**
> try using sudo gedit /filename which opens the document in a graphical text editor rather than in a terminal. 
 
DK

you should use **gksudo** with graphical apps such as gedit and not **sudo**.

Also you only need to use a gksudo or sudo action for editing if it is system file or file where admin priveleges is needed, no need for it on personal files.

Also you can use, vi/vim, nano, sed etc.  There are many editors to edit files from terminal.

peace

---

### Post by DiscoKiller on 2012-01-23
Hi Haqking, 
 
can you explain to me why you would need to use gksudo? 
 
not quite a newb but not aware of any difference between the two. 
 
Cheers
 
DK

---

### Post by nothingspecial on 2012-01-23
Read this [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by haqking on 2012-01-23
> **DiscoKiller said:**
> Hi Haqking, 
 
can you explain to me why you would need to use gksudo? 
 
not quite a newb but not aware of any difference between the two. 
 
Cheers
 
DK

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

saves me typing ;-)

and also read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) which explains some more

---

### Post by sisco311 on 2012-01-23
EDIT: D'oh! nothingspecial & haqking beat me to it. :)


> **DiscoKiller said:**
> Hi Haqking, 
 
can you explain to me why you would need to use gksudo? 
 
not quite a newb but not aware of any difference between the two. 
 
Cheers
 
DK

[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by DiscoKiller on 2012-01-23
Cheers dudes!!
 
I shall watch what what I sudo in future...
 
Peace
DK

---

### Post by haqking on 2012-01-23
> **DiscoKiller said:**
> Cheers dudes!!
 
I shall watch what what I sudo in future...
 
Peace
DK

no worries.

Also remember you only need to use sudo/gksudo for admin tasks, there is no requirement to use for text editing unless the file being edited (which wasnt stated in the OP) is owned by root or requires admin privelege.

Otherwise you will end up with personal files being owned by root.

Cheers

---

### Post by DiscoKiller on 2012-01-23
yeah i`m just gonna shut up... I`ll leave the advice to the people that actually know what they are talking about :)
 
Peace
 
DK

---

### Post by Canaryguy on 2012-01-23
> **sisco311 said:**
> ```
grep -v PATTERN file > new_file
```

That works fine for me. I should have known that! but I don't have too much practice with the terminal yet. 
Thanks sisco311

---

### Post by sisco311 on 2012-01-23
You are welcome!

---

### Post by tombott on 2012-01-23
sed is indeed the tool you need.

In a terminal

```
sed '/^$/d' textfile.txt > temptext
mv temptext newtext.txt
```

Line one will remove all empty text from the file specified and copy the output to a temp file called temptext
Line two moves the text from the the temp file to a permanant file.

Hope that makes sense!

---

### Post by sisco311 on 2012-01-23
> **tombott said:**
> sed is indeed the tool you need.


I'd use ed. :)

```
ed -s file <<< $'g/foo/d\n,p' > tempfile
```
Or to edit the file in place:
```
ed -s file <<< $'g/foo/d\nw'
```

See:
[http://wiki.bash-hackers.org/howto/edit-ed](http://wiki.bash-hackers.org/howto/edit-ed)
and BashFAQ 021

---

### Post by tombott on 2012-01-23
> **sisco311 said:**
> I'd use ed. :)

```
ed -s file <<< $'g/foo/d\n,p' > tempfile
```
Or to edit the file in place:
```
ed -s file <<< $'g/foo/d\nw'
```

See:
[http://wiki.bash-hackers.org/howto/edit-ed](http://wiki.bash-hackers.org/howto/edit-ed)
and BashFAQ 021

The joys of linux, always more than one way to skin a cat.
I'm not familiar with 'ed' but I will take a look. Cheers!

---

