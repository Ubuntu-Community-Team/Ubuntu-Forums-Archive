---
title: "Redirecting stream on same file"
date: 2011-09-26
forum: General Help
---

### Post by Rekax on 2011-09-26
I everyone, I have conducted some researches on this subject, but I found nothing satisfying.

I am trying to correct a bad keystroke on a file using command line, just to learn:

I have a file 'bar' containing fou instead of foo, so I enter:
```
cat bar | sed -e "s/fou/foo/" > bar
```Of course it doesn't work because I am erasing the streamed file, bar is now empty.
The solution I found was this:
```
cat bar | sed -e "s/fou/foo/" > bar.tmp; mv bar.tmp bar
```but this is not elegant so I am asking if there is a way to block the stream until it is over somehow and THEN write it in the file?
It would be something like:
```
cat bar | sed -e "s/fou/foo/" SPECIAL_STOP_CHARACTER > bar
```I know it is against intrinsic streaming idea, but it would be useful...

Any Idea?

Thank you

A

---

### Post by nothingspecial on 2011-09-26
If I understand you correctly, just get rid of cat and the redirect.

```
$ less bar
foo
foo
fou
foo
foo

$sed -i 's/fou/foo/' bar
$ less bar
foo
foo
foo
foo
foo
```

---

### Post by sisco311 on 2011-09-26
See: BashPitfalls #13 and BashFAQ #21 (links in my signature).

As nothingspecial pointed it out in GNU sed (> 4.x) you can use the -i option.

sed is a stream editor. For editing files, I would use ed, a command based text editor, but there is nothing wrong with using sed...

[http://bash-hackers.org/wiki/doku.php?id=howto:edit-ed](http://bash-hackers.org/wiki/doku.php?id=howto:edit-ed)

---

### Post by nothingspecial on 2011-09-26
And in situations like this, I would do what sisco311 says.

---

### Post by Rekax on 2011-09-26
Thank you that's exactly what I was looking for!
Yes you are right, it is weird to edit stream on files when you can do it directly on the file.
Anyway thank you for the fast and accurate answers !

A

---

