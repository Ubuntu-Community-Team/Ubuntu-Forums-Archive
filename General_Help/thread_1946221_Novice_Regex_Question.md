---
title: "Novice Regex Question"
date: 2012-03-24
forum: General Help
---

### Post by ShareBuntu on 2012-03-24
Really dumb regex question, but how would I invoke a command from the terminal to use the following regex command? I presume it would be a combination of cat on a file with the URLs and grep?

Here's the regex command (from [http://daringfireball.net/2010/07/improved_regex_for_matching_urls):](http://daringfireball.net/2010/07/improved_regex_for_matching_urls):)

```
(?i)\b((?:https?://|www\d{0,3}[.]|[a-z0-9.\-]+[.][a-z]{2,4}/)(?:[^\s()<>]+|\(([^\s()<>]+|(\([^\s()<>]+\)))*\))+(?:\(([^\s()<>]+|(\([^\s()<>]+\)))*\)|[^\s`!()\[\]{};:'".,<>?«»“”‘’]))
```

---

### Post by SeijiSensei on 2012-03-24
grep 'pattern' filename

or its equivalent

grep 'pattern'  < filename

If you want to grep a fixed string, use

echo 'string' | grep 'pattern'

For complex patterns, it is important to encase them in single quotes so that the bash shell won't try and interpret the pattern.  If you're searching for a single word, you can omit the quotes.

---

### Post by ShareBuntu on 2012-03-24
> **SeijiSensei said:**
> grep 'pattern' filename

or its equivalent

grep 'pattern'  < filename

If you want to grep a fixed string, use

echo 'string' | grep 'pattern'

For complex patterns, it is important to encase them in single quotes so that the bash shell won't try and interpret the pattern.  If you're searching for a single word, you can omit the quotes.
Odd that the regex command I used won't find any URLs in a file...

---

### Post by SeijiSensei on 2012-03-24
Well perhaps it makes sense to start slowly at first.  What happens when you run "grep 'http://' filename"?

---

### Post by Vaphell on 2012-03-24
quotes in exclusion part [^....] mess things up but once you escape them the expression appears to work correctly.

```
$ cat test.txt 
something something http://www.w3.org/Addressing/URL/url-spec.txt
<a>https://accounts.google.com/ServiceLogin?service=mail&passive=true&rm=false&continue=https://mail.google.com/mail/?ui%3D2%26shva%3D1&ss=1&scc=1&ltmpl=default&ltmplcache=2#inbox
"""http://www.youtube.com/watch?v=DW6LR2k4l6E&feature=g-logo&context=G212ed86FOAAAAAAACAA#t=1m20"""
www.fu.co.uk

$ grep -P '(?i)\b((?:https?://|www\d{0,3}[.]|[a-z0-9.\-]+[.][a-z]{2,4}/)(?:[^\s()<>]+|\(([^\s()<>]+|(\([^\s()<>]+\)))*\))+(?:\(([^\s()<>]+|(\([^\s()<>]+\)))*\)|[^\s`!()\[\]{};:[COLOR="Blue"]'\''[/COLOR]".,<>?«»&#8220;&#8221;&#8216;&#8217;]))' test.txt
something something **http://www.w3.org/Addressing/URL/url-spec.txt**
<a>**https://accounts.google.com/ServiceLogin?service=mail&passive=true&rm=false&continue=https://mail.google.com/mail/?ui%3D2%26shva%3D1&ss=1&scc=1&ltmpl=default&ltmplcache=2#inbox**
"""**http://www.youtube.com/watch?v=DW6LR2k4l6E&feature=g-logo&context=G212ed86FOAAAAAAACAA#t=1m20**"""
**www.fu.co.uk**
```

in that uber pattern the blue part does 'exit single-quoted string of the expression, glue it together with escaped ' (literal char) and enter the string again': (quoted string)stuff(quoted string)
simple example:
```
$ x='"abc"'1'def'; echo $x
"abc"1def

``` 
you could keep the original expression in file somewhere, read it into a variable and use it directly. Strings typed explicitly in script body are bound to be interpreted and you have to code around that.

---

### Post by ShareBuntu on 2012-03-24
> **Vaphell said:**
> quotes in exclusion part [^....] mess things up but once you escape them the expression appears to work correctly.

[/code]$ cat test.txt 
something something [http://www.w3.org/Addressing/URL/url-spec.txt](http://www.w3.org/Addressing/URL/url-spec.txt)
<a>[https://accounts.google.com/ServiceLogin?service=mail&passive=true&rm=false&continue=https://mail.google.com/mail/?ui%3D2%26shva%3D1&ss=1&scc=1&ltmpl=default&ltmplcache=2#inbox](https://accounts.google.com/ServiceLogin?service=mail&passive=true&rm=false&continue=https://mail.google.com/mail/?ui%3D2%26shva%3D1&ss=1&scc=1&ltmpl=default&ltmplcache=2#inbox)
"""http://www.youtube.com/watch?v=DW6LR2k4l6E&feature=g-logo&context=G212ed86FOAAAAAAACAA#t=1m20"""
[www.fu.co.uk](www.fu.co.uk)

$ grep -P '(?i)\b((?:https?://|www\d{0,3}[.]|[a-z0-9.\-]+[.][a-z]{2,4}/)(?:[^\s()<>]+|\(([^\s()<>]+|(\([^\s()<>]+\)))*\))+(?:\(([^\s()<>]+|(\([^\s()<>]+\)))*\)|[^\s`!()\[\]{};:[COLOR="Blue"]'\''[/COLOR]".,<>?«»“”‘’]))' test.txt
something something **[http://www.w3.org/Addressing/URL/url-spec.txt](http://www.w3.org/Addressing/URL/url-spec.txt)**
<a>**[https://accounts.google.com/ServiceLogin?service=mail&passive=true&rm=false&continue=https://mail.google.com/mail/?ui%3D2%26shva%3D1&ss=1&scc=1&ltmpl=default&ltmplcache=2#inbox](https://accounts.google.com/ServiceLogin?service=mail&passive=true&rm=false&continue=https://mail.google.com/mail/?ui%3D2%26shva%3D1&ss=1&scc=1&ltmpl=default&ltmplcache=2#inbox)**
"""**[http://www.youtube.com/watch?v=DW6LR2k4l6E&feature=g-logo&context=G212ed86FOAAAAAAACAA#t=1m20](http://www.youtube.com/watch?v=DW6LR2k4l6E&feature=g-logo&context=G212ed86FOAAAAAAACAA#t=1m20)**"""
**[www.fu.co.uk](www.fu.co.uk)**[/code]

in that uber pattern the blue part does 'exit single-quoted string, glue it together with escaped ' (literal char) and enter the string again'

That works perfectly! Thank you, guys. The question that now remains: Is it possible to display only the results grep found and not the entire line the result is on?

---

### Post by ShareBuntu on 2012-03-24
Looks like the argument "-o" for grep does the trick! Thanks again!

---

