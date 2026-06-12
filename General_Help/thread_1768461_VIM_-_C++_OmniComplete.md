---
title: "VIM - C++ OmniComplete"
date: 2011-05-26
forum: General Help
---

### Post by miningold on 2011-05-26
Hello I am trying to get omnicomplete to work with c++ code in VIM.
I followed this tutorial:
[C++ Code Completion]("http://vim.wikia.com/wiki/C%2B%2B_code_completion")

However, when I get to step in the tutorial where it says: 

Start typing: std::

I get a little message in VIM that says:

Omni completion (^O^N^P) Pattern not found

This is what my .vimrc file looks like:

```
set nocp
filetype plugin on "enable plugins

" configure tags - add additional tags here or comment out not-used ones
set tags+=~/.vim/tags/cpp
" build tags of your own project with Ctrl-F12
map <C-F12> :!ctags -R --sort=yes --c++-kinds=+p --fields=+iaS --extra=+q .<CR>

" OmniCppComplete
let OmniCpp_NamespaceSearch = 1
let OmniCpp_GlobalScopeSearch = 1
let OmniCpp_ShowAccess = 1
let OmniCpp_ShowPrototypeInAbbr = 1 " show function parameters
let OmniCpp_MayCompleteDot = 1 " autocomplete after .
let OmniCpp_MayCompleteArrow = 1 " autocomplete after ->
let OmniCpp_MayCompleteScope = 1 " autocomplete after ::
let OmniCpp_DefaultNamespaces = ["std", "_GLIBCXX_STD"]
" automatically open and close the popup menu / preview window
au CursorMovedI,InsertLeave * if pumvisible() == 0|silent! pclose|endif
set completeopt=menuone,menu,longest,preview
```

Does anyone know how to get OmniCompletion working with c++?

---

