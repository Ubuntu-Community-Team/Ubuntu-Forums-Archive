---
title: "export variables gone"
date: 2011-06-17
forum: General Help
---

### Post by bigthugs0 on 2011-06-17
hi all

im trying to export to PATH ,
at first everything goes well
but when i close the terminal and open it again its gone !! i dont know why!!!

i did the following

export GROOT=$HOME/go
export GOBIN=$GOROOT/bin
export PATH=$PATH:$GOBIN

help plz

---

### Post by nothingspecial on 2011-06-17
That's because once you close that terminal, any variable you defined in it is gone.

This is useful because sometimes you only want to define a variable for what you are trying to do right there and then.

If you want to define a variable for ever, for example, add a directory to your $PATH one option is to define it in your .bashrc

---

### Post by bigthugs0 on 2011-06-17
oh thnx very much that works :)

---

### Post by nothingspecial on 2011-06-17
No problem

---

