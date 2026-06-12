---
title: "What the vi escape syntax is to select something inside a parenthesis"
date: 2011-11-30
forum: General Help
---

### Post by rocksockdoc on 2011-11-30
I have a long file containing thousands of lines of the format:
• ANY NUMBER OF WORDS (ACRONYM)

I'm trying to get the vi syntax correct to bring the abbreviation to the front, as in:
• ACRONYM = ANY NUMBER OF WORDS

For example, from:
• THREE LETTER ACRONYM (TLA)
To:
• TLA = THREE LETTER ACRONYM

I'm having trouble with escaping parenthesis in vi commands.
For example, I know of \(stuff\) \(more stuff\) type selections and then rearranging those two selections as &1 and &2 ... but I'm having trouble escaping the parenthesis in the original text.

I did try double escaping them, but failed syntactically. 
For example:
:%s/\(^.*(\)\(.*$\)/&2=&1/

This failed but the 'intention was'
:% ==> the whole file
s/ ==> search for
\(^.*(\) ==> take the whole line up to the first parenthesis as the first variable
\(.*$\) ==> take the rest of the line after the first parenthesis as the second variable
/ ==> then 
&2=&1 ==> put the second thing found in front of the first found separated by an equal sign
/ ==> done

Since these attempts failed, may I ask what the syntax is to select something inside a parenthesis at the end of a sentence and bring it to the front of the sentence?

---

### Post by erind on 2011-11-30
This seems to work,

```
  %s/\(.*\)(\(.*\))$/\2 = \1/

```PS. For complex replacement I find tools such as sed, awk, perl, etc, easier to work with.

---

### Post by rocksockdoc on 2011-11-30
> **erind said:**
> 
```
  %s/\(.*\)(\(.*\))$/\2 = \1/

```

It worked like a charm!
:% ==> for the entire file
s/ ==> search for 
\(.*\) ==> any character, and any number of them as variable 1
( ==> and then an open parenthesis
\(.*\) ==> and any character, and any number of them as variable 2
)$ ==> a closing parenthesis at the end of the line
/ ==> replace that with
\2 = \1/ ==> the second thing you found, space, equal, space, the first thing you found
/ ==> done

Thank you very much! In hindsight, I was close ... but, ever so far away because I had the syntax wrong in more than one spot! 

Thanks for setting me straight. I have to remember this one!

---

