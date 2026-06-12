---
title: "Trouble with a2ps (ubuntu 9.04)"
date: 2009-10-26
forum: General Help
---

### Post by grkuntzmd on 2009-10-26
I cannot get a2ps to recognize my a2ps-site.cfg changes. I added the following line to the end of my config file, but a2ps keeps send 2-up pages to my default printer.

Options: -1 --columns=1 --rows=1 --landscape --chars-per-line=150 --borders=yes --line-numbers=1 --font-size=8 --lines-per-page=60

Here is the output of 'a2ps --list=defaults'

                       Configuration status of a2ps 4.14
                       =================================

Sheets:
-------
  medium          = Letter (libpaper), landscape
  page layout     = 1 x 1, rows first
  borders         = yes
  file alignment  = page
  interior margin = 0

Virtual pages:
--------------
  number lines         = each line
  format               = 60 lines per page
  tabulation size      = 8
  non printable format = caret (i.e., `^C', `M-^C' etc.)

Headers:
--------
  header       = %a
  left footer  = #?l!%E!#?v|%E|%s./%s#|!
  footer       = #?l|#!s-$f-, -||
  right footer = #?l!%s./%s#!#?v|%s./%s#|%E|!
  left title   = #?2||$e $T|
  center title = #?1|$t1|$n|
  right title  = #?2|$t2|$Q|
  under lay    = 

Input:
------
  truncate lines = no
  interpret      = yes
  end of line    = any type
  encoding       = ISO-8859-1
  document title = #10!f|$n|, |
  prologue       = bw
  print anyway   = no
  delegating     = yes

Pretty-printing:
----------------
  style sheet     = selected automatically
  highlight level = normal
  strip level     = 0

Output:
-------
  destination     = sent to the default printer
  version control = numbered backups of files already numbered,
                            and simple of others
  backup suffix   = ~

PostScript:
-----------
  magic number              = %!PS-Adobe-3.0
  Printer Description (PPD) = selected automatically
  default PPD               = level1
  page label format         = #{pl.short}
  number of copies          = 1
  sides per sheet           = Simplex
  page device definitions   = 
  statusdict definitions    = 
  page prefeed              = no

Internals:
----------
  verbosity level     = 2
  file command        = /usr/bin/file -L
  library path        = 
	/home/grk/.a2ps
	/usr/share/a2ps/sheets
	/usr/share/a2ps/ps
	/usr/share/a2ps/encoding
	/usr/share/a2ps/afm
	/usr/share/ogonkify/afm
	/usr/share/a2ps/ppd
	/usr/share/a2ps/fonts
	/usr/share/ogonkify/fonts
	/usr/share/a2ps

Any ideas?

---

