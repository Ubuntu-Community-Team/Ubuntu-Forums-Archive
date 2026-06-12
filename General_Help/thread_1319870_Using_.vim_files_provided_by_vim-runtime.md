---
title: "Using .vim files provided by vim-runtime"
date: 2009-11-08
forum: General Help
---

### Post by michaelmior on 2009-11-08
I'm a long-time Ubuntu user, but I recently switched from using gedit to vim. I'm having trouble making use of the tidy.vim compiler provided by the vim-runtime package. I understand that it should run HTML tidy for HTML documents, but I'm not quite sure how it works. Since the file is short, I included it below. Thanks!

```

if exists("current_compiler")
  finish
endif
let current_compiler = "tidy"

if exists(":CompilerSet") != 2          " older Vim always used :setlocal
  command -nargs=* CompilerSet setlocal <args>
endif

" this is needed to work around a bug in the 04/08/00 release of tidy which
" failed to set the filename if the -quiet option was used
if exists("tidy_compiler_040800")
  CompilerSet makeprg=tidy\ -errors\ --gnu-emacs\ yes\ %
else
  CompilerSet makeprg=tidy\ -quiet\ -errors\ --gnu-emacs\ yes\ %
endif

" sample warning: foo.html:8:1: Warning: inserting missing 'foobar' element
" sample error:   foo.html:9:2: Error: <foobar> is not recognized!
CompilerSet errorformat=%f:%l:%c:\ Error:%m,%f:%l:%c:\ Warning:%m,%-G%.%#

```

---

