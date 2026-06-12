---
title: "Search for an exact string in a Terminal"
date: 2010-10-22
forum: General Help
---

### Post by COKEDUDE on 2010-10-22
Is there hopefully a way to search for an exact string in Man Pages? I know if I want to search for anything containing -c I can just do this. 
```
/-c
```

How would I search for "-c"? I want only "-c" to show up. So I tried this. 
```
/"-c"
```
It took me literally and looked for the quotes also.

---

### Post by Miyavix3 on 2010-10-22
You can possibly use grep for what you need. It's a regular expression program.

You can do
```
man grep
```

or look up guides on the web.


But this is how you normally would use it:
Basically you run a command like you normally would, but you only want to filter out a specific line of text with your search pattern.
You can do this

```
cat file.txt | grep "the"
```

'cat' would normally output all of the file to the screen, but since we piped it into grep it just outputs the lines with the word "the" in them.

---

### Post by The Cog on 2010-10-22
I'm not sure what you're trying to do. For a start, if I enter **/-c** into a terminal, I get **bash: /-c: No such file or directory**. So I presume you are not just in the terminal, but running some program.

Secondly, if **/-c** searches for **-c** (like you say it does) then what are you searching for? 

Sorry, I don't really understand the question.

---

### Post by COKEDUDE on 2010-10-22
> **The Cog said:**
> I'm not sure what you're trying to do. For a start, if I enter **/-c** into a terminal, I get **bash: /-c: No such file or directory**. So I presume you are not just in the terminal, but running some program.

Secondly, if **/-c** searches for **-c** (like you say it does) then what are you searching for? 

Sorry, I don't really understand the question.

I'm looking at my man pages. When you go to the help pages it says something similar to this. 

>            SEARCHING

  /pattern          *  Search forward for (N-th) matching line.
  ?pattern          *  Search backward for (N-th) matching line.
  n                 *  Repeat previous search (for N-th occurrence).
  N                 *  Repeat previous search in reverse direction.
  ESC-n             *  Repeat previous search, spanning files.
  ESC-N             *  Repeat previous search, reverse dir. & spanning files.
  ESC-u                Undo (toggle) search highlighting.
  &pattern          *  Display only matching lines
        ---------------------------------------------------
        Search patterns may be modified by one or more of:
        ^N or !  Search for NON-matching lines.
        ^E or *  Search multiple files (pass thru END OF FILE).
        ^F or @  Start search at FIRST file (for /) or last file (for ?).
        ^K       Highlight matches, but don't move (KEEP position).
        ^R       Don't use REGULAR EXPRESSIONS.
 ---------------------------------------------------------------------------


---

### Post by The Cog on 2010-10-22
OK, man pages. But what are you searching for? **/-c** will find **-c**. No need to type quotes round it.

---

### Post by COKEDUDE on 2010-10-22
> **The Cog said:**
> OK, man pages. But what are you searching for? **/-c** will find **-c**. No need to type quotes round it.

I want only "-c" to show up. Without quotes I get:
```
-combine
-pass-exit-codes
-no-integrated-cpp
etc...
```

There has gotta be a way to get ONLY "-c" to show up.

---

### Post by The Cog on 2010-10-23
> **COKEDUDE said:**
> I want only "-c" to show up. Without quotes I get:
```
-combine
-pass-exit-codes
-no-integrated-cpp
etc...
```

There has gotta be a way to get ONLY "-c" to show up.

I you're looking for a line that only contains "-c", I don't think there's a way. And of course, that search would fail if there were a space before or after the -c. 

But I suspect you are looking for a line containing " -c " in which case typing ```
"/ -c "
``` (without the quotes but notice the space before and after the -c) will do the trick.

---

### Post by COKEDUDE on 2010-10-24
Perfect :). That does the trick :). Glad you pointed out to add the extra space. I didn't see that at first. 

This also does the trick. 
```
/[^a-z]-c[^a-z]
```

---

### Post by COKEDUDE on 2011-06-18
This also works :). 

```
/[^a-z]exec[^a-z]
```

---

