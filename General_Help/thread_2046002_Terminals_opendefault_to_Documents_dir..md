---
title: "Terminals open/default to Documents dir."
date: 2012-08-22
forum: General Help
---

### Post by scottr99 on 2012-08-22
Hi all,

I am using KDE 4.9, which I installed over Ubuntu 12.04.

I have use three different terminals: Sakura, Konsole, and one that is available through Cairo-Dock.

Regardless of which one I open, it will open as the default directory Documents.  Which is annoying because I usually kick off shell scripts from my home directory so I have to type 'cd-enter' every time.

Has anyone ever seen this or know how to fix it to default to my home dir?

Thanks.

---

### Post by spjackson on 2012-08-22
Ah, KDE 4.9. I hadn't gathered that from your [previous thread]("http://ubuntuforums.org/showthread.php?t=2045279"). I haven't used KDE much for several years. It appears to be a [feature of KDE 4.9]("https://bugs.kde.org/show_bug.cgi?id=302903"). I can't really help with that at the moment.

---

### Post by scottr99 on 2012-08-22
Oh I didn't think it made a difference.  I guess I'll have to live with it.  But thanks anyway! :)

---

### Post by vasa1 on 2012-08-22
> **scottr99 said:**
> Oh I didn't think it made a difference.  I guess I'll have to live with it.  But thanks anyway! :)
If you post the contents of your .bashrc someone may have something to suggest.

---

### Post by era86 on 2012-08-22
> **vasa1 said:**
> If you post the contents of your .bashrc someone may have something to suggest.

This. If you put:

[PHP]cd ~[/PHP]

at the end of your .bashrc maybe? I haven't confirmed, but this should change directory to home when a terminal starts.

---

### Post by conradin on 2012-08-22
.bashrc might not have the home path in it. I think bashrc assumes its running from the home directory of a user. 

so, what I want to see is the output of ```
echo $HOME

```

---

### Post by bodhi.zazen on 2012-08-22
> **era86 said:**
> This. If you put:

[PHP]cd ~[/PHP]

at the end of your .bashrc maybe? I haven't confirmed, but this should change directory to home when a terminal starts.

This is an excellent suggestion.

Perhaps another would be to put your scripts in ~/bin

If you put them in ~/bin, they will be on your path, and you can then call them from anywhere, as you would with any other command.

---

