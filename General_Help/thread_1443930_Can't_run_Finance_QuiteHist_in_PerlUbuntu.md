---
title: "Can't run Finance QuiteHist in Perl/Ubuntu"
date: 2010-03-31
forum: General Help
---

### Post by jeanc on 2010-03-31
Hi all,

I am relatively new to Ubuntu and to perl, and I cannot run the perl module called "Finance QuoteHist" in Ubuntu. Perl, as far as I know, would run in my terminal if I input the command line such as :~$ perl <script_name>.


Here are a few things that I did-

1. In the terminal, I typed in 
:~$ perl & 
to activate perl.

2. Then I also typed in several command lines to see whether it runs the module.
:~$ perl test1.pl
test1.pl contained the codes below, which I copied and pasted from the Perl Archive site called Cpan.

--------------------
 use Finance::QuoteHist;
  $q = Finance::QuoteHist->new
     (
      symbols    => [qw(IBM UPS AMZN)],
      start_date => '01/01/2008', # or 'one year ago', see Date::Manip
      end_date   => 'today',
     );

  # Quotes
  foreach $row ($q->quotes()) {
    ($symbol, $date, $open, $high, $low, $close, $volume) = @$row;
    ...
  }

hyperlink to Cpan:
[http://kobesearch.cpan.org/htdocs/Finance-QuoteHist/Finance/QuoteHist.html](http://kobesearch.cpan.org/htdocs/Finance-QuoteHist/Finance/QuoteHist.html)

----------------

What can I do to make this command work, so that I can get an access to the database? Thanks in advance for the help!

---

