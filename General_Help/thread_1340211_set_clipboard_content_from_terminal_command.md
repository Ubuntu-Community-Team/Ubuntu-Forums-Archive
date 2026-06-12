---
title: "set clipboard content from terminal command"
date: 2009-11-28
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-11-28
in windows i would use a program called [nircmd]("http://www.nirsoft.net/utils/nircmd.html")
any one know of a command for linux?

---

### Post by kaibob on 2009-11-28
The xclip utility will do what you want. The following is a description from the xclip man page. Xclip is not installed by default but is available in the repo's. 

> Reads from standard in, or from one or more files, and makes the data available as an X selection for pasting into X  applications. Prints current X selection to standard out.

For a little more information see:

[http://www.cyberciti.biz/faq/xclip-linux-insert-files-command-output-intoclipboard/](http://www.cyberciti.biz/faq/xclip-linux-insert-files-command-output-intoclipboard/)

You may also want to look at the xsel utility, which does pretty much the same thing. Xclip works for me, so I haven't used xsel.

BTW, I had never heard of NirCmd. It does a whole lot of different stuff.

---

### Post by pqwoerituytrueiwoq on 2009-11-30
do you have a usage example?
i cant figure out how to set a string to the clipboard or selection

---

### Post by kaibob on 2009-11-30
> **pqwoerituytrueiwoq said:**
> do you have a usage example?
i cant figure out how to set a string to the clipboard or selection

Run the following command in a terminal window. Then middle-mouse-button click in the terminal, text editor, or elsewhere to insert the text.

```
echo "this is a test" | xclip
```

The link in my earlier post was incorrect. I have fixed it, although a google search on xclip will show many pages with examples.

---

