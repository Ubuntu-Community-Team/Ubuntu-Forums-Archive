---
title: "AWK xml Extraction Help"
date: 2012-01-22
forum: General Help
---

### Post by drmrgd on 2012-01-22
I'm trying to extract a field value from a very long (maybe 30,000 lines or so) xml document.  I'm not entirely sure it's a well formed document, but that may not matter as the field I want is pretty static. The basic structure of it looks like:

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE DASDNA SYSTEM "http://www.biodas.org/dtd/dasdna.dtd">
<DASDNA>
<SEQUENCE id="chr1" start="115256475" stop="115256476" version="1.00">
<DNA length="2">
ag
</DNA>
</SEQUENCE>
</DASDNA>
<?xml version="1.0" standalone="no"?>
<!DOCTYPE DASDNA SYSTEM "http://www.biodas.org/dtd/dasdna.dtd">
<DASDNA>
<SEQUENCE id="chr1" start="115256476" stop="115256476" version="1.00">
<DNA length="1">
g
</DNA>
</SEQUENCE>
</DASDNA>
<?xml version="1.0" standalone="no"?>
<!DOCTYPE DASDNA SYSTEM "http://www.biodas.org/dtd/dasdna.dtd">
<DASDNA>
<SEQUENCE id="chr1" start="115256508" stop="115256508" version="1.00">
<DNA length="1">
c
</DNA>
</SEQUENCE>
</DASDNA>
<?xml version="1.0" standalone="no"?>
<!DOCTYPE DASDNA SYSTEM "http://www.biodas.org/dtd/dasdna.dtd">
<DASDNA>
<SEQUENCE id="chr1" start="115256518" stop="115256518" version="1.00">
<DNA length="1">
t
</DNA>
</SEQUENCE>
</DASDNA>
<?xml version="1.0" standalone="no"?>
<!DOCTYPE DASDNA SYSTEM "http://www.biodas.org/dtd/dasdna.dtd">
<DASDNA>
<SEQUENCE id="chr1" start="115256521" stop="115256521" version="1.00">
<DNA length="1">
a
</DNA>
</SEQUENCE>
</DASDNA>
<?xml version="1.0" standalone="no"?>
<!DOCTYPE DASDNA SYSTEM "http://www.biodas.org/dtd/dasdna.dtd">
<DASDNA>
<SEQUENCE id="chr1" start="115256524" stop="115256524" version="1.00">
<DNA length="1">
c
</DNA>

```

What I need to do is to grab the data between the <DNA length="*"> and </DNA> tags and move it to its own list, retaining the order.  I should note that the string "DNA length="*"" is variable, as is the actual length of the data between the tags.

I'm not very familiar with awk, but I'm thinking this is the tool to use for the job.  If my Python and / or Perl skills were better, I could probably write a script to do this as well.  But, I'm a little stuck there too.  

After playing around with it for a few hours, I did manage to come up with this:

```
awk '/DNA length="."/,/\/DNA/ {print}'
```

This seems to extract the block defined by the two tags I'm interested in.  However, asking to print $2 (like I assumed would be right) doesn't work.  It only outputs something like "length="1"".  I guess that I need to somehow split on a newline character (maybe?) by piping it to a second instance of awk, and then print field $2.  However, after playing with the FS and RS variables, I can't seem to get that work either.  The closest I got was:

```
awk 'BEGIN {RS=""} {FS="\n"}  {print $16}'
```

However, that only worked for 1 iteration of the block and stopped.  Piping it after the initial awk call from above was a catastrophic failure as well. 

Can anyone help me figure out how to extract this data into a separate list?

---

### Post by erind on 2012-01-22
Try the following code:

 ```
awk '/<DNA length="[0-9]+">/{ f=1; next } /<\/DNA>/{ f=0 } f'  filename

```Based on your sample, it outputs:

```
$ awk '/<DNA length="[0-9]+">/{ f=1; next } /<\/DNA>/{ f=0 } f'  filename
ag
g
c
t
a
c

```

---

### Post by drmrgd on 2012-01-22
> **erind said:**
> Try the following code:

 ```
awk '/<DNA length="[0-9]+">/{ f=1; next } /<\/DNA>/{ f=0 } f'  filename

```Based on your sample, it outputs:

```
$ awk '/<DNA length="[0-9]+">/{ f=1; next } /<\/DNA>/{ f=0 } f'  filename
ag
g
c
t
a
c

```

Wow!  That works perfectly!  Thanks a million for the help!

Out of curiosity (and in the interest of learning), what do the "f=1" / "f=0" bits do?  Are you using those to define fields somehow?

---

### Post by erind on 2012-01-22
> **drmrgd said:**
> Wow!  That works perfectly!  Thanks a million for the help!

Out of curiosity (and in the interest of learning), what do the "f=1" / "f=0" bits do?  Are you using those to define fields somehow?

Welcome. The '**f**' is a "flag" variable. When it's set **f=1**, it defines what record the printing will start, and viceversa, when **f=0** it stops the printing at that record - sort of ON/OFF switch, it defines what sections are to be printed. The "flags" usage is a common idiom in awk.

'**f**' by itself triggers the default action of printing the current record - '**f**' alone is equal to **f { print $0 }**. Also to make the code a bit more robust, I added anchors **^** and **$** in the regex part:

 ```
awk '/^<DNA length="[0-9]+">$/{ f=1; next } /^<\/DNA>$/{ f=0 } f'  filename

```

---

### Post by drmrgd on 2012-01-23
Oh, I see how that works now.  Very handy.  I definitely need to read up and learn awk better.  I have a feeling like it's going to really be a handy tool for me in the future.

Thanks again for the help!

---

