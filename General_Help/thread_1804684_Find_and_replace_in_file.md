---
title: "Find and replace in file"
date: 2011-07-15
forum: General Help
---

### Post by conradin on 2011-07-15
Hi Everyone,
I want to find html tags in a webpage File, and either erase them entirely, or replace them with commas where appropriate. 

I have alot of ideas about how to achieve this, but Im wondering if there is a terminal application out there which does the same thing already. 

for example:
I save the webpage:[http://www.agiweb.org/direct/](http://www.agiweb.org/direct/)
I can then use:
```
cat index.html | grep "@" >> someFile
```
and get all the email addresses. but Ill also have a bunch of HTML tages.
so Then I could Use parameter substitution in bash to weed out all the html tags, but that could fail in various ways, and I'd have to write parameters for all the types of tags and parts of tags that I could search for. Then I'd be at the mercy of any formating discrepancies, coding errors, or murphys law. 

So I'm wondering, is there a program in the repos, which can make parsing out html tags simple?

---

### Post by Grenage on 2011-07-15
sed is only way of doing it:

```
cat index.html | grep "@" | sed 's/<HTML>//' >> someFile
```

You can use regexes in sed, so it's very configurable and adaptable; there are some great sed guides on the internet.  I am sure others will suggest or concise and elegant solutions, but there's one option.

This, for example, should remove anything between < >, including the brackets:

```
cat index.html | grep "@" | sed 's/<.*>//' >> someFile
```

You could also use sed alone, and completely bypass grep.

---

