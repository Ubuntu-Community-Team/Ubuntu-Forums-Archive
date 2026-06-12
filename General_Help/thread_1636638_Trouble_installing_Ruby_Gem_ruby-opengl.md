---
title: "Trouble installing Ruby Gem ruby-opengl"
date: 2010-12-03
forum: General Help
---

### Post by Exp HP on 2010-12-03
I'm having a little trouble with installing the ruby-opengl gem on Lucid Lynx.

I made sure to get all the necessary packages from the repositories:
ruby, rdoc, ri, ruby1.8-dev, libgl1-mesa-dri, libgl1-mesa-dev, libglu1-mesa, libglu1-mesa-dev, freeglut3, freeglut3-dev, xorg-dev

> [mike:/home/mike] $ sudo gem install ruby-opengl
Building native extensions.  This could take a while...
ERROR:  Error installing ruby-opengl:
    ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 -rubygems /var/lib/gems/1.8/gems/rake-0.8.7/bin/rake RUBYARCHDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.60.1/lib RUBYLIBDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.60.1/lib
/usr/bin/ruby1.8 mkrf_conf.rb
(in /var/lib/gems/1.8/gems/ruby-opengl-0.60.1)
rake
rake aborted!
Command failed with status (127): [rake...]

(See full trace by running task with --trace)


Gem files will remain installed in /var/lib/gems/1.8/gems/ruby-opengl-0.60.1 for inspection.
Results logged to /var/lib/gems/1.8/gems/ruby-opengl-0.60.1/gem_make.outThe output of '**ruby -v**' is 'ruby 1.8.7 (2010-01-10 patchlevel 249) [i486-linux]'

I tried running 'gem install rake' and 'gem install rkmf' to make sure I had them.  Both succeeded, but 'gem install ruby-opengl' continues to fail.

By the way, despite what the error suggests, gem has no '--trace' option.  I guess that error message is produced by another program that gem calls?

---

### Post by Exp HP on 2010-12-03
I figured it out.

```
apt-get install rake
```Yup, there's a rake package in the repositories.
This is in addition to the rake GEM that the [ruby-opengl site]("http://ruby-opengl.rubyforge.org/build_install.html") suggests getting.
The rake gem wasn't enough for me.  I needed the rake package.

So what purpose does the rake gem have?*  No idea*.

**EDIT:** You know what, I'm really puzzled about this. Why doesn't the gem work? Both the gem and package are the same version of rake (0.8.7), Sure, installing the package puts an executable in PATH... but so does placing a symlink to '/var/lib/gems/1.8/rake-0.8.7/bin/rake' in /usr/local/bin. I tried doing that, and it didn't fix the error.

---

