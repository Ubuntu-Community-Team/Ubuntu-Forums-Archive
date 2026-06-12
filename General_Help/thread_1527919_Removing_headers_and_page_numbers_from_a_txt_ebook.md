---
title: "Removing headers and page numbers from a txt ebook and retain formatting with vim"
date: 2010-07-09
forum: General Help
---

### Post by powerpleb on 2010-07-09
I have a text file of a book I want to read on an ereader. The problem is that within the file there are page numbers and headers that make it look like this:
```
... But then, getting into the heat of the work,

580

ANNA KARENINA

and seeing how diligently and zealously Veslovsky pulled the cart by the splash&#8211;board, so that he even broke it off...
```
So as you can see the header and page numbers break up sentences which makes it annoying to read.

I managed to use the find a replace tool in VIM to remove the page numbers and the header and join the lines together (If anyone is interested how I did it, let me know and I can post this. Although I admit that I probably did it in a very convoluted way). So now it looks like this:
```
... But then, getting into the heat of the work, seeing how diligently and zealously Veslovsky pulled the cart by the splash&#8211;board, so that he even broke it off...
```

But now it has joined some lines I didn't want joined (ie lines where a page break fell at the same place as a paragraph break). So some parts look like this (the XI being the number of the next section):
```
&#8216;A fine marsh! Veslovsky must have hampered you. It&#8217;s inconvenient for two with one dog,&#8217; said Stepan Arkadyich, softening his triumph.XI
When Levin and Stepan Arkadyich came to the cottage of the muzhik with whom Levin always stayed...
```

My question is: is there a way to use an if statement or something to ensure that it formats the book correctly.
For example, could I get vim (or something else for that matter) to check to see whether the line ends with a period or a quotation mark, and next line begins with a capital letter or another quotation mark and exempt those lines from the join command?

I am pretty inexperienced at scripting or using vim so any help at all would be most appreciated.

---

### Post by DaithiF on 2010-07-10
Hi, heres the replace command i would use:
```
:%s/\n\n[0-9]\+\n\nANNA KARENINA\n\n//
```

It should only remove those pagenumber / title lines, so it may leave the paragraph headers intact for you.

cheers

---

### Post by powerpleb on 2010-07-13
Thanks, that worked great!

---

