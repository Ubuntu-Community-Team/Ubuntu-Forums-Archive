---
title: "perl use IO::Socket::SSL;"
date: 2009-06-25
forum: General Help
---

### Post by H4F on 2009-06-25
#!/usr/bin/perl -w
 use IO::Socket::SSL;

    my $client = new IO::Socket::SSL("www.example.com:https");

    if (defined $client) {
        print $client "GET / HTTP/1.0\r\n\r\n";
        print <$client>;
        close $client;
    } else {
        warn "I encountered a problem: ",
          IO::Socket::SSL::errstr();
    }

Can't locate IO/Socket/SSL.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./test.pl line 2.
BEGIN failed--compilation aborted at ./test.pl line 2.

:( 
Is there any think wrong. I just can't run this script cause it can't find
 use IO::Socket::SSL;

---

### Post by H4F on 2009-06-26
well the solution is: 
sudo apt-get install libio-socket-ssl-perl

[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by arthur.duarte on 2010-11-22
Thank you man.

This helped me =)

---

