---
title: "problem in installing ns2 in ubuntu 9.04"
date: 2010-01-06
forum: General Help
---

### Post by hisunnyvashistha on 2010-01-06
Hi 
I have a problem in installing NS. i would grateful if you could help me. 
after the command "~/.bashrc" , I got error: "bash: :/usr/X11R6/lib:/usr/local/lib: No such file or directory" 
and in the .bashrc file i have   X11_LIB=/usr/X11R6/lib but in the path /usr/X11R6 ther is not lib folder! 


AND When i tried to run the ns batch i get the error 

    (_o5 cmd line 1) 
    invoked from within 
"_o5 cmd at 1 “puts “Hello World!””" 
    invoked from within 
"catch "$self cmd $args" ret" 
    invoked from within 
"if [catch "$self cmd $args" ret] { 
set cls [$self info class] 
global errorInfo 
set savedInfo $errorInfo 
error "error when calling class $cls: $args" $..." 
    (procedure "_o5" line 2) 
    (SplitObject unknown line 2) 
    invoked from within 
"_o5 at 1 “puts “Hello World!””" 
    ("eval" body line 1) 
    invoked from within 
"eval $scheduler_ at $args" 
    (procedure "_o3" line 3) 
    (Simulator at line 3) 
    invoked from within 
"$ns at 1 “puts \“Hello World!\””" 
    (file "sample.tcl" line 2)

---

