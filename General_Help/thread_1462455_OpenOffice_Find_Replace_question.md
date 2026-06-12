---
title: "OpenOffice Find Replace question"
date: 2010-04-25
forum: General Help
---

### Post by uzd4ce on 2010-04-25
In Microsoft Word, you can specify sections of the found term, and then use them in the replacement.

For example, (John) (Smith) replaced by \2 \1 will produce Smith John or replaced by \2 alone will give Smith.

Is there a similar functionality in OpenOffice?

Thanks.

---

### Post by gmargo on 2010-04-25
Yes.  In the "Find & Replace" dialog, click the "More Options" button and check the "Regular expressions" box.  Now use "$2$1" in the "Replace with" field for the positional matches.  You can use the backslash form to reuse matches in the "Search for" box.

---

### Post by uzd4ce on 2010-04-25
Great thanks.  

And do I set up positions in the find term by wrapping them in parentheses like in Word?

Thanks

Edit:  Here's an example of what I'm trying to do.  Say in my doc I've got 

[[w:example1]
[[w:example2|with pipe]]
[[w:example3]]

I want to only replace the close brackets in the terms that do not already have a pipe, in this case, example 1 and 2, with |]]

I know the correct find term to find the ones without a pipe, but I don't know how to use the positional matches thing

---

### Post by gmargo on 2010-04-25
Is your example 1 text correct, with only a single closing bracket?  I'll ignore that one for now.  

To match [[....]] without a pipe within,

search for:
(\[\[[^|]+)(\]\])

replace with:
$1|$2

---

### Post by uzd4ce on 2010-04-25
Yeah, I forgot a bracket on example 1.

I get everything you said, but what does the + do in your find term?

---

### Post by gmargo on 2010-04-25
Plus (+) in regular expressions generally means "one or more".  The plus was after the character class "[^|]", which means "not-pipe".  So the combined expression "[^|]+" means "one or more not-pipe characters."

---

