---
title: "Perl : Failed to AUTOLOAD 'Tk::Widget::Graph'"
date: 2009-11-19
forum: General Help
---

### Post by ms020704 on 2009-11-19
Hello,
I just installed Ubuntu 9.10. I am practicing with Tk in Perl. I have installed all Tk Modules with Cspan, but when i try to run a simple program that uses Graph widget i get this error...

Assuming 'require Tk::Graph;' at pr03.pl line 13
Failed to AUTOLOAD 'Tk::Widget::Graph' at pr03.pl line 13

the code i am running is this I found in a magazine....
1   use Tk;
2  use Tk::Graph;
3
4   $mw = MainWindow->new;
5
6   my $data = {
7        Sleep   => 51,
8        Work    => 135,
9        Access  => 124,
10        mySQL   => 5
11   };
12
13   my $ca = $mw->Graph(
14                -type  => 'BARS',
15        )->pack(
16                -expand => 1,
17                -fill => 'both',
18        );
19
20   $ca->configure(-variable => $data);     # bind to data
21
22   # or ...
23
24   $ca->set($data);        # set data
25
26   MainLoop;

Any suggestion??  ... Thank you.

---

