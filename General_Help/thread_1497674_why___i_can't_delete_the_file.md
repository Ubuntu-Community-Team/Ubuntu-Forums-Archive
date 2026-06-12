---
title: "why   i can't delete the file?"
date: 2010-05-30
forum: General Help
---

### Post by luofeiyu on 2010-05-30
pt@pt-laptop:~$ find /home/pt -name '*~'
/home/pt/Desktop/ubuntu_usage/vcd  make~
/home/pt/Desktop/ubuntu_usage/shell/video/vcd  make~
/home/pt/ubuntu_usage/shell/video/vcd  make~
pt@pt-laptop:~$ find /home/pt -name '*~'|xargs rm -rf
pt@pt-laptop:~$ find /home/pt -name '*~'
/home/pt/Desktop/ubuntu_usage/vcd  make~
/home/pt/Desktop/ubuntu_usage/shell/video/vcd  make~
/home/pt/ubuntu_usage/shell/video/vcd  make~
what's the matter?how can i do?

---

### Post by JustinR on 2010-05-30
I'm not sure what your trying to accomplish but, "xargs rm -rf" looks incorrect to me.

---

### Post by luofeiyu on 2010-05-31
rm -rf "/home/pt/Desktop/ubuntu_usage/vcd make~"
can't delete too,what's wrong?

---

### Post by loko on 2010-05-31
If the solution mentioned in the last post is not working,

post the output of:

> find /home/pt -name '*~'|xargs ls -l

---

### Post by luofeiyu on 2010-05-31
it work!
find /home/pt -name '*~' | xargs -0 rm -rf 


  -0     Input  items  are  terminated  by a null character instead of by
              whitespace, and the quotes and backslash are not special  (every
              character is taken literally).  Disables the end of file string,
              which is treated like any other  argument.   Useful  when  input
              items  might  contain  white space, quote marks, or backslashes.
              The GNU find -print0 option produces  input  suitable  for  this
              mode.

can't i use one command of  rm  to delete it?
it need  find and xargs and rm ,three commands to work together?

---

