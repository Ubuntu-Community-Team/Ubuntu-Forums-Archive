---
title: "Vim the editor, configure problem"
date: 2010-04-19
forum: General Help
---

### Post by umsorg on 2010-04-19
Trying to learn how to use vim, but have one problem. Is there away to make vim show text like seen at the photo.

[http://i44.tinypic.com/24cxtnd.jpg](http://i44.tinypic.com/24cxtnd.jpg)

---

### Post by ibuclaw on 2010-04-19
In your ~/.vimrc file
```

highlight Normal ctermbg=black
highlight Normal ctermfg=green

```

Note: for gvim, you will use guibg= and guifg= respectively.

For more info
```
:help highlight
```

Regards
Iain

---

### Post by umsorg on 2010-04-19
Sorry, my mistake.

I mean how can I get padding left/right so the text is middle of the screen like in the photo.

---

