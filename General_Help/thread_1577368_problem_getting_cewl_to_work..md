---
title: "problem getting cewl to work."
date: 2010-09-18
forum: General Help
---

### Post by Mia_tech on 2010-09-18
guys, I'm trying to get [cewl]("http://www.digininja.org/projects/cewl.php") to work, but after installing all "gems" I'm still unable to getting working. I have used this guide

[http://www.backtrack-linux.org/forums/backtrack-howtos/27991-installing-cewl-backtrack4.html]("http://www.backtrack-linux.org/forums/backtrack-howtos/27991-installing-cewl-backtrack4.html")

this is the error I'm getting.
```
jorge@nixboxen:/usr/bin/samurai/cewl$ ./cewl.rb
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- net/https (LoadError)
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
        from /usr/lib/ruby/gems/1.8/gems/spider-0.4.4/lib/spider/spider_instance.rb:30
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
        from /usr/lib/ruby/gems/1.8/gems/spider-0.4.4/lib/spider.rb:26
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:36:in `require'
        from ./cewl.rb:58

```

any help appreciated

---

### Post by seswho704 on 2010-12-07
I followed the same guide you did, and found neither hpricot or nokogiri would work. There is a gem called cherry, download and install it (for some reason it would not install remotely). cewl ran after installing cherry.

Don't forget to export the rubyopt.

---

### Post by 2fast4u on 2010-12-22
Install package ruby-full and it's ok

---

