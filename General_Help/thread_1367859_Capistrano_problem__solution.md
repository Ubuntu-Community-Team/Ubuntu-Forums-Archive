---
title: "Capistrano problem / solution"
date: 2009-12-30
forum: General Help
---

### Post by Hakachukai on 2009-12-30
Just thought I'd throw this out there. It stumped me for a while.

I'm running ubuntu 9.04

I installed: 
ruby1.8
rubygems1.8
libruby1.8

Then used gem to install capistrano (ruby gem)

When I tried to run capistrano I got this cryptic (atleast to me) error message:

"custom_require.rb:36:in `gem_original_require': no such file to load -- jopenssl (LoadError)"

So, someone on IRC explained that:

"custom_require.rb is part of rubygems, which hooks into the loading of libraries. gem_original_require is the original require method (before rubygems hooked it), which gets called if rubygems couldn't find any matching gem. jopenssl obviously is the file/library that was tried to load. and why it fails in this particular case: no idea, probably because it is meant for jruby"

anyway... the solution was to install the "ruby-full" package.

Hope that helps someone out there somewhere

---

