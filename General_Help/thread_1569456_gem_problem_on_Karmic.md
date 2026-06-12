---
title: "gem problem on Karmic?"
date: 2010-09-06
forum: General Help
---

### Post by meburke on 2010-09-06
I get the following error trying to use gem to install anything:

ERROR:  While executing gem ... (URI::InvalidURIError)
    bad URI(is not URI?): [http://localhost:4001](http://localhost:4001) 

I'm on Karmic.

gem -v reports 1.3.5

apt says I have the latest version of gem

I have no idea how to troubleshoot gem and I would be grateful for any help.

Thanks,

Mike

---

### Post by bradleyd on 2010-09-06
what do you get when you run gem --debug install package_name

Are you running through a proxy?

---

### Post by meburke on 2010-09-06
I get:
root@bostrom:~# gem --debug install gemcutter
Exception `NameError' at /usr/lib/ruby/1.9.1/rubygems/command_manager.rb:161 - uninitialized constant Gem::Commands::InstallCommand
Exception `LoadError' at /usr/lib/ruby/1.9.1/rubygems/gem_openssl.rb:40 - no such file to load -- openssl
Exception `Gem::LoadError' at /usr/lib/ruby/1.9.1/rubygems.rb:827 - Could not find RubyGem test-unit (>= 0)

Exception `URI::InvalidURIError' at /usr/lib/ruby/1.9.1/uri/common.rb:156 - bad URI(is not URI?): [http://localhost:4001](http://localhost:4001) 
ERROR:  While executing gem ... (URI::InvalidURIError)
    bad URI(is not URI?): [http://localhost:4001](http://localhost:4001) 
	/usr/lib/ruby/1.9.1/uri/common.rb:156:in `split'
	/usr/lib/ruby/1.9.1/uri/common.rb:174:in `parse'
	/usr/lib/ruby/1.9.1/uri/common.rb:626:in `parse'
	/usr/lib/ruby/1.9.1/rubygems/remote_fetcher.rb:202:in `get_proxy_from_env'
	/usr/lib/ruby/1.9.1/rubygems/remote_fetcher.rb:66:in `initialize'
	/usr/lib/ruby/1.9.1/rubygems/remote_fetcher.rb:44:in `new'
	/usr/lib/ruby/1.9.1/rubygems/remote_fetcher.rb:44:in `fetcher'
	/usr/lib/ruby/1.9.1/rubygems/spec_fetcher.rb:52:in `initialize'
	/usr/lib/ruby/1.9.1/rubygems/spec_fetcher.rb:37:in `new'
	/usr/lib/ruby/1.9.1/rubygems/spec_fetcher.rb:37:in `fetcher'
	/usr/lib/ruby/1.9.1/rubygems/dependency_installer.rb:99:in `find_gems_with_sources'
	/usr/lib/ruby/1.9.1/rubygems/dependency_installer.rb:192:in `find_spec_by_name_and_version'
	/usr/lib/ruby/1.9.1/rubygems/dependency_installer.rb:213:in `install'
	/usr/lib/ruby/1.9.1/rubygems/commands/install_command.rb:118:in `block in execute'
	/usr/lib/ruby/1.9.1/rubygems/commands/install_command.rb:115:in `each'
	/usr/lib/ruby/1.9.1/rubygems/commands/install_command.rb:115:in `execute'
	/usr/lib/ruby/1.9.1/rubygems/command.rb:257:in `invoke'
	/usr/lib/ruby/1.9.1/rubygems/command_manager.rb:132:in `process_args'
	/usr/lib/ruby/1.9.1/rubygems/command_manager.rb:102:in `run'
	/usr/lib/ruby/1.9.1/rubygems/gem_runner.rb:58:in `run'
	/usr/bin/gem:21:in `<main>'
root@bostrom:~# 

(I didn't even know there was a --debug option. Can you also direct me to some good gem tutorials?)

Thanks,

Mike

---

### Post by bradleyd on 2010-09-06
you need to ```
apt-get install libopenssl-ruby
``` 
Then try it again.

---

### Post by meburke on 2010-09-07
Slightly new status: I tried to remove ruby1.9.1 and rubygems1.9.1 because all the docs I see are for ruby1.8. I somehow messed that up beautifully!

I get the following message trying to install rubygems1.8:

root@bostrom:~# apt-get install rubygems1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rubygems1.8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up rubygems1.8 (1.3.5-1ubuntu2) ...
update-alternatives: error: alternative gem can't be master: it is a slave of ruby
dpkg: error processing rubygems1.8 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rubygems1.8
E: Sub-process /usr/bin/dpkg returned an error code (1)

I presume this means the post-install script has an error.

I tried to fix it:

update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby1.8 400 \
> --slave   /usr/bin/ri ri /usr/bin/ri1.8 \
> --slave   /usr/bin/erb erb /usr/bin/erb1.8 \
> --slave   /usr/bin/rdoc rdoc /usr/bin/rdoc1.8 \
> --slave   /usr/bin/gem gem /usr/bin/gem1.8 \
> --slave   /usr/bin/irb irb /usr/bin/irb1.8 \
> --slave   /usr/share/man/man1/ruby.1.gz ruby.1.gz /usr/share/man/man1/ruby1.8.1.gz \
> --slave   /usr/share/man/man1/gem.1.gz gem.1.gz /usr/share/man/man1/gem1.8.1.gz \ 
> --slave   /etc/bash_completion.d/gem bash_completion_gem /etc/bash_completion.d/gem1.8

Now when I try to install I get:

root@bostrom:~# gem install gemcutter
ERROR:  While executing gem ... (URI::InvalidURIError)
    bad URI(is not URI?): [http://localhost:4001](http://localhost:4001)

So I'm back to a known problem, right?

Here is the debug output (libopenssl-ruby is installed and newest):

root@bostrom:~# gem --debug install gemcutter
Exception `NameError' at /usr/lib/ruby/1.8/rubygems/command_manager.rb:161 - uninitialized constant Gem::Commands::InstallCommand
Exception `Gem::LoadError' at /usr/lib/ruby/1.8/rubygems.rb:827 - Could not find RubyGem test-unit (>= 0)

Exception `URI::InvalidURIError' at /usr/lib/ruby/1.8/uri/common.rb:436 - bad URI(is not URI?): [http://localhost:4001](http://localhost:4001) 
ERROR:  While executing gem ... (URI::InvalidURIError)
    bad URI(is not URI?): [http://localhost:4001](http://localhost:4001) 
	/usr/lib/ruby/1.8/uri/common.rb:436:in `split'
	/usr/lib/ruby/1.8/uri/common.rb:485:in `parse'
	/usr/lib/ruby/1.8/rubygems/remote_fetcher.rb:202:in `get_proxy_from_env'
	/usr/lib/ruby/1.8/rubygems/remote_fetcher.rb:66:in `initialize'
	/usr/lib/ruby/1.8/rubygems/remote_fetcher.rb:44:in `new'
	/usr/lib/ruby/1.8/rubygems/remote_fetcher.rb:44:in `fetcher'
	/usr/lib/ruby/1.8/rubygems/spec_fetcher.rb:52:in `initialize'
	/usr/lib/ruby/1.8/rubygems/spec_fetcher.rb:37:in `new'
	/usr/lib/ruby/1.8/rubygems/spec_fetcher.rb:37:in `fetcher'
	/usr/lib/ruby/1.8/rubygems/dependency_installer.rb:99:in `find_gems_with_sources'
	/usr/lib/ruby/1.8/rubygems/dependency_installer.rb:192:in `find_spec_by_name_and_version'
	/usr/lib/ruby/1.8/rubygems/dependency_installer.rb:213:in `install'
	/usr/lib/ruby/1.8/rubygems/commands/install_command.rb:118:in `execute'
	/usr/lib/ruby/1.8/rubygems/commands/install_command.rb:115:in `each'
	/usr/lib/ruby/1.8/rubygems/commands/install_command.rb:115:in `execute'
	/usr/lib/ruby/1.8/rubygems/command.rb:257:in `invoke'
	/usr/lib/ruby/1.8/rubygems/command_manager.rb:132:in `process_args'
	/usr/lib/ruby/1.8/rubygems/command_manager.rb:102:in `run'
	/usr/lib/ruby/1.8/rubygems/gem_runner.rb:58:in `run'
	/usr/bin/gem:21

Thanks for your help,

Mike

---

### Post by meburke on 2010-09-07
Added NOTE: I'm simply trying to set up Jeckyll, but I would like my ruby environment to work for rails and app development as well.

Thanks again,

Mike

---

### Post by bradleyd on 2010-09-07
your package does not know where your gems are.  You can try setting gem paths or, what I would do, remove gem from ubuntu repo and grab the tar.gz from rubygems and install from source. This will nstall /usr/bin/gem1.8  ---try install via this

---

