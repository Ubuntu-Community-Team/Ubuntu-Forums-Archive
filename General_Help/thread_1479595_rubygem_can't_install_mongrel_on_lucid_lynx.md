---
title: "rubygem: can't install mongrel on lucid lynx"
date: 2010-05-10
forum: General Help
---

### Post by arscariosus on 2010-05-10
Hi, I just installed Ubuntu 10.04 on an old desktop computer so that I could use it for Rails. I installed Ruby, rubygems and Rails using ```
sudo apt-get install
``` and it works fine, but I cannot install Mongrel through ```
sudo gem install mongrel
``` it's giving me this block of error message:

```
Building native extensions.  This could take a while...
ERROR:  Error installing mongrel:
    ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb
extconf.rb:8:in `require': no such file to load -- mkmf (LoadError)
    from extconf.rb:8

```I tried removing the rubygem 1.3.5 package that came with the Ubuntu repository and downloaded Rubygems 1.3.6 from rubygems.org, but when I tried the same command, it still gives me the same error. Any help would be appreciated. :)

---

### Post by gmallard on 2010-05-20
You need to install the -dev ruby package, for example:

ruby1.8-dev

---

