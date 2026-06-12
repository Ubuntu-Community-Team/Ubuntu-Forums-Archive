---
title: "acroread plugin problem - opera"
date: 2010-01-24
forum: General Help
---

### Post by psrivats on 2010-01-24
Folks,

I am running ubuntu karmic (9.10) on my system and I use Opera (v 10.10, build 4742 for linux) as my main browser. I am having a peculiar problem with adobe reader plugin.

The plugin loads properly the first time and pdfs open in the browser. Once I close a tab with a pdf and open a new tab with the same (or a different pdf), all I get is a white page. Doing a 

```
ps -ef | grep acroread
```

lists a defunct acrobat process. Example:
```
psrivats@Bender:~$ ps -ef | grep acroread
psrivats 16777 16765  2 02:20 ?        00:00:03 [acroread] <defunct>
psrivats 16832 16621  0 02:23 pts/3    00:00:00 grep --color=auto acroread

```

kill -9 <pid> does not kill this zombie process. I have to issue kill -9 <parent pid> to close the process. If I do this, I will be able to view pdfs in the browser again. I have to keep repeating this if I want to see pdfs.

I checked and found out that there is no problem with Firefox.

Is there a fix for this issue? Or is this a bug - if so, has anyone filed a bug report?

---

### Post by psrivats on 2010-01-24
This is the same problem reported here:

[http://list.opera.com/pipermail/opera-linux/2009-April/009912.html](http://list.opera.com/pipermail/opera-linux/2009-April/009912.html)

I also notice that Opera creates two proceses whenever I open a PDF file - operapluginwrapper and operaplugincleaner. These proceses are still active even after closing the PDF tab. Killing these proceses kills the zombie acroread process and I can PDFs again.

---

### Post by psrivats on 2010-01-30
Does anyone has a fix for this ?

---

### Post by InvisibleEye on 2010-02-07
Hi psrivats,

I think I have a fix for this; at least it worked for me and I haven't had to kill processes since. I'm running Ubuntu 9.10 and Opera as my main browser (no FF installed anymore). Here's what I did:

Tools -> Preferences -> Advanced -> Downloads -> application/pdf -> Edit.

Check the box next to «open with default application». For some reason, in my case, no box at all was checked (and it's a clean Opera install). The default application is acroread.

Hope that helps!

---

### Post by psrivats on 2010-02-19
> **InvisibleEye said:**
> Hi psrivats,

I think I have a fix for this; at least it worked for me and I haven't had to kill processes since. I'm running Ubuntu 9.10 and Opera as my main browser (no FF installed anymore). Here's what I did:

Tools -> Preferences -> Advanced -> Downloads -> application/pdf -> Edit.

Check the box next to «open with default application». For some reason, in my case, no box at all was checked (and it's a clean Opera install). The default application is acroread.

Hope that helps!

Thank you!

I just tried this and found out that this makes the pdfs open in the application (acroread or okular, both work) I choose instead of the browser. This means I don't have to worry about my browser crashing anymore, or having to restart the plugin. With adobe reader 9's multi-tabbed interface, this is an excellent workaround.

---

### Post by scofflan on 2011-04-20
I'm having this same issue in FF with Acroread but only on 64 bit machines. 
I need to have the PDFs opened in the browser as they are embedded in our website.

Any suggestions?

---

