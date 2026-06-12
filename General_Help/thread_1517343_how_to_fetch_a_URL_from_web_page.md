---
title: "how to fetch a URL from web page"
date: 2010-06-24
forum: General Help
---

### Post by abjdiat on 2010-06-24
I used this perl script to fetch the content of some web pages, in the content there is one link I would like to look for and print .. mediafire.com/$$$$$$$, how can i do that 
```
#! /usr/bin/perl -w

use strict;
# use LWP::Simple;
use LWP::UserAgent;

my $ua = new LWP::UserAgent;
$ua->timeout(120);
my $url='http://amon2.linkatty.com/0e33e5.html';
my $request = new HTTP::Request('GET', $url);
my $response = $ua->request($request);
my $content = $response->content();
```

I tried this bash command but i prints all links, the link i want has mediafire as a domain , can you help me ?
```
wget -O - http://amon2.linkatty.com/614bb7.html | \grep -o '<a href=['"'"'"][^"'"'"']*['"'"'"]' | \sed -e 's/^<a href=["'"'"']//' -e 's/["'"'"']$//'
```

---

### Post by gmargo on 2010-06-25
Since you're already using perl, you can use the HTML::TreeBuilder module to parse the HTML page and find the link.

---

