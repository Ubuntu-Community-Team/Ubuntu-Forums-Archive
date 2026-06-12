---
title: "VI Help - Cursor Keys"
date: 2011-02-23
forum: General Help
---

### Post by JPKowal on 2011-02-23
How come in my Ubunto VI, if I try to navigate with the cursor keys while in insert mode it does not move the cursor? Instead it just inserts either an A, B, C, or D

On my knoppix installation I do not have this problem. 

However, it should be noted that my knoppix install does not run on my laptop since I can't boot a USB. In other words, my ubunto installed on my laptop so it is using a laptop keybord while the knoppix is using a standard keyboard if that makes any difference.

---

### Post by BHEJU on 2011-02-23
Dude. fundamental of VI:
Two modes.. 1]Command 2] insert
you switch between them by pressing "ESC" key.
so, if you are in insert mode and want to navigate using keys, switch to command mode by hitting "ESC" key. and other way around.

Cheers

---

### Post by Simian Man on 2011-02-23
vi doesn't support this, but vim does.  Pretty much nobody uses vi itself any more for reasons like this.  You probably just need to install the vim package.

---

### Post by jeremy1138 on 2011-02-23
Is there a reason to use vi as your terminal based text editor of choice?  I've tried to use it a couple times and it seems needlessly complicated, unintuitive and difficult to use.

I much prefer nano.  I believe it comes standard with all versions of Ubuntu.

---

### Post by Simian Man on 2011-02-23
> **jeremy1138 said:**
> Is there a reason to use vi as your terminal based text editor of choice?  I've tried to use it a couple times and it seems needlessly complicated, unintuitive and difficult to use.

Not if you rarely use a terminal-based text editor.  If you do so often, there are many reasons.

---

### Post by tjwoosta on 2011-02-23
> **JPKowal said:**
> How come in my Ubunto VI, if I try to navigate with the cursor keys while in insert mode it does not move the cursor? Instead it just inserts either an A, B, C, or D

On my knoppix installation I do not have this problem. 

However, it should be noted that my knoppix install does not run on my laptop since I can't boot a USB. In other words, my ubunto installed on my laptop so it is using a laptop keybord while the knoppix is using a standard keyboard if that makes any difference.

Some distros symlink vi to vim, so when you run vi you are actually running vim. Im not sure if thats the case in your situation, but its a possablility.


> **jeremy1138 said:**
> Is there a reason to use vi as your terminal based text editor of choice?  I've tried to use it a couple times and it seems needlessly complicated, unintuitive and difficult to use.

I much prefer nano.  I believe it comes standard with all versions of Ubuntu.

Heres a good demo of some of the advantages of vim (vi improved)

[http://www.youtube.com/watch?v=FcpQ7koECgk](http://www.youtube.com/watch?v=FcpQ7koECgk)

---

### Post by seawolf167 on 2011-02-23
[VI]("http://www.lagmonster.org/docs/vi.html") [cheat]("http://www2.cs.uidaho.edu/%7Erinker/ed03.pdf") [sheets]("http://www.eec.com/business/vi.html")

---

### Post by JPKowal on 2011-02-24
I am using vim on both. My apologizes for calling it vi. This boards is about as picky as some bash functions.

:set nocompatiblewas what I was looking for... Dude

---

### Post by tjwoosta on 2011-02-24
> This boards is about as picky as some bash functions.


Well.. it was kind of relevant in this case :p

---

### Post by SESteve on 2011-03-04
> **JPKowal said:**
> :set nocompatible was what I was looking for... Dude

If it makes you feel any better, this helped me figure out the same problem.

Thanks, Dude!

---

