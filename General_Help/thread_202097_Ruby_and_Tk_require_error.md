---
title: "Ruby and Tk require error"
date: 2006-06-22
forum: General Help
---

### Post by stash1071 on 2006-06-22
Hi, I've been learning Ruby and want to try out Tk. When I execute a .rb with a require 'tk' I get:

~/ruby$ ./test.rb
./test.rb:3:in `require': no such file to load -- tk (LoadError)
from ./test.rb:3

My system has tk.rb installed at
/usr/share/ruby/ruby-1.8.4/ext/tk/lib/tk.rb

tk.rb requires:
require 'tcltklib'
require 'tkutil'

which I find at
/usr/share/ruby/ruby-1.8.4/ext/tk/tcltklib.c
/usr/share/ruby/ruby-1.8.4/ext/tk/tkutil/tkutil.c
amongst other what look like necessary files

Im running Kubuntu (not Ubuntu but I wouldnt believe the disparity matters) and Adept package manager says I have
tcl8.4 and tk8.4 installed

Ive read I need bindings or have to run ./configure with options like
--with-tk-include, --with-tk-lib, --with-tk-dir

But I can't get anywhere, I probably need more details (Im a newbie)

Thanks for your help, I'll be glad to include more info

---

