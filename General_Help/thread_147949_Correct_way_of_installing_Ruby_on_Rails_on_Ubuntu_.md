---
title: "Correct way of installing Ruby on Rails on Ubuntu 5.10?"
date: 2006-03-21
forum: General Help
---

### Post by LordMerlin on 2006-03-21
Can someone please tell me what the correct way is of getting ROR, and especially Ruby Gems installed on Ubuntu 5.10, clean install? I want to start learning ROR, but can't even get it installed. I searched the forums high and low, and it seems like there's a lot of problems getting it to work. Needless to say, I tried to follow them all, but it seems each instance is rather unique.

I'm trying to install it on a Xeon with SCSI drives, not that that should make a difference, but I noticed it uses the i486 instead of the i686 folder in some instances. 

so far, I've got ruby 1.8.11 installed, but gems gives me issues. This is the link I'm following, as I need to get it working on my production server on a VPS hosting account as well: [http://wiki.rubyonrails.com/rails/pages/HowtoInstallAndRunRubyOnRailsOnCpanel]("http://wiki.rubyonrails.com/rails/pages/HowtoInstallAndRunRubyOnRailsOnCpanel")

I got stuck where Gems couldn't find zlib.so, and tried to follow this thread, [http://rubyforge.org/tracker/index.php?func=detail&aid=2671&group_id=126&atid=576]("http://rubyforge.org/tracker/index.php?func=detail&aid=2671&group_id=126&atid=576"), but got a new problem:

```
root@Gimbli:/usr/local/src/rubygems-0.8.11# find / -name zlib.so
/usr/lib/ruby/1.8/i486-linux/zlib.so
/usr/lib/python2.4/lib-dynload/zlib.so
/media/hdb3/usr/lib/zlib.so
/media/hdb3/usr/lib/python2.3/lib-dynload/zlib.so
root@Gimbli:/usr/local/src/rubygems-0.8.11# export RUBYLIB=/usr/lib/ruby/1.8/i486-linux/
root@Gimbli:/usr/local/src/rubygems-0.8.11# gem install rails
/usr/local/lib/ruby/1.8/yaml.rb:87: uninitialized constant YAML::Syck::Resolver (NameError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:6
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:1
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:61:in `manage_gems'
        from /usr/local/bin/gem:4
``` 

So, my question is, what is the correct way of installing ROR & Gems?

---

### Post by wannabelinuxconvert on 2006-03-21
Hi LordMerlin,

[http://fo64.com/articles/2005/10/20/rails-on-breezy]("http://fo64.com/articles/2005/10/20/rails-on-breezy")

I've used the above link several times to install Ruby, Ruby Gems and Rails and it works like a charm.

Hope it helps and good luck :mrgreen: 

Mic

---

### Post by dport113 on 2006-04-10
The aforementioned link is not correct in installing FastCGI support, some additional modifications to apaches configuration will have to be made to use the FastCGI handler rather than the apache CGI handler.

You would also need to enable the FastCGI handler:
'sudo a2enmod fcgid'

Also install the Ruby fastCGI bindings:
'sudo apt-get install libfcgi-ruby1.8'

Modify .htaccess on a per site/virtual site basis:
Change:
AddHandler fastcgi-script .fcgi
To: 
AddHandler fcgid-script .fcgi

And also change:
RewriteRule ^(.*)$ dispatch.cgi [QSA,L]
To:
RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]

Configure fcgi:
'sudo cd /etc/apache2/mods-enabled'
'sudo nano fcgid.conf'

You&#8217;ll want to include the following in the file:
These options are pretty standard you might need to adjust some, though I think
these should be fine for most applications.
<IfModule mod_fcgid.c>
  AddHandler fcgid-script .fcgi
  SocketPath /var/lib/apache2/fcgid/sock
  DefaultInitEnv RAILS_ENV production
  IdleTimeout 60
  ProcessLifeTime 6000
  MaxProcessCount 32
  DefaultMaxClassProcessCount 2
  IPCConnectTimeout 6
  IPCCommTimeout 6
</IfModule>

Hope this sheds some light on RoR with FastCGI.

---

### Post by LordMerlin on 2006-04-24
[quote=wannabelinuxconvert]Hi LordMerlin,

[http://fo64.com/articles/2005/10/20/rails-on-breezy]("http://fo64.com/articles/2005/10/20/rails-on-breezy")

I've used the above link several times to install Ruby, Ruby Gems and Rails and it works like a charm.

Hope it helps and good luck :mrgreen: 

Mic[/quote]

I have tried it, but keep on getting this:

lordmerlin@Gimbli:~/rubygems-0.8.11$ sudo gem install rubygems-update
Password:
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:9
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:1
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:61:in `manage_gems'
        from /usr/local/bin/gem:4
lordmerlin@Gimbli:~/rubygems-0.8.11$

Running sudo apt-get install zlib doesn't work. Any suggestions?

---

