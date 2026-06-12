---
title: "How to install Premailer?"
date: 2010-08-11
forum: General Help
---

### Post by quinthar on 2010-08-11
Hi!  I'm using Ubuntu 10.04 and I'm getting some errors installing Premailer; can you offer any tips?  Premailer is here:

[http://github.com/alexdunae/premailer/](http://github.com/alexdunae/premailer/)

I tried following the instructions, which boil down to:

```
sudo apt-get install ruby
gem sources -a http://gemcutter.org
sudo apt-get install rubygems1.9.1
sudo gem install premailer
```

However, the final step outputs the following:

```
Building native extensions.  This could take a while...
ERROR:  Error installing premailer:
	ERROR: Failed to build gem native extension.

/usr/bin/ruby1.9.1 extconf.rb
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
	from extconf.rb:1:in `<main>'


Gem files will remain installed in /var/lib/gems/1.9.1/gems/hpricot-0.8.2 for inspection.
Results logged to /var/lib/gems/1.9.1/gems/hpricot-0.8.2/ext/fast_xs/gem_make.out
```

That final logfile contains:

```
/usr/bin/ruby1.9.1 extconf.rb
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:1:in `<main>'
```

Any thoughts as to what this might mean?  I'm not hip to Ruby but it looks like it's missing some include file somewhere... Is this an obvious thing that has an obvious answer?  Thanks!

-david

---

### Post by ubunterooster on 2010-08-11
I am not sure why it is not working ( yes, I tried to figure out) then did a search on it. Web of Trust says it is a poorly rated site (see screenshot). If you do not know this program, I say it may be best to stay away from it.

See links for hosts' ratings:
[http://www.mywot.com/en/scorecard/premailer.dialect.ca](http://www.mywot.com/en/scorecard/premailer.dialect.ca)

[http://www.mywot.com/en/scorecard/downv.com](http://www.mywot.com/en/scorecard/downv.com)

---

