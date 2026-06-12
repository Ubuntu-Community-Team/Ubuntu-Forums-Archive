---
title: "Console calculator?"
date: 2006-03-18
forum: General Help
---

### Post by skorange on 2006-03-18
Hi are there any standard console calculators included with ubuntu?  Specifically, I'm looking for something to do quick (simple) math calculations as well as base conversions (hex to binary to decimal, that sort of thing).

Any suggestions?

---

### Post by aysiu on 2006-03-18
orpie? > RPN calculator for the terminal
Orpie is a fullscreen RPN calculator for the console. Its operation is
similar to that of modern HP calculators, but data entry has been optimized
for efficiency on a PC keyboard. Features include:

  * real and complex numbers and matrices
  * extensive function library
  * command completion of function names
  * base conversions
  * units and conversion factor handling
  * exact integer arithmetic, with unlimited integer size
  * visible stack, with browsing/modification capability
  * user-defined variables
  * user-configurable keybindings, via a Mutt-like rcfile
  * context-sensitive help I don't *recommend* it, having never used it myself, but it's one of the only console-based calculators I could find through a Synaptic Package Manager search.

---

### Post by 5-HT on 2006-03-19
bc !

bc is a great console-based arbitrary precision calculator language that should already be installed by default.

Just enter 'bc' to start interactively.
Enter 'man bc' to read the manual.

Some quick tips on variables that you may find useful:

i) scale=x (for 'x' # of digits after the decimal point to use in some operations)

 The default is 0...so I always put something like 'scale=10' in.

ii) For base conversion

ibase=x (for input in base 'x')
obase=x (for output in base 'x')

Default is base 10 (kinda goes without mention).

HTH

---

### Post by skorange on 2006-03-19
thanks guys!

bc is great, definitely useful to know how to use for the future when I might find myself on someone elses terminal needing to do a quick calculation..

orpie sounds intriguing though.  messing around with bc made me realize i'd really like to be able to conver 2's compliment binary negative numbers to decimal as well?  i  wonder if orpie can handle this?

---

