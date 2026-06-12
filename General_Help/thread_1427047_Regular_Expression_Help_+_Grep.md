---
title: "Regular Expression Help + Grep"
date: 2010-03-11
forum: General Help
---

### Post by tophor on 2010-03-11
I have tried for at least an 2 hours, and I just can't figure out regulars. 

I want to grab and delete everything inbetween something that goes like this that includes newlines. 

<table width="100%"..........blah blah blah newline newline

......

</table>

I need to delete everything inbetween and including that in multiple html files in a directory. It happens twice per html file. Once at the top and once at the bottom.

Could somebody set me up?

---

### Post by Barriehie on 2010-03-11
Just so I understand correctly; you want to delete everything, inclusive:
**<table width="100%"> *other stuff* </table>**

---

### Post by tophor on 2010-03-11
Yeah. :-?

But a specific table that is width 100%.

---

### Post by Barriehie on 2010-03-11
I did it with gawk like this:
```

gawk '{ if($0 !~ /^<table width="100.*table>$/) print $0 }' ./blah.html
```and my blah.html file looks like this:
```

<table width="100%"> blah blah blah </table>
...some more stuff here...
<table width="100%"> blah blah blah </table>

```And it output like this:
```

01:51:49 /home/barrie/tmp $ >> gawk '{ if($0 !~ /^<table width="100.*table>$/) print $0 }' ./blah.html
...some more stuff here...
01:54:22 /home/barrie/tmp $ >> 
```See if that works for you.

---

### Post by geirha on 2010-03-11
grep is not the tool to use for parsing HTML. [http://www.codinghorror.com/blog/2009/11/parsing-html-the-cthulhu-way.html](http://www.codinghorror.com/blog/2009/11/parsing-html-the-cthulhu-way.html)

If there's no tables inside the table elements you want to remove, then you could hack it with ed, sed, awk or similar, but not very reliably. 

Try something like perl, python or ruby. They all have libraries/modules designed to parse html.

---

### Post by Barriehie on 2010-03-11
> **geirha said:**
> grep is not the tool to use for parsing HTML. [http://www.codinghorror.com/blog/2009/11/parsing-html-the-cthulhu-way.html](http://www.codinghorror.com/blog/2009/11/parsing-html-the-cthulhu-way.html)

If there's no tables inside the table elements you want to remove, then you could hack it with ed, sed, awk or similar, but not very reliably. 

Try something like perl, python or ruby. They all have libraries/modules designed to parse html.

@OP, this is correct!  The gawk line I presented will fail with tables within tables and EOL characters preceeding the closing table tag.  Next best thing on my end would be an emacs macro... :)

---

### Post by DaithiF on 2010-03-11
I don't think the previous solution works when the table is spread across multiple lines, as per the OP's requirement.  Subject to the same caveats above about nested tables, this should work for you.  It isn't sensitive to the beginning and ending table tags appearing at particular places in a line, which would be tricky to achieve with sed or awk.

```
perl -0 -p -e 's/<table width="100%".*?<\/table>//ms' testfile.html
```

when you're happy it does what you want, you can run it against multiple flies (& update them in-place) with:```

perl -0 -pi -e 's/<table width="100%".*?<\/table>//ms' *.html
```

---

### Post by tophor on 2010-03-11
Could you explain what the 

s/

and 

//ms

do?

Is it like a container for a string literal, so you don't have to escape stuff.

The  .*? , looks like a normal operator for "everything in between including newlines.

I'm gonna have to perl -?, to see what -0, -p, and -e do. 

Thanks though, ill try it out. 

Worked....great, on the first instance. How could I have it do it mutliple times per file?

---

### Post by asmoore82 on 2010-03-11
Got it!

This was more challenging than it seemed, that's what makes it fun :popcorn:

I've created a recursive function `eatnestedtable`
```
eatnestedtable( )
{
   read line
   while [ "$line" != "</table>" ]
      do
      [ "${line::6}" = "<table" ] && eatnestedtable
      read line
      done
}
```

and use it like this:
```
cat [COLOR="Blue"]test.html[/COLOR] |
   sed 's/^/"/' | sed 's/$/"/' |
   sed 's/</"\n</g' | sed 's/>/>\n"/g' |
   while read line
      do
      if [ ! "$line" = [COLOR="Red"]"<table width=\"100%\" border=\"10\">"[/COLOR] ]; then
         echo "$line"
      else
         eatnestedtable
      fi
      done |
   tr '\n' '\r' |
   sed 's/"\r</</g' | sed 's/>\r"/>/g' |
   tr '\r' '\n' |
   sed 's/^"//' | sed 's/"$//' > [COLOR="Blue"]output.html[/COLOR]
```
^customize the [COLOR="Blue"]filenames[/COLOR] to your needs

^^notice [COLOR="Red"]here[/COLOR] where it is hard coded for which tables to eliminate

---

