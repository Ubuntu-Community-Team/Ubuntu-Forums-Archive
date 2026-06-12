---
title: "Printing Crashes Desktop"
date: 2011-11-21
forum: General Help
---

### Post by liferules on 2011-11-21
I have an interesting and annoying issue. Every time I print from an application, my desktop literally crashes (I think). All the icons and window dressings resets to Gnome Humanity (I beleive). 

In screenshot1 you will see my default desktop. 

In screenshot2 you see my desktop after I printed a test page from the printer applet. The desktop is fine. 

In screenshot3 I have printed from Adobe Reader and notice the change in the Desktop icons.... I have verified that this happens every time I print from an application, no matter the application or the file type. I have also verified this behavior in Unity and Gnome Shell so I do not believe it is the Window Manager. 

Any ideas?

You help would be appreciated.

---

### Post by liferules on 2011-11-28
Bump

---

### Post by bluexrider on 2011-11-28
I had a similar instance working in Nautilus as Root. My desktop icons would default to standard theme, I was forced to restart nautilus to regain my icons. 

It was a permissions issue. 

Your applications that cause your issue are NOT set as Root are they?

just a thought! seems like it might be related some how.

---

### Post by liferules on 2011-11-28
Not sure .... but being it happens in every application I print from I am more inclined to think it is a gnome-print or CUPS issue... 

Not sure how to check from here....

---

### Post by liferules on 2011-11-28
Installed kde-standard just to test and it prints fine ... so probably a gnome print issue....

---

### Post by bluexrider on 2011-11-28
as I recall I was running Gnome at the time my issues occurred too. never thought about changing desktops.

let the diagnosis begin

so....printing causes Gnome desktop to crash!

---

### Post by liferules on 2011-11-28
Yeh.... notice in my original post that it happens in Unity and Gnome Shell

---

### Post by kurt18947 on 2011-11-28
If you're using the default pdf viewer, you might try an alternative.  Certain pdf files or certain pages within a multipage document caused me printing problem though not your extent.  I installed Foxit reader and that printed properly where evince or whatever did not.  Just something to try.  I installed AcroRead from Adobe once on 11.04 (I think) and it worked well but what a bloated whale of a program.

---

### Post by liferules on 2011-11-28
I use Acroread but it crashes with other file formats too... 

I am thinking about re-installing the Brothers drivers to check that off my list... 

I can print a file (PDF or PS) but using the physically printer is the problem.... 

I will keep you informed....

---

### Post by liferules on 2011-11-29
re-installed Brothers was no help at all.... 

Still have this VERY annoying issue....

---

### Post by liferules on 2011-11-29
Bump

---

### Post by liferules on 2011-12-03
Bump

---

### Post by liferules on 2011-12-05
Okay it seems to be fixed ... I did notice a update to CUPS came through yesterday so maybe this was infact a bug ....

I will re-post if it happens again

---

