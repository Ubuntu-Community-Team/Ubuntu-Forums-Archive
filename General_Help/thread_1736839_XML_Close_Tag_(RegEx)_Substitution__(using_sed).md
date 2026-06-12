---
title: "XML Close Tag (RegEx) Substitution  (using sed?)"
date: 2011-04-22
forum: General Help
---

### Post by kd7swh on 2011-04-22
Hi everyone,

This makes me feel like a total n00b but I'm trying to figure out how to replace an XML close tag (such as </pagenum> ) with the same XML close tag followed by yet another close tag.

( I want every occurrence of '</pagenum>' to be replaced with '</pagenum></p>' )
 
I've tried using something like this:

```
sed 's/<\/pagenum>/<\/pagenum><\/p>/' old.xml new.xml

```

What am I missing? Please forgive me. I'm diving head first into RegEx.

Hopefully there will be a day when I laugh at this post.

Thanks,

Jon

---

### Post by Vaphell on 2011-04-22
i am guessing that old.xml is source and new is supposed to be created with these changes? if so add > new.xml at the end
```
sed 's:</pagenum>:&</p>:g' old.xml
```

such expression works - 100% confirmed
```
$ echo '</pagenum> </pagenum>' | sed 's:</pagenum>:&</p>:g'
</pagenum></p> </pagenum></p>

```
1st char after s defines a separator so you don't have to use / and escape it later, just pick something that is not used anywhere in your pattern
& = part matching the pattern
g at the end tells sed to replace all occurences, not only first

---

### Post by kd7swh on 2011-04-22
Wonderful!

Now implicitly,  

```
's:</pagenum>:&</p>' old.xml
```

would only apply to the first </pagenum> in the file?

That would be useful for other things.

Ideally, I would like to be to search for the first line on each page in a text file and insert XML tags around the content of that line.

Any ideas for that one? (Marking up page numbers in custom XML)

Thanks!

---

### Post by Vaphell on 2011-04-23
unfortunately no, sed works line by line

it's easy to test, just echo some multiline string with test cases and pipe it to sed with expression you want
```
echo $'</pagenum></pagenum>\n</pagenum></pagenum>' | sed 's:</pagenum>:&</p>:'
</pagenum></p></pagenum>
</pagenum></p></pagenum>

echo $'</pagenum></pagenum>\n</pagenum></pagenum>' | sed 's:</pagenum>:&</p>:g'
</pagenum></p></pagenum></p>
</pagenum></p></pagenum></p>
```

sed is good at performing repetitive braindead tasks, but it's not a suitable tool to improve on xml logic as its work is highly dependent on file formatting. If you had your xml with 1 line/page then the fix would be trivial. Sed can be made to work with multiline stuff but imo it would be easier to write a not so long script to do that.
It all depends on formatting and uniqueness of the lines to change. Paste some example snippet that shows the basic structure of the file and pages

---

### Post by kd7swh on 2011-04-23
As I continue to study, it is becoming clear that I need to use something a little more complex than sed to solve my XML issues.

I think I can see myself writing some Perl scripts in the near future...

I digitize entire textbooks into DAISY Digital Taking Books {DAISY XML) but I run into a lot of problems when validating the XML which is generated.

I am following these structure guidelines:
[http://www.daisy.org/z3986/structure/SG-DAISY3/index.html#contents](http://www.daisy.org/z3986/structure/SG-DAISY3/index.html#contents)

Basically, this XML has taken me a year to learn and I would love to find ways of automating the mark-up. It would save me so much trouble its not even funny.

I am marking up plain text into this (DTBook) XML:
```
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE dtbook
  PUBLIC "-//NISO//DTD dtbook 2005-3//EN" 
  "http://www.daisy.org/z3986/2005/dtbook-2005-3.dtd">
  <dtbook version="2005-3" xml:lang="de-DE">
    <head>
      <meta name="dc:Title" content="Hello World"/>
    </head>
    <book>
      <bodymatter>
              <pagenum id=1>1</pagenum>
          <level1>
          <h1>Hello World</h1>
          <p>This is an example.</p>
               <pagenum id=2>2</pagenum>
    <p> Something like that.</p>
        </level1>
      </bodymatter>
    </book>
  </dtbook>

```


See also:
[http://en.wikipedia.org/wiki/DTBook](http://en.wikipedia.org/wiki/DTBook)

---

### Post by Vaphell on 2011-04-24
while your xml is formatted quite regularly and it's possible to do modifications to some extent with basic tools, it's indeed better to think about perl or python - they are very flexible and have xml tools readily available.

---

