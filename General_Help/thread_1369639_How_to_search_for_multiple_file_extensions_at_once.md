---
title: "How to search for multiple file extensions at once in Gnome"
date: 2010-01-01
forum: General Help
---

### Post by mtinman on 2010-01-01
Does anyone know of a way to perform a search for multiple file extensions at once in Gnome? I know that M$ Windows Explorer had this capability, but I'm just not sure how to do it in Gnome, or if it's possible. I just want to be able to perform searches for Video, Music, and Document file types, without having to perform a separate search for each file extension. Example: When doing a search for Video file types (.avi,.mp4,.mov,.wma, etc.), I would like to do one search for all files that have these file extensions, instead of doing one search for .avi files, a second search for .mp4 files, another for .mov files, etc. If anyone can help, please let me know, and thanks in advance!

---

### Post by s.fox on 2010-01-01
Hello,

I found [this]("http://ubuntuforums.org/showthread.php?t=576081") in the archives.   Looks like it does a similar thing to what you are trying to achieve through the terminal.  Not sure if you can do it by other means.

-Silver Fox

---

### Post by SuperSonic4 on 2010-01-01
> **Silver_fox_ said:**
> Hello,

I found [this]("http://ubuntuforums.org/showthread.php?t=576081") in the archives.   Looks like it does a similar thing to what you are trying to achieve through the terminal.  Not sure if you can do it by other means.

-Silver Fox

This would be your best bet in GNOME.

Dolphin can do it in much the same way explorer can

---

### Post by zine92 on 2010-01-01
Hey, i am also new to linux and especially ubuntu. Anyway i found this, [HTML]http://software.twotoasts.de/index.php?/pages/catfish_summary.html[/HTML]. Anyway that is for your reference. to install you just go to your applications -- Ubuntu Software Center then search for the package catfish. Hope that helps. But multiple files.

---

### Post by kaibob on 2010-01-01
> **mtinman said:**
> Does anyone know of a way to perform a search for multiple file extensions at once in Gnome? I know that M$ Windows Explorer had this capability, but I'm just not sure how to do it in Gnome, or if it's possible.

You specify gnome, so I assume you mean the GUI search tool. This utility supports regex by way of the "Name matches regular expression" option. I'm not knowledgeable about regex, but the following does appear to work. Just change the extensions to whatever is appropriate. 

```
.*pdf|.*odt|.*txt
```

---

### Post by zine92 on 2010-01-01
My apologies, anyway, i found another useful piece of small software in the Ubuntu Software Center, which is called the searchmonkey. fast results and in the box that says containing just type the sort of extension, e.g. ogg and mp3, just type .mp3, .ogg and specify the right folder to be right. Hope that helps too.

---

### Post by mtinman on 2010-01-01
Thanks for the quick feedback, everybody! I really appreciate it... kaibob, are those pipe symbols between the file extensions? Also, thanks Silver_fox_, that was a good suggestion, find is adequate, and locate seems to work pretty damn quick!

Happy New Year!

---

### Post by kaibob on 2010-01-01
> **mtinman said:**
> kaibob, are those pipe symbols between the file extensions?

Yes, it's a pipe symbol or vertical bar. I'm not sure as to the correct terminology in this context. 

BTW, it would be better to precede the extensions with a period to prevent search from finding files that end in say txt but are not text files (admittedly an unlikely event). Anyways I tried to escape the period, but it didn't work.

---

### Post by mtinman on 2010-01-02
I figured it out, using gnome-search-tool, and creating a Name matches regular expression option with the following regex syntax: ```
.*pdf|.*odt|.*txt
```

I will attach a screen shot for anyone interested.

Hope this helps someone else, and again, thanks to everyone who helped me with this!

:guitar:

---

