---
title: "Color Text Editor?"
date: 2010-05-11
forum: General Help
---

### Post by klausner on 2010-05-11
Is there a simple text editor for Linux that will let you color or highlight text on demand? Something like gedit or leafpad with color? I know I can probably do this with vi or emacs, but I'm looking for something _*simple*_, need not be feature rich.

---

### Post by dantalion23 on 2010-05-14
I use vi and am searching for a way to turn off the colour!

I've just played with gedit and under the view menu there is a highlight option which allows you to turn on colour highlighting in various programming languages, latex, html etc.

---

### Post by r_s on 2010-05-14
For switching off colour in vim , you need to change .vimrc , the settings of this file is imported every time you execute a *vi file* command.

---

### Post by mcduck on 2010-05-14
Do you mean syntax highlighting, or actually creating text doucuments with colored text? In the first case pretty much any text editor will do the trick, but the later case is a bit more problematic.

The thing is that text files don't support any colors. It's just plain text without any formatting. So if you want to save a file with colored text, you'll have to use some other type of document instead. Most people go for .odt, .rtf or .doc, and to make those you need to use a word processor (like OpenOffice or Abiword), not a text editor.

If you really want to create a document with colored text using a text editor, you'll have to use something like HTML to add the formatting (and colors) to the document.. :)

(The simple answer is that text editors won't do the trick, you need a word processor, and Abiword is probably the on you should try if you want a lightweight app.)

---

### Post by klausner on 2010-05-14
> **mcduck said:**
> The simple answer is that text editors won't do the trick, you need a word processor, and Abiword is probably the on you should try if you want a lightweight app.

Thanks. Should have thought it through, and it would have been obvious.

---

