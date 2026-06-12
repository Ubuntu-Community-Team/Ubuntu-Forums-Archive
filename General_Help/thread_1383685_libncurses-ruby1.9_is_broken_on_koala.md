---
title: "libncurses-ruby1.9 is broken on koala"
date: 2010-01-17
forum: General Help
---

### Post by orengolan on 2010-01-17
I installed libncurses-ruby1.9 and when trying to run any of the samples scripts (/usr/share/doc/libncurses-ruby1.9/examples) I get no such file to load -- ncurses.so :
```
/opt/ruby-1.9.1-p243/lib/ruby/gems/1.9.1/gems/ncurses-0.9.1/lib/ncurses.rb:21:in `require': no such file to load -- ncurses.so (LoadError)
        from /opt/ruby-1.9.1-p243/lib/ruby/gems/1.9.1/gems/ncurses-0.9.1/lib/ncurses.rb:21:in `<top (required)>'
        from hello_ncurses.rb:17:in `require'
        from hello_ncurses.rb:17:in `<main>'
```

There is a similar thread of debian:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501294](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=501294)

I tried their solution (installed libncurses-ruby1.9_1.1-3_i386.deb)
but I get the same error.

---

