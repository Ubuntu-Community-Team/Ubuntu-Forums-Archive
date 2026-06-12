---
title: "Help with sed regular expressions"
date: 2010-03-04
forum: General Help
---

### Post by chris_l_13 on 2010-03-04
Hi,

I need to pick out the "domU-12-31-39-09-35-97.compute-1.internal" part from this string and am having trouble doing it with sed.

```
INSTANCE    i-81f621ea    ami-db9a76b2    ec2-72-44-54-233.compute-1.amazonaws.com    domU-12-31-39-09-35-97.compute-1.internal    running    chriskey    0    7866F6BD    m1.small    2010-03-04T16:38:06+0000    us-east-1c    aki-6eaa4907    ari-42b95a2b    
```After reading online documents regarding sed I made this regex:
```
's/\(\.*\tdomU-\w+\t\.*\)/\1/g'
```However this doesn't work.

Please help me! Thanks in advance!

Chris

---

### Post by Agent ME on 2010-03-04
Using sed with a regular expression of the form "s/.../,,,/g" performs a search and replace operation over a block of text (replacing ... with ,,,).

Your regex 's/\(\.*\tdomU-\w+\t\.*\)/\1/g' has a few problems.

The \1 in the replacement part is interpreted to be the same as the first ( ) block. The idea of that regex is to match the whole line, encapsulate the wanted section inside the parentheses, and then replace the whole line with just the wanted section. But the parentheses are located in the wrong places here, causing the entire line to (possibly) be matched, and then replaced with the same thing.

'\w+' will not match the '-' or '.' symbols that are in the string you're trying to match. Also, the '+' needs to be escaped to have meaning. You want '[0-9a-z.-]\+'.

You don't want to escape the periods with backslashes, or else they lose their meaning.

This command will work (followed by your file's name or used with a pipe):
```
sed 's/^.*\t\(domU-[0-9a-z.-]\+\)\t.*$/\1/g'
```

Though because you're not really doing search-and-replace, but just finding a matching string, I'd recommend using grep:
```
grep -o '\bdomU-[0-9a-z.-]\+\b'
```
The -o option is so that it only returns the matching part of the input. The two '\b' sequences mean to only match at word boundaries.

---

### Post by gmargo on 2010-03-04
> **chris_l_13 said:**
> I need to pick out the "domU-12-31-39-09-35-97.compute-1.internal" part from this string and am having trouble doing it with sed.

The right tool for the right job?
```

awk '{print $5;}'

```

---

