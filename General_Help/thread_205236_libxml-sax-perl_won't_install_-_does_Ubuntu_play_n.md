---
title: "libxml-sax-perl won't install - does Ubuntu play nice with CPAN?"
date: 2006-06-28
forum: General Help
---

### Post by msemtd on 2006-06-28
One day, in a glorious possible future, Ubuntu and CPAN will coexist happily. Right now, all the machines that I upgraded to Dapper are rendered unusable due to the libxml-sax-perl atrocity...

Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.

I have XML::SAX already installed perfectly well with CPAN but I assume that dpkg knows nothing about it so wants to install its own version.

I use a lot of Perl modules and like other Perl users I quite often find that the modules in repositories are aeons out of date. As Perl users we naturally use CPAN to get our machines in a consistent state. Then something like this comes along and screws everything up for weeks on end.

This particular issue is reported all over the place and we get typical responses along the lines of "well, it works for me so there's nothing wrong" (a particularly blinkered view), "you played in /usr/local so I won't give you any support", or "There's nothing in the Debian policy that says CPAN should just work for you", but typically we find that Debian package maintainers just push the problem back to the user.

Is anything being done to make Ubuntu CPAN aware?

---

