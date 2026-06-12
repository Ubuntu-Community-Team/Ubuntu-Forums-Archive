---
title: "convert html to text on ubuntu"
date: 2011-12-04
forum: General Help
---

### Post by coffeecake on 2011-12-04
hello everyone. Does anyone know of a command line utility that runs on ubuntu that is able to convert a html file into text. It should only convert the text content of the html file into text. Not the whole file. I mean the html tags should not appear in final the text file.

---

### Post by mutley89 on 2011-12-04
It's called "html2text".

---

### Post by raja.genupula on 2011-12-04
use man page of it for more info 

**man html2text** and its a Command-line tool.

---

### Post by Lars Noodén on 2011-12-04
You can use either html2txt or [lynx](http://manpages.ubuntu.com/manpages/precise/en/man1/lynx.1.html)
```

lynx --dump *somefile.html*
lynx --dump *http://www.example.org/somefile.html*

```

---

