---
title: "How to make a bookmark in a djvu file?"
date: 2010-07-02
forum: General Help
---

### Post by gabe1986 on 2010-07-02
Hi there!! I wish somebody could give a response because I have searched everywhere and I haven't found a good answer :-(

And the question is that of the title of this post. What happens is that I like the djvu format (a lot!), and I'd like to export all my pdf books (I'm studying the university and I have a lot of pdf books) to djvu format.

The problem is that I found very uncomfortable to read a djvu book (with hundreds of pages) without the help of bookmarks or index.

I have found some djvu files with bookmarks and that's why I believe that there is a way to do this.

I found an application called djvubookmarker on sourceforge.net , but this application only works on Windows OS (and doesn't work really good, it has some bugs) so I haven't used wine to use this application with my Ubuntu.

Thank you in advance to everybody.

I'll be waiting for you answer.

---

### Post by nbubis on 2010-07-17
Hi,

There's a program called "djvused" that you can use.
To install type:

```
sudo apt-get install djvulibre-bin
```

I admit I haven't quite managed to get a hang of it yet, if you do, please post back.

---

### Post by nbubis on 2010-07-17
Ok - so this is how it's done:

After installing "djvused", you create a text file with your bookmarks in the following format, where the numbers are the page numbers you see in evince:
```

(bookmarks
("Title" "#1")
("My Chapter 1" "#5"
("Sub Chapter 1" "#5")
("Sub Chapter 2" "#15"))
)
```

Say you saved the file as "bookmarks.txt", you then run:

```
djvused file.djvu -e 'set-outline bookmarks.txt' -s
```

Note that this will override any previous bookmarks.

Hope this helped ;)

---

### Post by gabe1986 on 2010-09-14
I hadn had time to answer before. Thank you very much!, I&#314;l try to use this program and I&#314;l tell you later if it works.

Thank you very much again.

Gabriel

P.S. Sorry if my english isn't really good, but I'm not a native speaker.

---

