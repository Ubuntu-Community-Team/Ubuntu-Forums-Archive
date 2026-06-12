---
title: "Scripting question"
date: 2010-05-29
forum: General Help
---

### Post by plantboy1 on 2010-05-29
I'm trying to write a script to generate an html file (complete with formatting- echo "[random formatting]" >> index.html) for all the files in the given directory.

So far, it works pretty well.  HOWEVER, I want the listed files to be treated as links.  I'm using awk to grab the part of the filename I want, but I don't know how to do this out as it fails if there is more than one file.
The HTML side would look something like this:
```
<li><a href="2010.05.29.html">May 29</a></li>
```
It all works fine up to the actual number of the day- fine with one file, fails with more than one.  My code is this:
```

# Grabs all the files and puts them in a list with anchor text "Listed"
ls | find 2*.html | sed -e 's/^/<li><a href="/' \
-e 's/$/">Listed<\/a><\/li>/' >> index.html
# This is where it fails with more than one file:
less index.html | sed -e "s/Listed/`ls | find 2*.html | awk -F"[_|.]" '{print $3}' `/g" > TMP && mv TMP index.html
echo '</ul><br />' >> index.html
```

I don't know where to go from here or even if it's possible to do what I'm asking.

---

### Post by StuartN on 2010-05-29
> **plantboy1 said:**
> I'm trying to write a script to generate an html file (complete with formatting- echo "[random formatting]" >> index.html) for all the files in the given directory.

I do not understand your code.

Is there some reason why you could not simply use:

```
for file in * ; do
  echo "<li><a href=\"$file\">${file%.*}</a></li>"
done
```

---

### Post by plantboy1 on 2010-05-29
Thank you, I knew I was probably over-complicating it, that was almost exactly what I was looking for.

---

