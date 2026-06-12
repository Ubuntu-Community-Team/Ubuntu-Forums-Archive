---
title: "Un-Installing a built from source program (Ruby on Rails Headaches)"
date: 2006-04-01
forum: General Help
---

### Post by kook44 on 2006-04-01
Hi-
I'm trying to install Ruby on Rails v1.1.  Since there is no official package for Ruby 1.8.4, I built it from source and installed it.  When I try to install gems with sudo ruby setup.rb, I get the following error:
```

/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': no such file to load -- zlib (LoadError)

```

From googling, I think I've determined that the problem is that I installed zlib *after* I installed Ruby, so it is not configured properly to use it.  Is there any way I can un-install ruby, then make sure I have all the dependencies installed, then re-install it.

Or, if anyone knows a shortcut to fixing this error - it would be much appreciated.

THANKS!

---

### Post by robtotheb on 2006-04-01
This method of installing worked for me in Dapper....

Hope it helps

[http://paulgoscicki.com/archives/2005/09/ruby-on-rails-on-ubuntu/]("http://paulgoscicki.com/archives/2005/09/ruby-on-rails-on-ubuntu/")

---

### Post by kook44 on 2006-04-02
Thanks, but I wanted to install the newsest rails v1.1, which isn't compatible with the packaged version of Ruby (1.8.3).

I need to compile Ruby 1.8.4 from source

---

