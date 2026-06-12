---
title: "Trying to revert from ruby 1.9.1 to 1.8.6"
date: 2009-09-15
forum: General Help
---

### Post by agm_ultimatex on 2009-09-15
I installed ruby 1.9.1 from source. I removed all the directories listed when running whereis ruby. Im now at the point where ive ran both 
sudo apt-get install ruby rdoc irb 
sudo aptitude install ruby

When i try to run ruby -v I get the following error.

The program 'ruby' is currently not installed.  You can install it by typing:
sudo apt-get install ruby
bash: ruby: command not found

Any suggestions?

---

### Post by falconindy on 2009-09-15
So you installed it from source, and then deleted it and now you're trying to install it from the repositories?

Try installing the package "ruby-1.8".

---

### Post by agm_ultimatex on 2009-09-15
Had a look under synaptic package manager, and that is checked as installed. Its wierd. When i intially removed stuff, and was trying to run ruby (to see that it wasnt being picked up) it kept saying "bash:/usr/local/lib/ruby: not found" or something like that. After trying a couple different things, the whereis ruby came up with more results, so i removed those, and here we are.

---

### Post by agm_ultimatex on 2009-09-15
bump, any suggestions? I also tried running:

sudo apt-get install ruby-dev1.8 but it said its already installed.

---

### Post by agm_ultimatex on 2009-09-15
I got it to work. I did a purge of just about everything i could think of.

sudo apt-get purge ruby
sudo apt-get purge ruby1.8 rdoc irb
sudo apt-get purge ruby-dev

Then i followed the install command on ruby-lang
sudo apt-get install ruby rdoc irb

ruby -v in command brings me 1.8.7 :)

---

