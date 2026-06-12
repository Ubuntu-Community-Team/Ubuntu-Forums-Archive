---
title: "Vim Syntax Highlighting"
date: 2011-09-24
forum: General Help
---

### Post by CaKiwi on 2011-09-24
I am trying to create a very simple syntax highlighting file for vim. Highlighting is working for standard files such as .vim files

Example file t.pp
               
LN1 = LINE/0,0,2,0              $$ COMMENT
LN2 = LINE/PARLEL,LN1,XLARGE,1  %  COMMENT
$$ COMMENT
% COMMENT

I want the word LINE to be one color and the words PARLEL and XLARGE to be another color. There are more words of each type which I want to be able to add. Everything after $$ or % is a comment which could be a third color.

Any help greatly appreciated.

---

### Post by CaKiwi on 2011-09-29
I think the piece I'm missing is how to get vim to recognize a new file type. Fortran has a few of the same key words (if, endif, do, etc) so I copied the fortran syntax file as a pp syntax file but nothing was hightlighted.

Any help greatly appreciated.

---

### Post by CaKiwi on 2011-10-06
The part I was missing was to put my file type in the filetype.vim file (in /usr/share/vim/vimcurrent on my system). I found it by searching for f77 in the vim directory. It must be mentioned in the doc somewhere, but I didn't find it, although reading doc is not my forte.

---

### Post by Claus7 on 2011-10-06
Hello,

I did not understand what you did, yet if you open a file with vim, 
e.g. vim something.f90, the text will be highlighted accordingly, as vi will be able to recognise the type of file, from the extension.
Also there are options, from which you can choose different highlighting techniques for your files.

Regards!

---

### Post by CaKiwi on 2011-10-06
What I did was edit the file filetype.vim in the /usr/share/vim/vimcurrent directory and put the following line in it for ncl which is my file type.

au BufNewFile,BufReAD *.pp,*.ncl              setf ncl

Then I created a file ncl.vim with syntax commands in it and put it in the ~/.vim/syntax directory.

---

