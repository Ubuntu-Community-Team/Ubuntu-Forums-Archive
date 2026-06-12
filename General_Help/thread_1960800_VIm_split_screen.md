---
title: "VIm split screen"
date: 2012-04-18
forum: General Help
---

### Post by Drenriza on 2012-04-18
Hey guys.

I have taken the step to work with vim in a single terminal window with multiple vim windows.
My only issue at the moment. Is that i open a vim and split the screen with

vim -O file1 file2

But how do i switch between the windows? ctrl + w + arrow left / right docent work. And the :n and :prev is not what i'am looking for. Is their another way to switch between the windows?

Thanks on advance.
Kind regards.

---

### Post by codemaniac on 2012-04-18
when editing multiple files at one go , i use :ar to check which file i am currently in and :n to traverse through files .
i guess you can use Vim's split screen feature to divide the screen into multiple panes, each of which can display a file.

```
:split file
``` Splits the window horizontally

In order to traverse between splitted windows have a ```
<ctrl>+w
```

---

### Post by sj1410 on 2012-04-18
ctrl+ww to switch between windows

---

### Post by Drenriza on 2012-04-18
> **sj1410 said:**
> ctrl+ww to switch between windows

Thanks **ctrl + ww** works like a charm

---

