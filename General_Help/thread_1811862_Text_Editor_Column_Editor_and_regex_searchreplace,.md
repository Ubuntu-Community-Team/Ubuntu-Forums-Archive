---
title: "Text Editor Column Editor and regex search/replace, incrementing number insert"
date: 2011-07-25
forum: General Help
---

### Post by xekon on 2011-07-25
On windows I really only used Notepad++ as my text editor, it had two features that I loved.

What I need to accomplish is what I would do with Notepad++ column editor.

I could have like 100 lines, and place the cursor at a column, and goto edit>column editor, and I could insert an incrementing number. (I could also pad the incrementing number with 0s, this was GREAT for making batch files among other things.)

So each line at that column had a number higher than the previous line.

The other feature that I used sometimes was a search/replace with regex patterns.

Does anyone know of an editor that has those features for linux? I am mostly after the column editor insert feature but if you know of one with both features that would rock.

---

### Post by enimeizoo on 2011-07-25
Hello,
Two very popular code editors are emacs and vi(m). I use emacs, but I'm pretty sure what you are looking for is also doable with vim.
The regexp search can be performed with a shortcut. (not sure which one since I don't use the default for it, shortcuts are pretty easy to configure to fit your needs/habits.
As for the column insertion, I'm not aware it exists, but if it is a feature you use often, you can write a function to do it. The function would be pretty easy to write. You would need basic understanding of lisp to write it, though. I could help if you want.

Hope it helps!

(edit) Actually, it does exist. have a look [there]("http://stateofflux.com/2008/06/14/column-editing-with-emacs/").

---

