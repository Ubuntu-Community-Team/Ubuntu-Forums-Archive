---
title: "Prevent recursive mappings in .vimrc"
date: 2010-08-12
forum: General Help
---

### Post by geoffjay on 2010-08-12
I've added the following to my .vimrc:

```
function CommentLines()
  :'<,'>s/^/\/\/
endfunction

map <F2> :call CommentLines()<CR>
```

This works fine if I then copy multiple lines in vim using C-v and hit <ESC>:call CommentLines()<CR>, but if I press <F2> instead of this

//line 1
//line 2

I get this

////line 1
////line 2

The sequence repeats recursively depending on the number of lines that were selected. I know that there is a noremap that is apparently to fix this I just don't know how to use it.

Can anyone enlighten me? Thanks.

---

### Post by geoffjay on 2010-08-27
bump. no vim experts out there?

---

