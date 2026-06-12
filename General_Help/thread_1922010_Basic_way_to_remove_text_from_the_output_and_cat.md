---
title: "Basic way to remove text from the output and cat"
date: 2012-02-07
forum: General Help
---

### Post by altjx on 2012-02-07
For example, if there's a .txt file on the desktop that has
```
abcdefg
abcdefg
abcdefg
```

Is there a way to strip out "defg" from that text file but keep abc? Of course there's a manual way, but what if the file has 4k lines of the same thing that needs to be stripped out.

---

### Post by iponeverything on 2012-02-07
> **altjx said:**
> For example, if there's a .txt file on the desktop that has
```
abcdefg
abcdefg
abcdefg
```

Is there a way to strip out "defg" from that text file but keep abc? Of course there's a manual way, but what if the file has 4k lines of the same thing that needs to be stripped out.

cat file | sed s/defg// > temp-file

---

### Post by SeijiSensei on 2012-02-07
Use the command line editor sed like this:

```
sed 's/defg//g' < /path/to/your/source_file > /path/to/your/output_file
```

The slashes are delimiters; the leading "s" means substitute.  So this substitutes the empty string for all instances of "defg".  The "g" means to apply the substitution "globally" so all instances of "defg" will be deleted.  (You can use any character as the delimiter so if the string to be edited includes slashes, you could use something like "s%/home/me%/home/you%g" instead.)

The pattern to be matched is a "regular expression," a method of creating pattern templates for strings.  For instance the command

```
sed 's/defg$//g' < /path/to/your/source_file > /path/to/your/output_file
```

will only remove instances of "defg" at the end of a line.  The "$" represents the end of the line.  Regular expressions are very powerful, but the syntax is a bit arcane.  If you search Google for 'regular expression' you'll find a lot of documentation.

---

### Post by papibe on 2012-02-07
> **iponeverything said:**
> cat file | sed s/defg// > temp-file

+1

or, if it is more a matter of columns instead of patterns, you can also try this:
```
cut -c-3 file > new_file 
```
Regards.

---

### Post by dgharmon on 2012-02-07
> **altjx said:**
> Is there a way to strip out "defg" from that text file

$sed -i 's/old/new/g' *.txt

---

### Post by altjx on 2012-02-07
> **iponeverything said:**
> cat file | sed s/defg// > temp-file

Thank you!

---

### Post by Khayyam on 2012-02-08
All ...

Many ways to skin a cat .. but awk is much more flexable for fields:

```
awk '{print (substr($1,1,4))}' input.txt > output.txt
```

"$1"  .. the first field
"substr" .. a substring .. we want only chars 1 to 4 of "$1"

So, unlike the sed subsitutions provided above we don't need to know the string, only the area we're operating on.

HTH ...

---

