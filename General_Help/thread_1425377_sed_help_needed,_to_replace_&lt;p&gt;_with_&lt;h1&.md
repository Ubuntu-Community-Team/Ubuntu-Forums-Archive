---
title: "sed help needed, to replace &lt;/p&gt; with &lt;/h1&gt;"
date: 2010-03-09
forum: General Help
---

### Post by Funkey Monkey on 2010-03-09
Problem:
<h1><a id="heading-1" />Heading<br /br><em>Some Emphasised Heading</em>**</p>**

I need to write a SED substitution script to do the following:
1) Look for a String Starting with <h1>
2) and then ending with </p>
3) Replace only </p> with </h1>

Issues:
1) The heading changes form page to page
2) The <h1> and </p> is not always on the same line.

I have done a lot of reading before asking but I am still not sure how to phrase the SED command.

I am thinking:
```
sed -i.old -e '/\<h1\>\<a\ id.*\<\p>/ s_\<\p>_\<\/h1\>_g' *html
```

but it is _[COLOR="Red"]NOT[/COLOR]_ working.

Please help.

Some of the great websites I read:
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by cong06 on 2010-03-09
Ok, well, I'm just thinking about how I'd do this... and I'd probably try perl.

Maybe put the document in a variable, and cut out the large segments of text:
```

$html_doc =~ /(\<h1\>.*?\<\/p\>)/i; # i for case insensitive
$text = $1;
$text_b = $text; # back it up

```
and put them in a perl variable, and then do a simple search and replace
```

$text =~ s/\<\p>/\<\/h1\>/g; # do the replacement

```
Then maybe replace:
```

$html_doc =~ s/$text_b/$text/g;

```

Then repeat until you can't find another pattern match, and dump html_doc back to a file.

Just a note, since </p> is always at the end of the $text string, it might make sense to only replace at the end. (s/\<\p>$/\<\/h1\>/g;)

---

### Post by Funkey Monkey on 2010-03-09
> **cong06 said:**
> 
Just a note, since </p> is always at the end of the $text string, it might make sense to only replace at the end. (s/\<\p>$/\<\/h1\>/g;)

Thanks for the response cong06.

I would like to replace p with h1 using sed and not perl.
Because:
a) I am trying to learn how to use sed (and have done a lot of reading on sed)
b) I have no experience with perl (and do not wish to learn it while learning sed)

With regards to your last Idea, (s/\<\p>$/\<\/h1\>/g) yes that is a good idea, except that I need to replace only 1 </p> and there are lots of <p></p> combinations correctly closed with </p>'s and your command will "break" the <p></p>'s.

**[COLOR="RoyalBlue"]I really hope some one can guide me to understand why my command (in 1st post) is not working as expected.[/COLOR]**

Thanks for your time.

---

