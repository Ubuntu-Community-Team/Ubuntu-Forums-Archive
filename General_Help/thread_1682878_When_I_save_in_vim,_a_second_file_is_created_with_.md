---
title: "When I save in vim, a second file is created with ~ attached to the end"
date: 2011-02-06
forum: General Help
---

### Post by nobleisthyname on 2011-02-06
Every time I create a file in vim (which I use for coding, so mostly .h and .cpp files) after I save it a second file is created of the exact same name with the tilde symbol attached to the end. Why does this happen and how can I stop it? Thanks for your help.

---

### Post by [Snc] on 2011-02-06
> **nobleisthyname said:**
> Every time I create a file in vim (which I use for coding, so mostly .h and .cpp files) after I save it a second file is created of the exact same name with the tilde symbol attached to the end. Why does this happen and how can I stop it? Thanks for your help.

That is actually a backup file, so if you save something and want the original back, you can.

(Edit: I forgot to mention this as a developer, if you edit a file and the process goes ballistic on you and eventually crashes & pukes all over the stack, nasty [*unpredictable*] stuff can happen ... including random writes to certain open files, this means your code ... if you do not have a backup ... well :) you know ... crap! :))

IMHO i wouldn't disable this behavior, but you can do it like this
Go into your _vimrc file. Add these lines to the bottom &#8211;
 ```
set nobackup
set nowritebackup
set noswapfile
```additional info: [http://thehumblecoder.wordpress.com/2006/08/08/vim-swap-and-backup-files/](http://thehumblecoder.wordpress.com/2006/08/08/vim-swap-and-backup-files/)

---

### Post by asmoore82 on 2011-02-06
I would recommend the `nobackup` options, but **not** the `noswap` option!
Vim creates swapfiles of everything you edit, but deletes them automatically.

The *~ backup files that vim and other editors create and leave behind drive me nuts.

---

### Post by nobleisthyname on 2011-02-06
Thank you very much!

---

