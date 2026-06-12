---
title: "Ruby Gems are getting a &quot;No such file to load&quot; error"
date: 2010-05-26
forum: General Help
---

### Post by Randuin on 2010-05-26
My code is as follows

```
require 'rubygems'
require 'sinatra'

get '/hi' do
        "Hi"
end
```

The output I get is

```
main.rb:2:in `require': no such file to load -- sinatra (LoadError)
```

My gem list is

```
*** LOCAL GEMS ***

nokogiri (1.4.2)
rack (1.1.0)
sinatra (1.0)
```

gem environment

```
RubyGems Environment:
  - RUBYGEMS VERSION: 1.3.7
  - RUBY VERSION: 1.9.1 (2010-01-10 patchlevel 378) [x86_64-linux]
  - INSTALLATION DIRECTORY: /usr/lib/ruby/gems/1.9.1
  - RUBY EXECUTABLE: /usr/bin/ruby1.9.1
  - EXECUTABLE DIRECTORY: /usr/bin
  - RUBYGEMS PLATFORMS:
    - ruby
    - x86_64-linux
  - GEM PATHS:
     - /usr/lib/ruby/gems/1.9.1
     - /root/.gem/ruby/1.9.1
  - GEM CONFIGURATION:
     - :update_sources => true
     - :verbose => true
     - :benchmark => false
     - :backtrace => false
     - :bulk_threshold => 1000
  - REMOTE SOURCES:
     - http://rubygems.org/
```

my $PATH looks like this

```
/usr/lib/ruby/gems/1.9.1:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

I'm not sure why it's not finding any of the gems?

---

### Post by DenisShepelin on 2010-05-28
I hope it will help :) :
Add following lines to your .bashrc or .bash_profile:
```
export GEM_HOME="/usr/lib/ruby1.9.1/gems/1.9.1"
```

---

