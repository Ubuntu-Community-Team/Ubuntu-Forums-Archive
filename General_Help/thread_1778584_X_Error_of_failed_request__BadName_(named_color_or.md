---
title: "X Error of failed request:  BadName (named color or font does not exist)"
date: 2011-06-09
forum: General Help
---

### Post by ilSignorCarlo on 2011-06-09
Hi,
I'm trying to run Xcmodel, a 3D graphic environment developed in my university. When I run it I get this error:

```

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  45 (X_OpenFont)
  Serial number of failed request:  58
  Current serial number in output stream:  59
```

I don't really understand what this is about. I'm missing a font or what? If that's the case, what shall I install?

---

### Post by Toz on 2011-06-09
A possible solution from [http://www.dm.unibo.it/~casciola/php/public_html/projects/2004/tutorials/Guitar/relazione.html]("http://www.dm.unibo.it/~casciola/php/public_html/projects/2004/tutorials/Guitar/relazione.html") (translated):
> The first problem was a problem with the font used by XCModel: during use, in fact, found seemingly unexplained crashes, with messages to the console who acted more or less

X_OpenFont: bad font name
After some investigation, I discovered that on my system (Slackware Linux 9), the font server is not able to translate the string
-Adobe-helvetica-medium-o-normal - 18-*- 75-75-p-*- iso8859-1
in a font used, and this caused the crash. However, fortunately the string
-Adobe-helvetica-medium-o-normal - 18-*- 75-75-p-0-iso8859-1
is handled properly: this has allowed me to solve the problem directly by modifying the executable (with a hex editor) to replace the last * of the previous string with a 0 .

---

### Post by ilSignorCarlo on 2011-06-09
> **Toz said:**
> A possible solution from [http://www.dm.unibo.it/~casciola/php/public_html/projects/2004/tutorials/Guitar/relazione.html]("http://www.dm.unibo.it/~casciola/php/public_html/projects/2004/tutorials/Guitar/relazione.html") (translated):


I don't really know in which file I have to search that string or even if that's the font that's causing the issue. But, let's suppose that's the problem, isn't there anything that I can do in Ubuntu to make it recognize the font instead of modifyng a hex file?

---

### Post by Toz on 2011-06-09
I'm not really a font guru, but perhaps you can try this.

There is a file (/usr/share/fonts/X11/Type1/fonts.alias) that contains font aliases. Perhaps you can create an alias for the problem font. Open the file and add to the end of it:
```
-Adobe-helvetica-medium-o-normal--18-*-75-75-p-*-iso8859-1 "-urw-nimbus sans l-regular-i-normal--18-*-75-75-p-0-iso8859-1"
```
Save, reboot and try again.

If that doesn't work, you might want to also try:```
-Adobe-helvetica-medium-o-normal--18-*-75-75-p-*-iso8859-1 helvetica-medium-o-normal--18-*-75-75-p-0-iso8859-1
```

---

### Post by Calcousin55 on 2011-10-10
I had the same porblem and I just installing the xorg fonts 100dpi and 75dpi and then rebooted. This fix the problem for me.

---

