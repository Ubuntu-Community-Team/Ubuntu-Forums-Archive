---
title: "symbolic link not doing what expected"
date: 2009-10-01
forum: General Help
---

### Post by yogourta on 2009-10-01
I'm trying to do a soft link but it creates the link inside the destination folder. 

if I do : ln -s ~/www ~/htdocs it will create www -> /home/alex/www inside the htdocs folder.

I'm using ubuntu 9.04

---

### Post by bruno9779 on 2009-10-01
I can't understand what you want to link to what.

please write the full paths and explain a bit more.

---

### Post by bruno9779 on 2009-10-01
Let's see if i can figure it out.

What your command says is:

ln -s(create softlink) ~/www (of ~/www) ~/htdocs (inside ~/htdocs)

so, it does what you are telling it to.

---

### Post by unutbu on 2009-10-01
Normally,
```

ln -s ~/www ~/htdocs

```
would create a symlink from ~/htdocs --> ~/www. 

But if a ~/htdocs directory already exists, then you get a symlink from ~/htdocs/www --> ~/www.

If you wish ~/htdocs to be a symlink, then you have to remove the ~/htdocs directory first.

---

### Post by Giblet5 on 2009-10-01
Let me see if I understand what you're saying.

You have a folder named $HOME/www and you want to symbolically link that folder to $HOME/htdocs -- is that correct?

In order for it to do what you expect:
A) $HOME/htdocs must NOT exist
B) $HOME/www must exist

If ~/htdocs exists, then ~/www will be linked to ~/htdocs/www.

If ~/htdocs does not exist, then ~/www will be linked to ~/htdocs.

That's just how it works.

Or, maybe I misunderstood.

---

### Post by yogourta on 2009-10-01
I'm trying to link /home/alex/www to /home/alex/htdocs 

when I type : "ln -s /home/alex/www /home/alex/htdocs" Do I expect to have the link inside /home/alex like this : "www -> htdocs" ?

instead the link is created inside /home/alex/htdocs like this : "www -> /home/alex/www"

---

### Post by unutbu on 2009-10-01
To create a symlink from ~/www --> ~/htdocs, try
```

ln -s ~/htdocs ~/www
```

The general form of the command is 

```

ln -s EXISTING-DIRECTORY SYMLINK
```

---

### Post by yogourta on 2009-10-01
Ok I got it now than you very much.

I thought that I have to create both folders. 

Thank you again

---

### Post by laceration on 2009-10-01
I think an easier way make symlinks and save yourself some possible confusion is to right click a folder or file in Nautilus and select make link.  Then you can rename it and copy and paste it wherever you want

---

