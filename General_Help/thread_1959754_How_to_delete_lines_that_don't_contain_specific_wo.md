---
title: "How to delete lines that don't contain specific words with global ex?"
date: 2012-04-16
forum: General Help
---

### Post by Rytron on 2012-04-16
Hi.

I just read this article.
Delete Lines that Doesn’t Contain Specific Words with Notepad++ 
[http://www.raymond.cc/blog/delete-lines-that-doesnt-contain-specific-words-with-notepad/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+RaymondccBlog+%28Raymond.CC+Blog%29](http://www.raymond.cc/blog/delete-lines-that-doesnt-contain-specific-words-with-notepad/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+RaymondccBlog+%28Raymond.CC+Blog%29)

I noticed the line '**Linux users can easily delete lines that doesn’t contain specific words by using the global ex command but unfortunately we need a software to do that in Windows.**'
How would this be done?

Thanks.

---

### Post by dragonfly41 on 2012-04-16
Run a linux utility on cygwin?

[http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by Rytron on 2012-04-16
> **dragonfly41 said:**
> Run a linux utility on cygwin?

[http://www.cygwin.com/](http://www.cygwin.com/)

No, I'd presume it is a native GNU/Linux feature.

---

### Post by dragonfly41 on 2012-04-16
Sorry .. I misunderstood .. thought you wanted to run linux functions in windows.

Does this thread help ..

[http://stackoverflow.com/questions/614654/linux-removing-files-that-dont-contain-all-the-words-specified](http://stackoverflow.com/questions/614654/linux-removing-files-that-dont-contain-all-the-words-specified)

---

### Post by Rytron on 2012-04-18
> **dragonfly41 said:**
> Sorry .. I misunderstood .. thought you wanted to run linux functions in windows.

Does this thread help ..

[http://stackoverflow.com/questions/614654/linux-removing-files-that-dont-contain-all-the-words-specified](http://stackoverflow.com/questions/614654/linux-removing-files-that-dont-contain-all-the-words-specified)

I gleaned these from that site:

This will remove all files that doesn't contain words **Ping** or **Sent**
# File names must have no spaces
```
grep -L 'Ping\|Sent' * | xargs rm
```

# If a file does not contain foo, then it will be deleted.
```
grep -L foo *.txt | xargs rm
```

Those are similar but do not remove lines from within a file but rather remove files that don't contain certain words (although that is also useful).

---

### Post by HiImTye on 2012-04-18
you could use something like
```
grep -v "undesired string" /your/file > tmp
```and once you know your file is as desired
```
mv tmp /your/file
```

---

### Post by dragonfly41 on 2012-04-18
I'm not sure if **[COLOR=DarkSlateBlue]recoll[/COLOR]** (advanced search) might help you.

You'll find this in Synaptic Package Manager.

See screenshot of recoll.

---

### Post by Rytron on 2012-04-18
> **dragonfly41 said:**
> I'm not sure if **[COLOR=DarkSlateBlue]recoll[/COLOR]** (advanced search) might help you.

You'll find this in Synaptic Package Manager.

See screenshot of recoll.

That is perfect!

---

### Post by Rytron on 2012-04-18
> **HiImTye said:**
> you could use something like
```
grep -v "undesired string" /your/file > tmp
```and once you know your file is as desired
```
mv tmp /your/file
rm tmp
```

Nice one! ):P

---

### Post by HiImTye on 2012-04-18
my bad, I misread, that will remove lines that contain those words. take out the -v and it will be the behaviour you want
```
grep "desired string" /your/file > tmp
```

and remember that any line that doesn't contain that will be removed, so make sure your string is as specific as possible to avoid collisions

---

### Post by Rytron on 2012-04-18
> **HiImTye said:**
> my bad, I misread, that will remove lines that contain those words. take out the -v and it will be the behaviour you want
```
grep "desired string" /your/file > tmp
```

and remember that any line that doesn't contain that will be removed, so make sure your string is as specific as possible to avoid collisions

But it copied the line with the undesired string into a file named 'tmp' (and left it in the text file). How could you get it to delete the line containing the undesired string from the text file?

---

### Post by HiImTye on 2012-04-18
```
grep "desired string" /your/file > tmp
```will copy your current file, into a new file 'tmp', with only the lines[COLOR=PaleGreen] [COLOR=DarkGreen]that contain[/COLOR][/COLOR] your "[COLOR=DarkGreen]desired string[/COLOR]"
```
grep -v "undesired string" /your/file > tmp
```will copy your current file, into a new file 'tmp', with only the lines [COLOR=DarkRed]that don't contain[/COLOR] your "[COLOR=DarkRed]undesired string[/COLOR]"

once you have the output you want, replace your old file, with the new file
```
mv tmp /your/file
```

---

### Post by Rytron on 2012-04-18
> **HiImTye said:**
> ```
grep "desired string" /your/file > tmp
```
will copy your current file, into a new file 'tmp', with only the lines that contain your "desired string"
```
grep -v "undesired string" /your/file > tmp
```
will copy your current file, into a new file 'tmp', with only the lines that don't contain your "undesired string"

once you have the output you want, replace your old file, with the new file
```
mv tmp /your/file
```

I see. Thank you HiImTye.

---

### Post by HiImTye on 2012-04-18
you're welcome, please [mark as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by Rytron on 2012-04-18
> **HiImTye said:**
> you're welcome, please [mark as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Just a quick question - What is **global ex**?

---

### Post by HiImTye on 2012-04-18
ex is a utility

---

### Post by sudodus on 2012-04-18
> **Rytron said:**
> Just a quick question - What is **global ex**?
I think they meant the old line editor ex (from unix). Today it is emulated by vim, see
```
man ex
``` or ```
man vim
```

---

### Post by Rytron on 2012-04-18
> **sudodus said:**
> I think they meant the old line editor ex (from unix). Today it is emulated by vim, see
```
man ex
``` or ```
man vim
```

Cheers guys.):P

---

