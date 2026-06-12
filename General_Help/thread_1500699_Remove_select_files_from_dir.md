---
title: "Remove select files from dir"
date: 2010-06-03
forum: General Help
---

### Post by SOG420 on 2010-06-03
[RIGHT][/RIGHT]So I'm trying to remove  or move any files that are not mp3 or ogg from my music folder with the command rm -r *.jpg 
and I keep getting the message that:
rm: cannot remove `*.jpg': No such file or directory
{I'm trying to remove jpegs} any help would be appreciated

---

### Post by ThesaurusRex on 2010-06-03
> **SOG420 said:**
> [RIGHT][/RIGHT]So I'm trying to remove  or move any files that are not mp3 or ogg from my music folder with the command rm -r *.jpg 
and I keep getting the message that:
rm: cannot remove `*.jpg': No such file or directory
{I'm trying to remove jpegs} any help would be appreciated

Be very careful when removing multiple items at once. The command you used without the -r should work. Make sure you're in the proper directory.

---

### Post by SOG420 on 2010-06-03
Will be careful. Is there any way to remove all but XXXX file type?

---

### Post by ThesaurusRex on 2010-06-03
I know there is, but I'm not certain of the syntax. I believe using *.jpg is just using regular expressions, so if you simply put a "not" in front of the expression ('!', I think), it should rm all files that don't match.

---

### Post by SOG420 on 2010-06-03
In Case anyones ever wondering this command 
find . -name *.xxx -exec rm -rf {} \;
removed all file types of xxx type

---

