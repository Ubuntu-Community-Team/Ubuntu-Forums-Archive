---
title: "Checking html with tidy"
date: 2011-07-11
forum: General Help
---

### Post by conradin on 2011-07-11
Hi all, 
Im checking some webpages Im trying to update using tidy. 
Im getting some messages about the doctype of my pages, Im trying for HTML 4.01
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">

but I keep getting some comment which amounts to the doctype not being formatted correctly. 

Does Anyone Know what the correct doctype format for html 4.01 transitional is? 

```
tidy doctype myHtml.html
```

---

### Post by conradin on 2011-07-14
Bump.
Can anyone show me a correnctly formated html 4.01 transitional doctype markup which doesnt give comments when checked using tidy?

---

### Post by mcduck on 2011-07-14
You are missing the last part of the doctype declaration. This should work:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

---

### Post by conradin on 2011-07-16
Thanks for the reply, but that didnt work. I did go to w3c to see what they are using, and that too also loaded the comments into tidy. But seriously, who wants to shoot for transitional html 4.01 these days anyhow? I sohuld go for something newer.

---

### Post by gmargo on 2011-07-16
List of recommended Doctype declarations: 
[http://www.w3.org/QA/2002/04/valid-dtd-list.html](http://www.w3.org/QA/2002/04/valid-dtd-list.html)

For validation of (x)html markup, I like to use the **w3c-markup-validator** package.

---

