---
title: "zlib-devel and rubygems"
date: 2006-03-23
forum: General Help
---

### Post by jlapier on 2006-03-23
Hey Ubunters - 
I've been running Ruby on Rails on Breezy (PPC) for a couple months now. The ruby package that gets installed in Breezy is called 1.8.2-9ubuntu1, but when you do 'ruby -v', it says Ruby 1.83. Rails is recommended to be run on 1.82 or 1.84, but not 1.83. I ran it anyway, which seemed to work ok, but recently, an RC for Rails 1.1 came out and I tried to run it but it gives an error about running on Ruby 1.83.
So I tried to install Ruby 1.84 from source. This seemed to compile fine and I can run Ruby just fine. When I tried to install rubygems however, I get the following error:

/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': no such file to load -- zlib (LoadError)

When I search around on this error, people say you need to have the zlib development libraries installed, which as far as I can tell, I do:
```

root@jubunt:~# aptitude search zlib
i A libcompress-zlib-perl                                                     - Perl module for creation and manipulation of gzip files
p   libio-zlib-perl                                                           - IO:: style interface to Compress::Zlib
p   libjzlib-java                                                             - Reimplementation of zlib in pure java
iB  libzlib-ruby                                                              - Extension library to use zlib from Ruby
p   libzlib-ruby1.6                                                           - An extension library to use zlib from Ruby 1.6
v   libzlib-ruby1.8                                                           -
i   zlib-bin                                                                  - compression library - sample programs
v   zlib1                                                                     -
v   zlib1-dev                                                                 -
i   zlib1g                                                                    - compression library - runtime
i   zlib1g-dev                                                                - compression library - development
v   zlib1g-udeb                                                               -
i   zlibc                                                                     - Uncompressing C Library

```

I noticed that for other distros, there is a zlib-devel package - I'm assuming that's the same as zlib1g-dev (since I don't see any zlib-devel in the list). 

Anyone got any suggestions?

---

### Post by jlapier on 2006-03-23
Nevermind - I got it. Turns out after you run ./configure you have to edit ext/Setup and uncomment any extensions you want added before you run make.

- Jason

---

