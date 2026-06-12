---
title: "What tool can I use to divide paragraphs into one word per line?"
date: 2010-03-27
forum: General Help
---

### Post by wersdaluv on 2010-03-27
I'm making a massive list of words that I use often (especially non-English ones) to add them on my Android Keyboard Dictionary. I found a tool called User Dictionary Manager. It imports words from a text file which has one word per line.

What tool on Ubuntu can I use to automate the process of splitting paragraphs into one word per line? I'm copying text written in my local language from different sources. I'd like to automate the process so I won't have to split them all manually.

---

### Post by HermanAB on 2010-03-27
sed and awk

Otherwise gedit has search and replace.  Basically, you need to search for spaces and replace them with newlines.

---

### Post by srix on 2010-03-27
You could try this quick and dirty method:
$ cat filename | tr " " "\n"

---

### Post by wersdaluv on 2010-03-27
> **HermanAB said:**
> sed and awk

Otherwise gedit has search and replace.  Basically, you need to search for spaces and replace them with newlines.

Thanks!

I got this nice code cat input_file.txt | perl -pe 's/(.+?)\b/\1\n/g' | perl -ne 'print if ! /^\s*$/' > output_file.txt

> **srix said:**
> You could try this quick and dirty method:
$ cat filename | tr " " "\n"

That's cool! That's like the code I got but shorter. How do I export the whole output to a file if I am to use this?

---

### Post by junapp on 2010-03-27
> **wersdaluv said:**
> 
I got this nice code cat input_file.txt | perl -pe 's/(.+?)\b/\1\n/g' | perl -ne 'print if ! /^\s*$/' > output_file.txt

That's cool! That's like the code I got but shorter. How do I export the whole output to a file if I am to use this?
same way you do with your perl output, use the greater than sign.
```

$ cat filename | tr " " "\n" > output_file.txt

```

---

