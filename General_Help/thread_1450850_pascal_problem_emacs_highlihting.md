---
title: "pascal problem emacs highlihting"
date: 2010-04-09
forum: General Help
---

### Post by baha'a on 2010-04-09
hi guys

I started using emacs for programming Pascal and the indentation is amaizing but the problem (so far) is that it doesn't recognize the two reserved words (function and procedure) so is there a more recent version of emacs that does or can I adjust the highlihting scheme or is there any thing else I can do?
thank you for any help.

---

### Post by tlroche on 2010-04-09
> **baha'a said:**
> I started using emacs for programming Pascal

Then you really should ask this question on an emacs list. This is complicated slightly by the existence of 2 main forks of emacs, GNU and XEmacs. I know little about the latter, but when I have a question about GNU emacs, I go to [the help-gnu-emacs list]("http://lists.gnu.org/mailman/listinfo/help-gnu-emacs").

> **baha'a said:**
> is there a more recent version of emacs

Not knowing which version of emacs you're running makes it hard to say. To discover your emacs version from within, do M-x emacs-version; from without, run `emacs --version`. Mine is "GNU Emacs 23.1.50.1", which I get with package=emacs-snapshot on karmic.

---

### Post by baha'a on 2010-04-09
thanks for replying it seems that the version I have isn't the latest:
```

bahaa@bahaa-laptop:~$ emacs --version
GNU Emacs 22.2.1 Copyright (C) 2008 Free Software Foundation, Inc. 

```
but how can I get the latest?

---

### Post by baha'a on 2010-04-09
I've just downloaded this one:
```

GNU Emacs 23.1.1
Copyright (C) 2009 Free Software Foundation, Inc.

```

I'll try my luck in the list but still please if any body can help it would be appreciated:)

---

### Post by diesch on 2010-04-09
Could you provide some short example source code?

---

### Post by baha'a on 2010-04-09
```

program challenge;
type
   flaging = 1..6;
   break   = record
        total,key : integer;
         end;      
   breaks  = record
        solution : point;
        next     : ^breaks;
         end;     
   point   = record
        grain      : char;
        num      : integer;
        next,prev : ^point;
         end;      
var
   beads.out     : text;
   beads.in     : text;
   Agrain     : char;
   solutionsList : ^breaks;
   LS,LE     : ^point;
   flag         : flaging;
function
ReadNeculas(var LS : ^point;var LE : ^point;beads.in:text):flaging
begin
   writeln('                     welcome to our program');
   assign(beads.in,'<path>/beads.in');
   assign(solutions,<path>/beads.out');
   ReadNeculas(LS,LE,beads.in,flag);
   solveNeculas(LS,LE,solutionsList);
   giveSolution(solutionsList,beads.out);
end.

```as you can see I'm still in the beginning of the program but I need to write it as functions and procedures and emacs doesn't recognize the reserved words (function and procedure) as I said so the problem isn't in the highlighting but in the indentation because I can't go on without the indentation.

---

### Post by diesch on 2010-04-09
I don't have an Ubuntu Emacs around, but with the current development version it works if you write 

```
function ReadNeculas(var LS : ^point;var LE : ^point;beads.in:text):flaging
``` (all in one line)

instead of

```
function
ReadNeculas(var LS : ^point;var LE : ^point;beads.in:text):flaging
``` (two lines)

Looks like a bug to me.

---

### Post by baha'a on 2010-04-09
> **diesch said:**
> I don't have an Ubuntu Emacs around, but with the current development version it works if you write 

```
function ReadNeculas(var LS : ^point;var LE : ^point;beads.in:text):flaging
``` (all in one line)

instead of

```
function


ReadNeculas(var LS : ^point;var LE : ^point;beads.in:text):flaging
``` (two lines)

Looks like a bug to me.
man thank you so much :D

it really worked I really appreciate it thank you sooo much
and thanks a lot to everybody who helped.

---

### Post by baha'a on 2010-04-09
EMACS is the best ;) :D

note: it seems it's just programmed this way

because after writing in one line worked I made the program name in a separate line and it didn't highlight neither the reserved word "program" nor it's name :).

---

