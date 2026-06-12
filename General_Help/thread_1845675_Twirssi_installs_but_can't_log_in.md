---
title: "Twirssi installs but can't log in"
date: 2011-09-17
forum: General Help
---

### Post by GeekyAdam on 2011-09-17
I've been running irssi for a long time now and actually had twirssi running with it perfectly awhile ago, but just set up a new machine and can't get it to work.

```

01:15 ***   <(^)                   TWIRSSI v2.5.0
01:15 ***    (_(\           http://twirssi.com/ for full docs
01:15 ***     || ` Log in with /twitter_login, send updates with /tweet
01:15 *** Loading WWW::Shorten::TinyURL...


(here is where i do "/twitter_login [myusername]")


01:15 *** Error when creating object:   Can't locate Net/Twitter/Role/RetryOnError.pm in @INC (@INC contains:  /home/adam/.irssi/scripts /usr/share/irssi/scripts /usr/lib/perl/5.10  /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1  /usr/lib/perl5 /usr/share/perl5 /usr/share/perl/5.10  /usr/local/lib/site_perl .). at /usr/lib/perl5/Class/MOP.pm line 116
01:15   Class::MOP::load_first_existing_class('Net::Twitter::Role::RetryOnError') called at /usr/lib/perl5/Class/MOP.pm line 121
01:15   Class::MOP::load_class('Net::Twitter::Role::RetryOnError') called at /usr/share/perl5/Net/Twitter.pm line 44
01:15    Net::Twitter::__ANON__('Net::Twitter', 'API::REST', 'OAuth',  'API::Search', 'RetryOnError') called at /usr/share/perl5/Net/Twitter.pm  line 88
01:15    Net::Twitter::new('Net::Twitter', 'traits', 'ARRAY(0xad348e0)',  'consumer_key', 'BZVAvBma4GxdiRwXIvbnw', 'consumer_secret',  '0T5kahwLyb34vciGZsgkA9lsjtGCQ05vxVE2APXM', 'source', 'twirssi', ...)  called at /home/adam/.irssi/scripts/twirssi.pl line 581
01:15   eval {...} called at /home/adam/.irssi/scripts/twirssi.pl line 571
01:15   Irssi::Script::twirssi::cmd_login('geekyadam', 'Irssi::Irc::Server=HASH(0xadd5d48)', undef) called at -e line 0
01:15   eval {...} called at -e line 0
01:15 
01:15 *** Failed to create object!  Aborting.
```ubuntu server 10.04
Any ideas on what to do next?

---

### Post by sddhrthrt on 2012-03-10
Gah! Will someone put a solution for this, please? :P I am facing the *Exact* same problem. Do something, GuyS!!!

---

### Post by GeekyAdam on 2012-03-12
Just an update, still have the problem. Can't get twirssi to work.

---

