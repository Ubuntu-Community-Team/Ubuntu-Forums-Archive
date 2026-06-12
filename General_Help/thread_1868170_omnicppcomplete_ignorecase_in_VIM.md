---
title: "omnicppcomplete ignorecase in VIM?"
date: 2011-10-23
forum: General Help
---

### Post by xiangxw on 2011-10-23
How to set omnicppcomplete to ignorecase in VIM when doing completion? How can I do this?

---

### Post by micael3000 on 2011-10-23
Hello,

I am not sure if I got what you mean... Try reading this ([http://www.vim.org/scripts/script.php?script_id=1520](http://www.vim.org/scripts/script.php?script_id=1520)).
If it is not about it, please describe again (more detailed) what you need.

:)

---

### Post by xiangxw on 2011-10-23
> **micael3000 said:**
> Hello,

I am not sure if I got what you mean... Try reading this ([http://www.vim.org/scripts/script.php?script_id=1520](http://www.vim.org/scripts/script.php?script_id=1520)).
If it is not about it, please describe again (more detailed) what you need.

:)

sorry for my english.:)
I want vim to ignorecase when omnicppcomplete doing completion.
I add "set ignorecase" to ~/.vimrc, but this does not work for omnicppcomplete.

---

### Post by micael3000 on 2011-10-24
Hello xiangxw,

I don't think it is easily possible... OmniCppComplete is dated of 2007 (pretty old) and on the final release note you can see this paragraph:
> -   Bug where the script fails to detect the type of a variable when  
    the ignorecase option is on (reported by Alexey Vakhov) 


However, if I may ask you... Why are you trying to ignore case in C/C++? It is case-sensitive.

[]'s.


edit:
Oohh, I believe you are trying to write everything in lowercase and make it adjust it all for you, is that correct?

---

### Post by xiangxw on 2011-10-24
> **micael3000 said:**
> Oohh, I believe you are trying to write everything in lowercase and make it adjust it all for you, is that correct?

Yes, that's what i want to do. I write Qt code and it has many functions that have uppercase letter.

---

### Post by micael3000 on 2011-10-26
In this case, I am sorry because I have no idea how to help you. :(

---

### Post by xiangxw on 2011-10-26
thanks all the same

---

