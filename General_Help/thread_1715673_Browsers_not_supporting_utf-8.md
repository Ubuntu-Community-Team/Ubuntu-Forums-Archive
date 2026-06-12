---
title: "Browsers not supporting utf-8?"
date: 2011-03-27
forum: General Help
---

### Post by 4dummies on 2011-03-27
Sorry if this comes off wrong -- but the problem is I'm trying to read the famous "[How To Ask Questions The Smart Way]("http://www.catb.org/~esr/faqs/smart-questions.html")" page and having trouble with it.

I've peeked at the XHTML, and the head section seems to properly advertise the encoding in use: 
[INDENT][INDENT]<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />[/INDENT][/INDENT]
and with Eric Steven Raymond as one of the authors, I think I'm safe assuming the problem is at my end.

However, I'm trying to read this with mozilla-firefox-3.6.16 and Chromium-10.0.643.133~r777, on Lucid, and I'm getting the raw characters.  Here's the top of the document as rendered by Firefox (not noticeably different from Chrome):
[IMG]http://kosmanor.com/~kevin/bugs/top.png[/IMG]

Here's something a bit further down:
[IMG]http://kosmanor.com/~kevin/bugs/mid.png[/IMG]

In both cases, I can read it but it's very annoying and I'd like to fix it, but I would appreciate even confirmation that this is or is not a configuration problem at my end.  I get the same result with Chrome, BTW,
so it's not just the browser.

---

### Post by Anonymous is Incognito on 2011-03-27
> **4dummies said:**
> In both cases, I can read it but it's very annoying and I'd like to fix it, but I would appreciate even confirmation that this is or is not a configuration problem at my end.  I get the same result with Chrome, BTW,
so it's not just the browser.

I checked Chrome and Firefox on Win 7 and Arch 64-bit. They all showed up the same way.

It is not only on your end, it is the webpage.

---

### Post by SeijiSensei on 2011-03-27
In Firefox, try forcing utf-8 by going to View > Character Encoding and clicking the Unicode radio button.  If it's already set to utf-8, try forcing ISO-8859-1 instead.

---

### Post by Irony on 2011-03-27
> **SeijiSensei said:**
> In Firefox, try forcing utf-8 by going to View > Character Encoding and clicking the Unicode radio button.  If it's already set to utf-8, try forcing ISO-8859-1 instead.
That worked for me - maybe the following should not be;

```
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```

but in lower case;

```
<meta content="text/html; charset=utf-8" http-equiv="content-type" />
```

---

### Post by 4dummies on 2011-03-28
I got a quick reply from ESR today.  He had not known there was a problem,
but could see it in Firefox.  Like an earlier poster, he also said that
view->Character Encoding->UTF-8 seemed to work around the problem.  I had
never used that thingie but it does indeed make things look a lot better.
At least for Firefox.

So the ball is in his court.

---

