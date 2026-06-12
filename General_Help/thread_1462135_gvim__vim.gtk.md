---
title: "gvim ? vim.gtk"
date: 2010-04-25
forum: General Help
---

### Post by tanyeun on 2010-04-25
there's something about gvim and vim.gtk
that I couldn't explain

```

$ls -l /usr/bin/gvim
.....-> /etc/alternatives/gvim
$ls -l /etc/alternatives/gvim
.....-> /usr/bin/vim.gtk

```

so if I type $gvim should be equivalent to $vim.gtk
but only $gvim calls the GUI $vim.gtk still stays in CLI

any ideas why?

thx,

David

---

### Post by ibuclaw on 2010-04-25
This is actually to do with the way the program is designed.

vim checks what command it was called as (in this case, checks if program name == 'gvim'), and starts a GUI or CLI editor in accordance to this.


If you prefer the GUI vim, I recommend that you have a look at [cream]("apt:cream") - is a much nicer/friendlier GUI editor for vim.

Regards

---

