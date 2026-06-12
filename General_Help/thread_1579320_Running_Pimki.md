---
title: "Running Pimki"
date: 2010-09-21
forum: General Help
---

### Post by BlakeGideon on 2010-09-21
Hi, I am trying to run pimki, but it is looking for an older version of rails. I'm at 2.3.8, its looking for 1.0.0! Any clue on how to get this app to run, I've installed all dependencies. Thanks for your help!

```
blake@x301:~/Depaul/pimki/pimki-2.0$ ruby pimki.rb 
/home/blake/Depaul/pimki/pimki-2.0/config/environment.rb:66:Warning: Gem::SourceIndex#search support for String patterns is deprecated, use #find_name
/usr/lib/ruby/1.8/rubygems.rb:827:in `report_activate_error': RubyGem version error: rails(2.3.8 not = 1.0.0) (Gem::LoadError)
	from /usr/lib/ruby/1.8/rubygems.rb:261:in `activate'
	from /usr/lib/ruby/1.8/rubygems.rb:68:in `gem'
	from /home/blake/Depaul/pimki/pimki-2.0/config/environment.rb:86
	from ./script/server:71:in `require'
	from ./script/server:71
	from pimki.rb:3:in `load'
	from pimki.rb:3
```

---

