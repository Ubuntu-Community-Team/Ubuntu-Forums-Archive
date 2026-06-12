---
title: "pecl wont install pdflib"
date: 2009-09-16
forum: General Help
---

### Post by paxmanchris on 2009-09-16
the command I try to run:

sudo pecl install pdflib

the error i get:
configure: error: pdflib.h not found! Check the path passed to --with-pdflib=<PATH>. PATH should be the install prefix directory.
ERROR: `/tmp/pear/temp/pdflib/configure --with-pdflib=' failed


during the install i a get dialog:
 1. path to pdflib installation? : 

1-1, 'all', 'abort', or Enter to continue:

whats with this 1-1, 'all', 'abort' options?

I downloaded pdflib-2.1.7, untaring it, and using the path to the results as the input for this first dialog.. but no success.


are thery any difinive guides on installing this package for Ubuntu (Jaunty)..

---

### Post by CyberJack on 2009-09-22
I think that you need to install a version of pdflib from the pdflib website before you can install the pecl package. I found a post from April 2008 where someone tried to install it on fedora, and according to his steps he downloaded a package from the pdflib website: [http://www.linuxforums.org/forum/redhat-fedora-linux-help/114187-pdflib-installation.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/114187-pdflib-installation.html)

Have you tried tcpdf or fpdf? They are 2 php only solutions to create pdf files.
tcpdf works fine for my pdf creation needs.

---

### Post by paxmanchris on 2009-09-22
the post did not help. but i was able to get PDFlib to work.

thanks anyways.

---

### Post by pbr on 2010-02-12
> **paxmanchris said:**
> the post did not help. but i was able to get PDFlib to work.

thanks anyways.
paxmanchris - So... HOW were you able to get PDFlib to work?  What was it that finally fixed things for you?

Please let us know - these forums are as much about helping others as receiving help.

Thanks!
-pbr

---

### Post by paxmanchris on 2010-02-12
Ahh, its been a long time... and yes I should have said what I did.

well. instead of using PDFlib, i used FPDF (package: php-fpdf).

also for some reason, I needed to include the fpdf.php file in order to get it to work, here is example code:
[PHP]
require_once('/usr/share/php/fpdf/fpdf.php');
$pdf=new FPDF();
$pdf->AddPage();
$pdf->SetFont('Arial','B',16);
$pdf->Cell(40,10,'Hello World!');
$pdf->Output();
[/PHP]

this is taken from [http://fpdf.org/](http://fpdf.org/) where you can find documentation and other examples. 

so, I lied a little on how the fpdf suggestion did not help; it ended up being my solution.

--
as for the skinny on how I got in to this mess. I first started developing on a windows XAMPP system. where PHPlib worked just fine; but then I switch to a Linux server; couldn't for the life of me get PDF lib to work, had to reprogram. at first I was going to write a wrapper, but I did not have the time.

---

