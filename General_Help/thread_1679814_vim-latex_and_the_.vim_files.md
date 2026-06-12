---
title: "vim-latex and the *.vim files"
date: 2011-02-01
forum: General Help
---

### Post by rks171 on 2011-02-01
I installed the vim-latex suite.  Syntax colors are working great, but the autoindent feature is not working like it works for .html and .f90 files.  My .vimrc file is, as far as I can see, correct:

```
syntax on

" REQUIRED. This makes vim invoke Latex-Suite when you open a tex file.
filetype plugin on

" IMPORTANT: win32 users will need to have 'shellslash' set so that latex
" can be called correctly.
set shellslash

" IMPORTANT: grep will sometimes skip displaying the file name if you
" search in a singe file. This will confuse Latex-Suite. Set your grep
" program to always generate a file-name.
set grepprg=grep\ -nH\ $*

" OPTIONAL: This enables automatic indentation as you type.
filetype indent on

" OPTIONAL: Starting with Vim 7, the filetype of empty .tex files defaults to
" 'plaintex' instead of 'tex', which results in vim-latex not being loaded.
" The following changes the default filetype back to 'tex':
let g:tex_flavor='latex'

" Expand autoindenting features
set autoindent
set shiftwidth=4
```My tex.vim file was not in the /usr/share/vim/vim72/indent directory.  I believe, but I'm not sure because I'm a linux newb, that it should be in there, so I copied it from the /usr/share/vim/vim72/ftplugin directory.  The tex.vim file looks a little funny to me, though, because, to my untrained eye, it looks like there's no rules for indenting in it.

```
" LaTeX filetype plugin
" Language:     LaTeX (ft=tex)
" Maintainer:   Benji Fisher, Ph.D. <benji@member.AMS.org>
" Version:    1.4
" Last Change:    Wed 19 Apr 2006
"  URL:        http://www.vim.org/script.php?script_id=411

" Only do this when not done yet for this buffer.
if exists("b:did_ftplugin")
  finish
endif

" Start with plain TeX.  This will also define b:did_ftplugin .
source $VIMRUNTIME/ftplugin/plaintex.vim

" Avoid problems if running in 'compatible' mode.
let s:save_cpo = &cpo
set cpo&vim

let b:undo_ftplugin .= "| setl inex<"

" Allow "[d" to be used to find a macro definition:
" Recognize plain TeX \def as well as LaTeX \newcommand and \renewcommand .
" I may as well add the AMS-LaTeX DeclareMathOperator as well.
let &l:define .= '\|\\\(re\)\=new\(boolean\|command\|counter\|environment\|font'
    \ . '\|if\|length\|savebox\|theorem\(style\)\=\)\s*\*\=\s*{\='
    \ . '\|DeclareMathOperator\s*{\=\s*'

" Tell Vim how to recognize LaTeX \include{foo} and plain \input bar :
let &l:include .= '\|\\include{'
" On some file systems, "{" and "}" are inluded in 'isfname'.  In case the
" TeX file has \include{fname} (LaTeX only), strip everything except "fname".
let &l:includeexpr = "substitute(v:fname, '^.\\{-}{\\|}.*', '', 'g')"

" The following lines enable the macros/matchit.vim plugin for
" extended matching with the % key.
" ftplugin/plaintex.vim already defines b:match_skip and b:match_ignorecase
" and matches \(, \), \[, \], \{, and \} .
if exists("loaded_matchit")
  let b:match_words .= ',\\begin\s*\({\a\+\*\=}\):\\end\s*\1'
endif " exists("loaded_matchit")

let &cpo = s:save_cpo

" vim:sts=2:sw=2:

```Are there different *.vim files (i.e. one for syntax highlighting and one for indent rules)?  Maybe this is my problem.

---

### Post by rks171 on 2011-02-01
Apparently there are different *.vim files.  I downloaded a tex.vim file from [http://www.vim.org/scripts/script.php?script_id=218](http://www.vim.org/scripts/script.php?script_id=218)

The file is completely different than the tex.vim file in my /ftplugins directory.  I copied the new file to /indent/ and indent now works, but only for the \item command.  Now that I'm learning more about how vim works, I should be able to manage manipulating the tex.vim file to add my own rules for indenting.  I'll post back with any modifications I make incase anybody else hits this problem.

---

