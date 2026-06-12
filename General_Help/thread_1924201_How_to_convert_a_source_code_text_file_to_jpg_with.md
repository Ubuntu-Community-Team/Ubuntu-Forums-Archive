---
title: "How to convert a source code text file to jpg with syntax highlight using bash?"
date: 2012-02-12
forum: General Help
---

### Post by Luca Borrione on 2012-02-12
I need to create images of the first page of some source code text files, like asp or php or js files for example.
I usually go on through this doing something as

```
enscript --no-header --pages=1 "${input_file}" -o - | ps2pdf - "${temp_pdf_file}"
convert -quality 100 -density 150x150 -append "${temp_pdf_file}"[0] "${output_file}"
trash "${temp_pdf_file}"

```
This works nice for my needs, but it obviously outputs an image "as is" with no "eye-candy" features. I was wondering if there's a way to add syntax highlighting too. This might come handy to speed up the creation of presentations of developed works for example

---

### Post by raja.genupula on 2012-02-12
[http://stackoverflow.com/questions/3938953/convert-source-code-to-syntax-highlighted-image](http://stackoverflow.com/questions/3938953/convert-source-code-to-syntax-highlighted-image)

may helps you a bit

---

### Post by Luca Borrione on 2012-03-23
Hello, thank you very much for your tip.
It's a very interesting link.

In the meanwhile I solved my problem using Pygments,
as suggested 
[here]("http://stackoverflow.com/questions/9248571/how-to-convert-a-source-code-text-file-e-g-asp-php-js-to-jpg-with-syntax-high").

However your link is full of information about this issue.
Very appreciated, thanks again.

---

