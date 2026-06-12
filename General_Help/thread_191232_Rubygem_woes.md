---
title: "Rubygem woes"
date: 2006-06-07
forum: General Help
---

### Post by LodeRunner on 2006-06-07
I have installed libsqlite0-dev, ruby1.8-dev, and build-essential, and I still cannot get the SQLite-Ruby interface to work.   

After installing each package, the error changed to something different.  After build-essential, it changed to a "installation success" but with errors:

> Successfully installed sqlite-ruby-2.2.3
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': no such file to load -- rdoc/rdoc (LoadError)
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/site_ruby/1.8/rubygems/doc_manager.rb:43:in `generate_rdoc'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:215:in `execute'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:214:in `execute'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:153:in `execute'
        from /usr/local/lib/site_ruby/1.8/rubygems/command.rb:49:in `invoke'
        from /usr/local/lib/site_ruby/1.8/rubygems/cmd_manager.rb:94:in `process_args'
        from /usr/local/lib/site_ruby/1.8/rubygems/cmd_manager.rb:67:in `run'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_runner.rb:13:in `run'
        from /usr/bin/gem:17


Note that Rubygems itself appeared to install perfectly without any errors whatsoever. 

When I try running a test script, I get the same error one gets when one doesn't have the SQLite-Ruby Rubygem installed at all:

> test.rb:1:in `require': no such file to load -- sqlite (LoadError)
        from test.rb:1


So, what's going on here exactly?  Has anyone managed to get SQLite and Ruby talking to each other?  Should I compile from source?

Right now I'm running my scripts on XP, which just feels so... *wrong*.

---

