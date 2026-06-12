---
title: "ruby1.8 versus ruby 1.9.1: require of local file"
date: 2012-02-22
forum: General Help
---

### Post by djconnel on 2012-02-22
I'm running 11.10 Oneric, but am having a problem upgrading from default Ruby 1.8 to recommended 1.9.

Here's a local file, Test2.rb:

```
class Test2
  puts "hello, from Test2!"
end
```

And here's Test.rb:

```
require 'Test2'
puts RUBY_VERSION

```

The important line is the first one: the *require*.

I can run from 1.8 fine:

```
% ruby1.8 < Test.rb
hello, from Test2!
1.8.7
```

But from 1.9.1....

```
% ruby1.9.1  < Test.rb
<internal:lib/rubygems/custom_require>:29:in `require': no such file to load -- Test2 (LoadError)
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from -:1:in `<main>'
```


Non-local requires are fine:

```
% ruby1.9.1 << EOF
require 'rubygems'
EOF
% ruby1.8 << EOF
require 'rubygems'
EOF
```

Same problem running irb, where here I'm manually switching between Ruby versions, and it works with 1.8 but not 1.9:

```
% irb
irb(main):001:0> puts RUBY_VERSION
1.8.7
=> nil
irb(main):002:0> require 'Test2'
hello, from Test2!
=> true
irb(main):003:0> exit
% sudo update-alternatives --config ruby
[sudo] password for djconnel: 
There are 2 choices for the alternative ruby (providing /usr/bin/ruby).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/ruby1.8     50        auto mode
  1            /usr/bin/ruby1.8     50        manual mode
  2            /usr/bin/ruby1.9.1   10        manual mode

Press enter to keep the current choice[*], or type selection number: 2
update-alternatives: using /usr/bin/ruby1.9.1 to provide /usr/bin/ruby (ruby) in manual mode.
% irb
irb(main):001:0> puts RUBY_VERSION
1.9.2
=> nil
irb(main):002:0> require 'Test2'
LoadError: no such file to load -- Test2
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from (irb):2
	from /usr/bin/irb:12:in `<main>'
irb(main):003:0> exit
% sudo update-alternatives --config ruby
There are 2 choices for the alternative ruby (providing /usr/bin/ruby).

  Selection    Path                Priority   Status
------------------------------------------------------------
  0            /usr/bin/ruby1.8     50        auto mode
  1            /usr/bin/ruby1.8     50        manual mode
* 2            /usr/bin/ruby1.9.1   10        manual mode

Press enter to keep the current choice[*], or type selection number: 1
update-alternatives: using /usr/bin/ruby1.8 to provide /usr/bin/ruby (ruby) in manual mode.
% irb
irb(main):001:0> puts RUBY_VERSION
1.8.7
=> nil
irb(main):002:0> require 'Test2'
hello, from Test2!
=> true
```

Any help?

thanks!
Dan

---

### Post by djconnel on 2012-02-22
Apologies: I see now this probably should have been in the Programming Talk forum.

---

### Post by djconnel on 2012-02-23
Problem "solved"...

"." is not in $LOAD_PATH in 1.9.1 (sic), but it is in 1.8.

so I add the following to the first line in the script:

$LOAD_PATH << "."

and it runs under each.

Now the question becomes why "." isn't in the load path under 1.9.1...

Apparently this is considered a "bug": [link to Debian.Bugs.Dist post](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/9bc94d44d9d5a4e7)

---

