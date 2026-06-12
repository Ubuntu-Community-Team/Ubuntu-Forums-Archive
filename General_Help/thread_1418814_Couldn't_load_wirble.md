---
title: "Couldn't load wirble"
date: 2010-03-01
forum: General Help
---

### Post by Thomas Garman on 2010-03-01
I am running Karmic and I use irb (ruby, rubygems)...

Even though I installed irb and rubygems and used sudo gem install wirble from my .irbrc file..

# Script 1.1 - .irbrc
# irb initialization script

# Include support for tab completion:

require 'irb/completion'

begin 
   require 'rubygems'
 rescue LoadError => err
   warn "Couldn't load RubyGems: #{err}"
 end

begin 
  # load and initialize wirble
  require 'wirble'
  Wirble.init

Wirble.colorize
rescue LoadError => err
  warn "Couldn't load Wirble: #{err}"
end

I GET THE ERROR MESSAGE "Couldn't load ruby gems" and "Couldn't load wirble"

Does anyone know why this would be happening?

---

