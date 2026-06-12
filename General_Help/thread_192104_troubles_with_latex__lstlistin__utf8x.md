---
title: "troubles with latex / lstlistin / utf8x"
date: 2006-06-08
forum: General Help
---

### Post by schilcha on 2006-06-08
Since upgrading to dapper, I cannot compile my latex-docs as under breezy. I include source-code into my beamer-class-based slides using lstlisting. However, code that conatins special characters raise error messages. 

Here's a minimalistic example:
```

\documentclass{article}

\usepackage[T1]{fontenc}
\usepackage{ucs}
\usepackage[utf8x]{inputenc}
\usepackage[german]{babel}
\usepackage{listings}

\begin{document}
  \lstinputlisting{code}
\end{document}

```
The included file *code* looks as follows:
```

# cömment with ümläüt

```
Finally, my latex-output is: 
```

[...]
(/usr/share/texmf/tex/latex/ucs/ucsencs.def) (./code

! Package utf8x Error: Malformed UTF-8 sequence.

See the utf8x package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.1 # cömment
               with ümläüt
? X
No pages of output.

```

Believe it or not, even after extensive search on the net, I couldn't find only the slightes hitn on how to deal with this problem. 

Any help is greatly appreciated!

---

### Post by sherlock-holmes on 2006-06-08
[QUOTE=schilcha]Since upgrading to dapper, I cannot compile my latex-docs as under breezy. I include source-code into my beamer-class-based slides using lstlisting. However, code that conatins special characters raise error messages. 

Here's a minimalistic example:
```

\documentclass{article}

\usepackage[T1]{fontenc}
\usepackage{ucs}
\usepackage[utf8x]{inputenc}
\usepackage[german]{babel}
\usepackage{listings}

\begin{document}
  \lstinputlisting{code}
\end{document}

```
The included file *code* looks as follows:
```

# cömment with ümläüt

```
Finally, my latex-output is: 
```

[...]
(/usr/share/texmf/tex/latex/ucs/ucsencs.def) (./code

! Package utf8x Error: Malformed UTF-8 sequence.

See the utf8x package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.1 # cömment
               with ümläüt
? X
No pages of output.

```

Believe it or not, even after extensive search on the net, I couldn't find only the slightes hitn on how to deal with this problem. 

Any help is greatly appreciated![/QUOTE]

did you try without that utf8x package....i mean a very simple one with no additional package invoked?

---

### Post by schilcha on 2006-06-09
Thanks for your suggestion!

I've tried to reduce the packages with the following results:

1) using *listings* only results in the following error:
[CODE]
[...]
(/usr/share/texmf-tetex/tex/latex/listings/listings.cfg)) (./test.aux

! Package babel Error: You haven't loaded the option german yet.

See the babel package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.3 \select@language{german}

? X
No pages of output.
Transcript written on test.log.
[/QUOTE]

2) adding package *babel*/german (as suggested in the previous error) gives a clean compilation, but results in a document without any special characters. 

3) adding *fontenc* replaces umlauts with cryptic combinations of characters 

4) adding *ucs* has no effect

5) finally, adding *utf8x* results in what I've described in my initial post

---

### Post by schilcha on 2006-06-09
RTFM!! Shame on me! 

Adding the line 
```

\lstset{inputencoding=utf8x, extendedchars=\true}

```
makes it work almost -- of course it's all in the manual.

BUT ONE QUESTION REMAINS:
Why, are words with umlauts scrambled in the output - i.e. all umlauts are gathered in the beginning of the word, followed by ordinary characters.

e.g. "hellö wörld" results in "öhell öwrld"

---

### Post by marteus on 2006-12-18
I have the same problem with scrambled words. Did you ever find a solution?

---

### Post by schilcha on 2006-12-18
Unfortunately no. I chose to work around that issue by avoiding offending characters (which is quite easily possible in german).

---

