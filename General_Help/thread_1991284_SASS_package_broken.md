---
title: "SASS package broken?"
date: 2012-05-30
forum: General Help
---

### Post by gcaplan on 2012-05-30
Hi

Trying to get the SASS CSS pre-compiler to work on the latest version of Ubuntu server.

Installed the package, but when I run >sass --watch I get the error:

LoadError: no such file to load -- fssm
Run "gem install fssm" to get it.

The fssm gem installs ok, but sass --watch still throws the same error.

I've tried the development sass gem, same problem. No joy with the compass gem. I've also upgraded to Ruby 1.9.3 via the Brightbox repo.

That's as much as my limited sysadmin skills enable me to do. I'd very much appreciate some advice!

---

### Post by gcaplan on 2012-05-30
UPDATE: I've got watch working with compass, so this isn't so urgent. But I'd still like to get to the bottom of it if possible!

---

### Post by AK-Chopper on 2012-07-12
i have the same problem with Ubuntu 12.04

---

### Post by AK-Chopper on 2012-07-12
EDIT: an update to the latest version 3.1.20 helped as well. (at first it was blocked from the version 3.1.15 shipped with rubygems itself i think)

For me it worked to hardwire the path to fssm (because the relative path was wrong)

vim /usr/lib/ruby/vendor_ruby/sass/../sass/plugin/compiler.rb

go to line 239 and change "dir" to the path where you find your fssm (i had two since i tried installing it as well in 
/var/lib/gems/1.8/gems/sass-3.1.7/vendor/fssm/lib/ 
and
/var/lib/gems/1.8/gems/fssm-0.2.9/lib/ it does not matter which one you take the second one was the latest with a notice that the fssm project is dead and now moved to guard/listen )

 ```
  def watch(individual_files = [])
      update_stylesheets(individual_files)

      begin
        require 'fssm'
      rescue LoadError => e
        dir = '/var/lib/gems/1.8/gems/fssm-0.2.9/lib'
        if $LOAD_PATH.include?(dir)
```

---

