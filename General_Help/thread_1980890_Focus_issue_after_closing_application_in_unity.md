---
title: "Focus issue after closing application in unity"
date: 2012-05-16
forum: General Help
---

### Post by 4984 on 2012-05-16
In Ubuntu 11.10 and 12.04 I encountered a focus relate issue.
Since the only description of this problem I could find is this video: [http://www.youtube.com/watch?v=w6lUH-l2AGM]("http://www.youtube.com/watch?v=w6lUH-l2AGM"), I though I ask here if there's any solution as of now.

Thanks for your help.

---

### Post by efflandt on 2012-05-16
I have noticed that too when using firefox, opening the file viewer, hitting Ctrl+H, and discovering that it opened History in firefox instead of showing hidden files.  So I just click on the file viewer to give it focus and move on.

---

### Post by 4984 on 2012-05-16
I know I can work around that, but the problem is that every application keeps it's focus after I closed it. Now since I use Ubuntu on my notebook, I start and close (and use) all applications via hotkeys (I really don't like trackpads). The custom hotkeys do only work while the Ubuntu desktop is focused though. That means whenever I close a programm, my hands have to leave the keyboard, I have to move the mouse to the desktop and perform an unneccesary click.
I can live with that, but since this behaviour can't possibly be intended, I would really appreciate to know if there's a fix for it.
Thank you for your reply though!

---

### Post by 4984 on 2012-05-20
Just in case somebody has the same problem, here's the solution:
The issues were caused by conky. Adding the following lines to .conkyrc soved the issues:

```

own_window yes
own_window_class Conky
own_window_transparent no
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

Enjoy!

---

