---
title: "Weird Line Break Character?"
date: 2009-07-17
forum: General Help
---

### Post by Teasdale on 2009-07-17
I hope somebody knows what I'm talking about . . .

Sometimes I see a weird square image in text where a special character couldn't be identified. 

I'm trying to edit plain text documents in Leafpad and when I click "replace" and paste in a line break, this is the character that it displays. I suspect that this is a hard line break, and I've seen another one that I suspect is a soft line break.

Is there a place that shows/lists and identifies these characters?

I tried to attach a tiny image of the character. It looks like a square with three O's and an A inside it.

This isn't idle curiosity; texts that I'm converting to pdb are stripping line breaks and I suspect that I may need to replace this one with the other one, but I don't know how.

---

### Post by jonobr on 2009-07-18
Was this file copied from a windows dos enviroment or similar?

I thinks its the diff between dos LFs and Linux ones,

Theres a util called dos2unix or tofrodos in the repos if it is this issue

heres the info on tofro

> DOS text files traditionally have CR/LF (carriage return/line feed) pairs
as their new line delimiters while Unix text files traditionally have
LFs (line feeds) to terminate each line.

Tofrodos comprises one program, "fromdos" alias "todos", which converts
text files to and from these formats. Use "fromdos" to convert DOS
text files to the Unix format, and "todos" to convert Unix text files
to the DOS format.

This functionality is also available via the dos2unix/unix2dos symlinks.

---

### Post by kaibob on 2009-07-18
> **Teasdale said:**
> Is there a place that shows/lists and identifies these characters?

I believe it's the new line character. See the ASCII man page for a list of these.

---

### Post by lisati on 2009-07-18
I've occasionally seen a similar graphic for other "special" characters.

As well as the DOS2UNIX tool previously mentioned, there's one of my own efforts to achieve a similar effect here: [http://ubuntuforums.org/showpost.php?p=7435161&postcount=5](http://ubuntuforums.org/showpost.php?p=7435161&postcount=5) (it doesn't handle the MAC CR-only convention, but it shouldn't be too hard to add it in)

---

### Post by Teasdale on 2009-07-18
> **jonobr said:**
> Was this file copied from a windows dos enviroment or similar?

It was copied from a Leafpad file on my Ubuntu system.

I looked at the ASCII page and saw this: "users are expected to type a carriage return (enter key) between each paragraph. Formatting settings, such as first-line indentation or spacing between paragraphs, take effect where the carriage return marks the break. A non-paragraph line break, which is a soft return, is inserted using shift-enter or via the menus..."

But both methods yield the same character/image when I try to "replace" in Leafpad. So I'm totally stumped as to why the online file converter  sometimes strips the line break and sometimes doesn't. Maybe my source .txt file types are different, even though I'm working with them all in Leafpad - something to do with the character encoding option. All my old Notepad files work fine, but some new files that I'm creating in Leafpad end up with line breaks stripped when they convert to pdb.

---

### Post by Teasdale on 2009-07-18
> **Teasdale said:**
> Maybe my source .txt file types are different, even though I'm working with them all in Leafpad - something to do with the character encoding option.

That could be logical - I guess I need to google the difference between ISO-8859-15, CP1252, current locale (UTF-8 ), etc.

---

