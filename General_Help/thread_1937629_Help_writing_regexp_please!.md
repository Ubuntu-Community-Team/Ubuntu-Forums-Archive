---
title: "Help writing regexp please!"
date: 2012-03-08
forum: General Help
---

### Post by Kissell on 2012-03-08
I'm trying to match the episode numbers from some file names using some regexp expressions, but I am really bad at doing these.  It seems I get one thing to work it causes another problem somewhere else.

I want to match the "09" of ```
"Another - [09] - Body Paint.mkv"
``` but not the "01 of ```
"The Daily Show with Jon Stewart - [2012-01-09] - George Lucas.avi"
```

I can drop the brackets if that helps, but I would like to keep them...  

Also, sometimes the 09 is a three digit number, like the "001" of ```
"Naruto - [001] - Enter Naruto Uzumaki!.avi"
```

---

### Post by Vaphell on 2012-03-08
what do you need it for exactly?
you want to do **ls <some regex>** to magically list all files with digits in square brackets? Or maybe you want to extract that number to do something with it?

---

### Post by Kissell on 2012-03-08
I need it for an app that requires I give it a regexp to match the episode numbers in my files.  So there is no way around me needing the regexp, otherwise I would solve it another way, because I do not like using regexp.

---

### Post by Vaphell on 2012-03-08
2 or 3 digits -> [0-9]{2,3} or [0-9]?[0-9]{2} or [0-9]?[0-9][0-9]
2 or 3 digits in square brackets -> \[[0-9]{2,3}\] etc
but it depends on the flavor of regex

> because I do not like using regexp.
that's very unwise. They are one of the best things since sliced bread and you can't live without them once you become familiar with them, they are THAT cool ;-)

---

### Post by Kissell on 2012-03-08
I recognize regexp's potential, just hate that I can never get them to work right.

```
<regexp>[\._ \- ]()([0-9]{2,3}+)</regexp>
```
matches
```
Another - 09 - Body Paint.mkv
```
but does NOT match
```
Bleach - 363 - Fierce Fight! Shinigami vs. Xcution.mkv
```

I think it should match them both, and I don't understand why it doesn't.

---

### Post by TeoBigusGeekus on 2012-03-08
What about this?
```
ls|grep ".*\[[0-9]*\].*"
```

---

### Post by lechien73 on 2012-03-08
A great resource for testing regular expressions is here: [http://www.regular-expressions.info/javascriptexample.html](http://www.regular-expressions.info/javascriptexample.html)

I got it working with a similar syntax to @TeoBigusGeekus's example:

```
.*\[[0-9]{2,3}\].*
```

The only difference is that mine matches a minimum of 2 and maximum of 3 digits inside the square brackets.

---

### Post by vasa1 on 2012-03-08
> **Kissell said:**
> I'm trying to match the episode numbers from some file names using some regexp expressions, but I am really bad at doing these.  It seems I get one thing to work it causes another problem somewhere else.

I want to match the "09" of ...
It would help if you include the list of filenames that you're dealing with and then explain what you want.

---

### Post by Kissell on 2012-03-08
> **TeoBigusGeekus said:**
> What about this?
```
ls|grep ".*\[[0-9]*\].*"
```

That works for "ls" in a terminal, but not as a regexp in the application I'm trying to pass it to.

---

### Post by Kissell on 2012-03-08
duplicate

---

### Post by Kissell on 2012-03-08
duplicate, bad connection

---

### Post by Kissell on 2012-03-08
> **vasa1 said:**
> It would help if you include the list of filenames that you're dealing with and then explain what you want.

I'm not sure what you're asking for here in addition to what I've already listed.

---

### Post by TeoBigusGeekus on 2012-03-08
What short of app is this?
What does it do?
Can't you replace it with a bash script?

---

### Post by Kissell on 2012-03-08
> **TeoBigusGeekus said:**
> What short of app is this?
What does it do?
Can't you replace it with a bash script?

The app is XBMC, the advancedsettings.xml file requires a regexp to use absolute numbering.  but all the online examples people have posted that say it works, are wrong, in that they only work for episodes without brackets and the solution causes errors in detection of episodes named with dates, such as the daily show. I've listed in my original post.

It can't be replaced with a bash script, I'm not trying to do something outside the application, I'm trying to get the application to match these filenames as tv episodes by passing it a regexp, but nothing I'm trying seems to work.  

I've never messed with regexp much, so I thought maybe it was just something I didn't understand, but really it seems the reason is that regexp isn't standardized, something that works in the ubuntu command line doesn't work elsewhere.

---

### Post by TeoBigusGeekus on 2012-03-08
Putting my line in the regexp, does it even come any close to what you want?
What episodes does it include?

---

### Post by Kissell on 2012-03-08
> **TeoBigusGeekus said:**
> Putting my line in the regexp, does it even come any close to what you want?
What episodes does it include?

It doesn't work at all...  doesn't match anything...  weird right!?

There's like a hundred different ways to say the same thing in regexp, and I think I've tried them all.

---

### Post by Kissell on 2012-03-08
Oh man...  it's working now...

Turns out it wasn't entirely a regexp problem, but also an application problem.

The application lets me pass a parameter to it in the XML file to "prepend" the regexp rules.  Without doing that, the app uses it's rules first and appears not always use the rules in the XML file.  Weird, you'd think it'd use the rules in the XML file after it failed to find a match.

Anyway, got it working with this: 
```

<tvshowmatching action="prepend">
<regexp>[\._ \- ](\d{2,3})</regexp>
</tvshowmatching>

```

I had tried the prepend command before, but I guess in those times my regexp was really screwed up because by then I was trying anything and everything.  

Anyway, this appears to be a valid line for everything I wanted, except it obviously doesn't work with brackets...  I'm happy enough with this solution, but will try for a few more minutes to see if I can get brackets to work too before renaming my files to not use them.

---

### Post by Kissell on 2012-03-08
```
<regexp>[\._ \- ](\d{2,3})</regexp>
``` matches```
Another - 09 - Body Paint.mkv
```

However, neither ```
<regexp>[\._ \- ](\\[\d{2,3}\\])</regexp>
``` nor ```
<regexp>[\._ \- ](\[\d{2,3}\])</regexp>
```  match ```
Another - [09] - Body Paint.mkv
```

Seems I'll have to abandon using brackets in the names...

---

### Post by Kissell on 2012-03-08
Ah, finally got it...  
```
<regexp>[\._ \- ]\[(\d{2,3})\]</regexp>
```
works with everything.

:popcorn:

---

### Post by TeoBigusGeekus on 2012-03-08
Hurray!!!

---

### Post by kevdog on 2012-03-08
I'm no expert in regexp, but I've written a lot in my time, however can you explain the syntax in your final expression?  I'm even a little bit lost.

---

### Post by Vaphell on 2012-03-08
<dot or underscore or space or minus or space>[<2 or 3 digits>]

---

### Post by TeoBigusGeekus on 2012-03-08
...and the reason this regex works remains a complete mystery to me...
Where's Sisco311 when you need him?

---

### Post by lechien73 on 2012-03-08
I understand the regex, but I still don't really understand the application, since 1) it only returns the numbers from the filenames, and 2) the examples we saw only had a space preceding the numbers in [].

If he's having to match a dot, space, minus or underscore preceding the numbers in square brackets, then the filenames must be a bit messed up.

---

### Post by Vaphell on 2012-03-08
OP didn't exactly elaborate what kind of data he has to deal with, he gave only 3 clear-cut examples and who knows what the app does exactly with the supplied regex

---

### Post by Kissell on 2012-03-08
The examples were representative of an exact pattern that applies 100% of the time in my file names.

The regexp that works is hacked together from my partial knowledge of how regexp works and other examples I picked up from other people...  so it may also match things with other filenames which are irrelevant to my file names.

---

