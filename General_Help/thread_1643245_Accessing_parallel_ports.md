---
title: "Accessing parallel ports"
date: 2010-12-11
forum: General Help
---

### Post by tumoheat on 2010-12-11
Hello, I am trying to write to the parallel port pins from a Perl  program running Ubuntu Linux, to light up led's on a bread board. I've  already accomplished this on this same box using a C program, but I  cannot get my code below to work. I believe the problem is with the  line: 
  $parport = Device::ParallelPort->new('auto:0');
  I've tried different variables between the ('') ticks, but nothing  has worked. I use Perl on my web pages for forms, but this has me  stumped. Any help would be appreciated. Code is below:
  [SIZE=-1]#!/usr/bin/perl  require "subparseform.lib"; &Parse_Form;  print "Set-cookie: cart_id=1234; user_id=123;\n";    print "Content-type: text/html\n\n";  use strict; use CGI;    use Device::ParallelPort;  # use Device::ParallelPort::drv; # use Device::ParallelPort::drv::linux # use Device::ParallelPort::drv::parport  # Set up your parallel port object and tell it what driver to use.  #my $parport = Device::ParallelPort->new('auto:0');  print "It works!!!";  [/SIZE]

---

### Post by gordintoronto on 2010-12-11
You might get better results in the Programming Talk forum.  Also, you should use the CODE and /CODE formatting.

---

