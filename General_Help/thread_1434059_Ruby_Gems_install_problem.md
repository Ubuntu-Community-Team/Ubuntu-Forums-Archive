---
title: "Ruby Gems install problem"
date: 2010-03-19
forum: General Help
---

### Post by zeemy23 on 2010-03-19
Hello, I've been trying to install ruby on rails on my ubuntu 8.10 system

I got ruby gems installed, but then found that when I tried to install a Gem, I received this error.

sudo gem install passenger
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- zlib (LoadError)
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:10
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/format.rb:9
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/installer.rb:11
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/dependency_installer.rb:3
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/commands/install_command.rb:4
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:167:in `load_and_instantiate'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:88:in `[]'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:144:in `find_command'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:131:in `process_args'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:102:in `run'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/gem_runner.rb:58:in `run'
    from /usr/local/bin/gem:21


What's wrong?
Thanks for your help,
zeem

---

### Post by n0dix on 2010-03-19
You need the zlib devel package,
apt-get install zlib1g-dev
# or something like that

---

### Post by zeemy23 on 2010-03-19
Thanks for your advice, but sadly it didn't help. Looks like it was already installed.

azeem@azeem-laptop:~$ sudo apt-get install zlib1g-dev
Reading package lists... Done
Building dependency tree        
Reading state information... Done
zlib1g-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
azeem@azeem-laptop:~$ gem install rails
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- zlib (LoadError)
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:10
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/format.rb:9
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/installer.rb:11
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/dependency_installer.rb:3
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/commands/install_command.rb:4
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:167:in `load_and_instantiate'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:88:in `[]'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:144:in `find_command'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:131:in `process_args'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:102:in `run'
    from /usr/local/lib/ruby/site_ruby/1.8/rubygems/gem_runner.rb:58:in `run'
    from /usr/local/bin/gem:21

---

### Post by n0dix on 2010-03-19
And if you install zlib-devel or look in synaptics for this package and installed.

---

