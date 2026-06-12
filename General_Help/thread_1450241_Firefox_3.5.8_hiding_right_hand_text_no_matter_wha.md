---
title: "Firefox 3.5.8 hiding right hand text no matter what"
date: 2010-04-08
forum: General Help
---

### Post by hangfire on 2010-04-08
In viewing some web pages, the right hand dozen or so characters are hidden unless the left-right scroll bar is used.

When Firefox 3.5.8 32 bit is expanded to full screen on a 1920 pixel wide monitor on Kubuntu 9.10, Firefox changes the word wrap so the new dozen or so characters are STILL hidden, forcing me to use the left-right scrool bar.

There no longer appears to be any Word Wrap option. I tried several solutions Googled, including userContent.css hacks and a couple of add-ins, but they all appear to apply only to the preformatted tag.

This is not a "pre" issue. The text in question is not inside the preformatted text tag, and the site CSS is not under my control.

---

### Post by lovinglinux on 2010-04-08
[COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by hangfire on 2010-04-08
Thanks. There is lots of useful information there, but I find nothing about invoking word wrap on non-pre text, or any other hint of a solution.

---

### Post by lovinglinux on 2010-04-08
> **hangfire said:**
> Thanks. There is lots of useful information there, but I find nothing about invoking word wrap on non-pre text, or any other hint of a solution.

At the beginning of the troubleshooting section, there are some steps to help you determine where the problem lies. Do that and post your results.

---

### Post by hangfire on 2010-04-08
Thanks. I went back and found the issue.

The web pages in question have text like this:

<p class=MsoNormal style='margin-top:0in;**margin-right:-.75in**;margin-bottom:0in;
margin-left:.25in;margin-bottom:.0001pt'><span style='font-size:14.0pt;
font-family:Arial'>A Paragraph worth of text </span></p>

So Firefox is only doing what it is told to do.

According to the meta generator tag, this is the work of a very popular commercial word processor that should never be allowed to generate HTML.

-HF

---

### Post by lovinglinux on 2010-04-08
> **hangfire said:**
> According to the meta generator tag, this apparently this is the work of a very popular commercial word processor that should never be allowed to generate HTML.

-HF

:lol:

---

