---
title: "Vi copying text"
date: 2011-01-25
forum: General Help
---

### Post by COKEDUDE on 2011-01-25
Is there a trick for copying from something like a powerpoint into vi? Every time I try to copy text from something like a powerpoint to vi my spacing gets messed up. I think it has something to do with my .vimrc file. When I renamed it was able to copy it in just fine so can someone please tell me what in my .vimrc is messing it up. Here is my .vimrc so you can take a look at it. Below it is what I am trying to copy into vi.

```
set nocompatible
set autoindent
set smartindent
set tabstop=4
set shiftwidth=4
set showmatch
set vb t_vb=
set ruler
set nohls
set incsearch
set virtualedit=all
set number
set cmdheight=2
"This command uses unix mode
set ff=unix

"This command uses dos mode
"set ff=dos

``````
#include <iostream>

int main( void )                                          
{  
   int a;
   int b;
   std::cout << "Enter two integers to compute their sum:" << std::endl;

   std::cin >> a;
   std::cin >> b;

   std::cout << "The sum of " << a << " and " << b  << " is ";
   std::cout << a + b << std::endl;

   return 0;
}
```

---

### Post by eentonig on 2011-01-25
I think the autoindent is messing up the copy and paste.


[http://vim.wikia.com/wiki/Vim_Tips_Wiki](http://vim.wikia.com/wiki/Vim_Tips_Wiki) is a good source to find out how to overcome this.

---

