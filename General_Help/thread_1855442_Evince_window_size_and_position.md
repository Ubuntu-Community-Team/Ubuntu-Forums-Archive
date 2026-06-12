---
title: "Evince window size and position"
date: 2011-10-06
forum: General Help
---

### Post by bovender on 2011-10-06
Hello,

the PDF document viewer (evince) does not remember its window size and position between sessions. Every time I start the application, the size of the window seems to be totally random. Currently, the window is so small that not even the thumbnails on the left fit into it. Sometimes, the window will be very wide, but not high enough. Also, the window is placed in a completely random way on my screen.

How can I convince evince to remember its window size and position like the other applications do?

It's somewhat of a hassle having to resize the window every time I want to view a PDF file.

Thanks!

---

### Post by WasMeHere on 2011-10-06
Would it help to run fullscreen mode (either by F5) or simply to maximize the window? See also ```
evince --help-all
```

---

### Post by bovender on 2011-10-06
Thanks for your response.

The -f switch is indeed an interesting workaround! Not quite what I want, but better than the current situation.

---

### Post by Howard Cheng on 2011-12-08
I have exactly the same problem.  Every time evince opens with a document it is very small.  None of the settings is remembered from one document to another (although it does seem that it is remembered for the same document).  That makes reading PDFs from web pages tedious since it is always a new temporary file.

---

### Post by MichaelBurns on 2012-03-21
Olle, do you actually know how to make window maximized by default (for all new documents)?  I saw the -f switch in the --help-all, but I would prefer to have it maximized rather than fullscreen.  (I am terminally addicted to the alt+tab key sequence.)

I have read in my online snooping that the team responsible for evince has withheld confinguration settings from the user ON PURPOSE!  ("that's the beauty of evince", they say.)  WHAT!?

---

