---
title: "Display Line numbers in VI editor"
date: 2010-06-18
forum: General Help
---

### Post by dheerajkabra on 2010-06-18
Hi,

we display line numbers in vi editor by typing ":set nu" 

but I want VI to display line numbers as soon as I open a file (meaning I don't have to type ":set nu"). 

I believe this is possible by setting some environment variable for VI. But I don't know exactly what variable to set and how to set.

Thanks.

---

### Post by gmargo on 2010-06-18
You can place commands like "set number" in your $HOME/.vimrc file.

Take a look at /usr/share/vim/vimrc and  /usr/share/vim/vim72/vimrc_example.vim for starting points for your own $HOME/.vimrc. And read the help while running vim with ":help" and ":help vimrc".

---

### Post by dheerajkabra on 2010-06-18
That was a kicker.
Many thnx gmargo:guitar:

---

