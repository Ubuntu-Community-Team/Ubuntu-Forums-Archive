---
title: "error when running wireless1  and 2 in Marc Greis tutorial"
date: 2010-10-22
forum: General Help
---

### Post by alinnic1 on 2010-10-22
Hello all !
I am using ns2-34allinone on Ubuntu 10.04.
I installed/validated it succesfully ,but I get the following error
when doing Marc Greis's tutorial,wireless1 and wireless2.
All scripts until this one worked .

 num_nodes is set 3
warning: Please use -channel as shown in tcl/ex/wireless-mitf.tcl
INITIALIZE THE LIST xListHead
Loading connection pattern...
couldn't read file "../../tcl/mobility/scene/cbr-3-test": no such file or directory
    while executing
"source.orig ../../tcl/mobility/scene/cbr-3-test"
    ("uplevel" body line 1)
    invoked from within
"uplevel source.orig 
[list $fileName]"
    invoked from within
"if [$instance_ is_http_url $fileName] {
set buffer [$instance_ read_url $fileName]
uplevel eval $buffer
} else {
uplevel source.orig 
[list $fileName]
..."
    (procedure "source" line 8)
    invoked from within
"source $val(cp)"
    (file "wireless1.tcl" line 121)


Can anyone please help me ?The solutions I found google-ing didn't work .

Thanks in advance.

---

