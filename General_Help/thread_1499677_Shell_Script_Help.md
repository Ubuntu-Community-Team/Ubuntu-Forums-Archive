---
title: "Shell Script Help"
date: 2010-06-02
forum: General Help
---

### Post by Vishal Agarwal on 2010-06-02
Hi,

I want to download some files using the wget command. I want to create a shell script, which will extract all the required parameters from the given URL of download location.
eg.
[http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip](http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip)

Out of this I want to extract 
wget [http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip](http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip) -O FILENAME -a Filename

1. Here the source file name contains the (ABCD.ABC) which I don't want into the -O or -a output filename.
2. The FIRSTDIR can be /FIRSTDIR/SECONTDIR/..../..... ans so on. Out of that the last / contains the file name.

Thanks in advance .

---

### Post by blchinezu on 2010-06-02
> ```
#!/bin/bash

text="http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip"

ext=`echo "$text" | awk -F"." '{print $NF}'`
remove="(`echo $text | awk -F"(" '{print $NF}' | sed -e 's/.'$ext'//g'`"
filename_ext=`echo $text | awk -F"/" '{print $NF}' | sed -e 's/'$remove'//g'`
filename_only=`echo $text | awk -F"/" '{print $NF}' | sed -e 's/'$remove'//g' | sed -e 's/.'$ext'//g'`

echo -e "ext\t\t= $ext\nremove\t\t= $remove\nfilename_ext\t= $filename_ext\nfilename_only\t= $filename_only"
```and this is the output of running it:

```
ext        = zip
remove        = (ABCD.ABC)
filename_ext    = FILENAME.zip
filename_only    = FILENAME
```it doesn't matter how big is the folder tree it will still get this data as it get's what's after the last slash "**/**" to work with
i suppose you can figure it out from here :)

this was so you can understand something... so next time you can do it yourself.. now here's how to get it in one line:



> ```
filename=`echo $text | awk -F"/" '{print $NF}' | sed -e 's/('$(echo $text | awk -F"(" '{print $NF}' | sed -e 's/.'$(echo "$text" | awk -F"." '{print $NF}')'//g')'//g'`
```and if you echo the *$filename *variable you'll get:
```
FILENAME.zip
```

---

### Post by DaithiF on 2010-06-02
slightly simpler sed expression to do it in one line:
```
$ in="http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip"
$ out=$(echo $in | sed -r 's/^(.*\/)([^(]*)(.*)$/wget \0 -O \2 -a \2/')
$ echo $out
wget http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip -O FILENAME -a FILENAME

```

---

### Post by blchinezu on 2010-06-02
> **DaithiF said:**
> slightly simpler sed expression to do it in one line:
```
$ in="http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip"
$ out=$(echo $in | sed -r 's/^(.*\/)([^(]*)(.*)$/wget \0 -O \2 -a \2/')
$ echo $out
wget http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip -O FILENAME -a FILENAME

```
and that's kind of a sed master :) i don't know that much but i manage to do the thing.. still your script is better

---

### Post by geirha on 2010-06-02
And with parameter expansions:
```

#!/bin/bash
url='http://WEBSITE/FIRSTDIR/FILENAME(ABCD.ABC).zip'
filename=${url##*/} filename=${filename%%(*} ext=${url##*.}
wget -O "$filename.$ext" -a "$filename.log" "$url"

```

[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by Vishal Agarwal on 2010-06-03
Thanks to all of you.

I was knowing that there is some way to solve this equation, was not getting the solution. 

Thanks to all of you again.

Regards,

Vishal Agarwal

:)

---

### Post by blchinezu on 2010-06-03
> **geirha said:**
> [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)
thanks for that link... it's really useful

---

