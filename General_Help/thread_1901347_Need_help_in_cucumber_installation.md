---
title: "Need help in cucumber installation"
date: 2011-12-28
forum: General Help
---

### Post by sarge1238 on 2011-12-28
Hi All,

I am a newbee in ubuntu and over to that i want to learn cucumber.
I did install ubuntu 11.10 using usb.

* i ran the following because i knew cucumber can be install only after ruby [though i don't have any sequential list of steps]
sudo apt-get install ruby1.9.1
which got executed successfully 
* now i am lost because i search on google and found every body says something else and i tried most of them and nothing works.

===========================================================
sudo gem install gherkin <<-- What ever word [related to cucumber installation] i mention after install i get the same error
===========================================================
Building native extensions.  This could take a while...
ERROR:  Error installing gherkin:
    ERROR: Failed to build gem native extension.

/usr/bin/ruby1.9.1 extconf.rb
<internal:lib/rubygems/custom_require>:29:in `require': no such file to load -- mkmf (LoadError)
    from <internal:lib/rubygems/custom_require>:29:in `require'
    from extconf.rb:1:in `<main>'


Gem files will remain installed in /var/lib/gems/1.9.1/gems/json-1.6.4 for inspection.
Results logged to /var/lib/gems/1.9.1/gems/json-1.6.4/ext/json/ext/parser/gem_make.out

===========================================================
Pleas guide me, and let me know what I am missing
Regards,
Rajiv

---

### Post by sarge1238 on 2011-12-28
its very simple i got it 
please follow the below steps:

===========================
sudo aptitude install ruby1.8-devsudo aptitude install rake
sudo aptitude install rubygems1.8
sudo gem install gherkin cucumber

===========================

If you got an error saying aptitude command not found, no worries 
Just Run ::
sudo apt-get install aptitude

Please feel free to msg me for any issue related to cucumber installation on Ubuntu
:popcorn:

---

