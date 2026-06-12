---
title: "Problems installing rbot on 10.04"
date: 2010-05-11
forum: General Help
---

### Post by Apewall on 2010-05-11
I've installed rbot from the lucid universe and now receive.
```

D, [2010/05/11 13:16:04#5115] DEBUG -- ircbot.rb:124: debug test
I, [2010/05/11 13:16:04#5115]  INFO -- ircbot.rb:125: log test
W, [2010/05/11 13:16:04#5115]  WARN -- ircbot.rb:126: warning test
E, [2010/05/11 13:16:05#5115] ERROR -- ircbot.rb:127: error test
F, [2010/05/11 13:16:05#5115] FATAL -- ircbot.rb:128: fatal test
D, [2010/05/11 13:16:05#5115] DEBUG -- rbotconfig.rb:28: trying to load rubygems
D, [2010/05/11 13:16:05#5115] DEBUG -- rbotconfig.rb:35: loaded rubygems, looking for rbot version 0.9.14 (rbot-0.9.14)
D, [2010/05/11 13:16:05#5115] DEBUG -- rbotconfig.rb:37: got gem
D, [2010/05/11 13:16:05#5115] DEBUG -- rbotconfig.rb:43: not installed via rubygems
/usr/local/lib/site_ruby/1.8/rbot/load-gettext.rb:25: undefined method `add_default_locale_path' for main:Object (NoMethodError)
        from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
        from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `require'
        from /usr/local/lib/site_ruby/1.8/rbot/ircbot.rb:135
        from /usr/bin/rbot:94:in `require'
        from /usr/bin/rbot:94

```

not sure where to go from here.

---

### Post by blazemore on 2010-05-13
You need to [manually install rubygems]("apt:rubygems"). For some reason it's not listed as a dependency: This is a bug.

---

### Post by virtualsid on 2010-07-27
I've got the same issue as the original poster - same errors (Except the original '/usr/local' bit is '/usr/lib/ruby/1.8/rbot/ircbot.rb:135' on mine).

I do have rubygems already installed:

```

$ dpkg -l rubygems rbot
||/ Name             Version          Description
+++-================-================-================================================
ii  rbot             0.9.14-2ubuntu1  IRC bot written in ruby
ii  rubygems         1.3.5-1ubuntu2   package management framework for Ruby libraries/

```

I've removed my old .rbot directory, no luck.

I've checked the path to rbot, and it all seems to be correct...

```

$ which rbot
/usr/bin/rbot
$ dpkg -S /usr/bin/rbot
rbot: /usr/bin/rbot

```

Any ideas on where to go next? I'm guessing it must be something fairly simple, as it stops rbot from running even without an existing configuration... I've purged it, and reinstalled it too - not that I thought that would make much of a difference!

---

