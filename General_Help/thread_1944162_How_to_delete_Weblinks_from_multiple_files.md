---
title: "How to delete Weblinks from multiple files"
date: 2012-03-20
forum: General Help
---

### Post by SupaDupaNooB on 2012-03-20
Hi,
I need to delete a weblink say "http://www.example.com/abc/xyz/" from multiple files in a folder.

I've tried with **sed**. 
Which can delete words in multiple files like this: *sed -i 's/text-to-remove//g' *html*

But it doesn't work with a weblink:
*sed -i 's/http://www.example.com/abc/xyz//g' *html*
Results:
sed: couldn't open file ww.example.com/abc/xyz//g: No such file or directory

Note: The weblink is more than once in each file. All need to removed.

Any idea how to do it? Doesn't need to be **sed**.

Thanks.

---

### Post by Habitual on 2012-03-20
I don't think you can wildcard *html like that and I'd suggest sed -e first as a non-invasive test (kind of like a simulation) and give it an actual /path/to/file.html and you have to escape the "/", "&", and "?" metacharacters..

```

cat habitual.html
http://www.example.com/abc/xyz
http://www.example.com/abc/xyz
http://www.example.com/abc/xyz
Habitual was here.
http://www.example.com/abc/xyz

[COLOR=Red]sed -e 's/http:\/\/www.example.com\/abc\/xyz/http:\/\/www.domain.com/g' habitual.html [/COLOR]

http://www.domain.com
http://www.domain.com
http://www.domain.com
Habitual was here.
http://www.domain.com

cat habitual.html
http://www.example.com/abc/xyz
http://www.example.com/abc/xyz
http://www.example.com/abc/xyz
Habitual was here.
http://www.example.com/abc/xyz

[COLOR=Red]sed -i 's/http:\/\/www.example.com\/abc\/xyz/http:\/\/www.domain.com/g' habitual.html  [/COLOR]

cat habitual.html
http://www.domain.com
http://www.domain.com
http://www.domain.com
Habitual was here.
http://www.domain.com

```HTH.

Edit: This code will remove **all** occurrences of "http://www.example.com/abc/xyz" in a/the file(s).

Edit2: easier replacement for example string.

---

### Post by SupaDupaNooB on 2012-03-21
That works!
Thank you. :)

---

### Post by Habitual on 2012-03-21
You are very welcome.
Glad it worked out.

---

