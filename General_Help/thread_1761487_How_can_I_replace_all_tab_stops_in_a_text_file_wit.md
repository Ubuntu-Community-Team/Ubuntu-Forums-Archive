---
title: "How can I replace all tab stops in a text file with 4 spaces?"
date: 2011-05-18
forum: General Help
---

### Post by guest_user on 2011-05-18
can anybody help?
and how can I make vi and nano such that when I press the tab key, it automatically replaces the tab with 4 spaces?

---

### Post by garyweigh on 2011-05-18
There are three ways to fix this problem: 
&#8226;    Manually replace the multiple space characters with tabs.
&#8226;    Use several Find and Replace tasks, which is a bit faster than doing it manually.
&#8226;    Use one Find and Replace task to replace each instance of multiple space characters with a single tab character. 
I know which one I&#8217;d choose! To replace multiple and consecutive spaces with a single tab character, do the following: 
1.    Choose Replace from the Edit menu (or press [Ctrl]+H) to open the Find And Replace dialog box. 
2.    Click the More button.
3.    In the Find What text box, enter one space character and the following characters, exactly as shown: {2,}. 
4.    In the Replace With control, enter ^t.
5.    Check the Use Wildcards option.
6.    Click Replace All. 
7.    Click Close.
The {2,} component tells Word to find two or more of the literal character, which in this case is a space character. You could use this component to find other multiple characters.


[Fastest MP3 Blog]("http://fastestmp3.blogspot.com/")

---

### Post by benson444 on 2011-05-18
I don't know about vi but I wanted to do the same thing in vim and found [_this_]("http://vim.wikia.com/wiki/Converting_tabs_to_spaces")

---

### Post by guest_user on 2011-05-18
> **garyweigh said:**
> There are three ways to fix this problem: 
•    Manually replace the multiple space characters with tabs.
•    Use several Find and Replace tasks, which is a bit faster than doing it manually.
•    Use one Find and Replace task to replace each instance of multiple space characters with a single tab character. 
I know which one I’d choose! To replace multiple and consecutive spaces with a single tab character, do the following: 
1.    Choose Replace from the Edit menu (or press [Ctrl]+H) to open the Find And Replace dialog box. 
2.    Click the More button.
3.    In the Find What text box, enter one space character and the following characters, exactly as shown: {2,}. 
4.    In the Replace With control, enter ^t.
5.    Check the Use Wildcards option.
6.    Click Replace All. 
7.    Click Close.
The {2,} component tells Word to find two or more of the literal character, which in this case is a space character. You could use this component to find other multiple characters.


[Fastest MP3 Blog]("http://fastestmp3.blogspot.com/")

is it possible to use sed or awk to do a global replace?

---

### Post by Toz on 2011-05-18
> **guest_user said:**
> is it possible to use sed or awk to do a global replace?

```
cat file | sed -e 's/\t/    /g'
```

---

### Post by Toz on 2011-05-18
> **guest_user said:**
> 
and how can I make vi and nano such that when I press the tab key, it automatically replaces the tab with 4 spaces?

For vi:
[http://www.tech-bits.com/index.php/CategoryID/6/EntryId/24/entry](http://www.tech-bits.com/index.php/CategoryID/6/EntryId/24/entry)

For nano, start it like:```
nano -T 4
```

---

