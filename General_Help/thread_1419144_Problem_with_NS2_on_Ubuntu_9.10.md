---
title: "Problem with NS2 on Ubuntu 9.10"
date: 2010-03-01
forum: General Help
---

### Post by DoSoo on 2010-03-01
Hi everybody, 
I'm trying to modify OWns Code in order to install in on ns2-34.
I thought I could do it but i can't get rid of this error
> ns-test$ ns /home/rihab/ns-allinone-2.34/ns-2.34/OWNS/demos/owns_demo.tcl
type random, seed 99
nodes 7, scale 7,  method pure-random
conn prob 0.4, beta  0.5, gamma 0.5
Creating WDMNodes...
Creating links 0...rihab@rihab-laptop:~/ns-test$ ns /home/rihab/ns-allinone-2.34/owns_demo.tcldemos/
type random, seed 99
nodes 7, scale 7,  method pure-random
conn prob 0.4, beta  0.5, gamma 0.5
Creating WDMNodes...
Creating links 0...
    (_o42 cmd line 1)
    invoked from within
"_o42 cmd attach-nam-traces _o14 _o38 file3"
    invoked from within
"catch "$self cmd $args" ret"
    invoked from within
"if [catch "$self cmd $args" ret] {
set cls [$self info class]
global errorInfo
set savedInfo $errorInfo
error "error when calling class $cls: $args" $..."
    (procedure "_o42" line 2)
    (SplitObject unknown line 2)
    invoked from within
"$queue attach-nam-traces $n1 $n2 $file"
    (procedure "_o4" line 10)
    (Simulator namtrace-queue line 10)
    invoked from within
"$self namtrace-queue $n1 $n2 $trace"
    (procedure "_o4" line 30)
    (Simulator simplex-FiberLink line 30)
    invoked from within
"_o4 simplex-FiberLink _o14 _o38 8Mb 70ms Null 8"
    ("eval" body line 1)
    invoked from within
"eval $self simplex-FiberLink $n1 $n2 $bw $delay $linktype $nlambda $args"
    (procedure "_o4" line 9)
    (Simulator duplex-FiberLink line 9)
    invoked from within
"$ns duplex-FiberLink $n([lindex $t 0]) $n([lindex $t 1]) $linkBW [lindex $t 2] Null $wvlens"
    (procedure "create-topology" line 46)
    invoked from within
"create-topology ns WDMNode SessionTrafficRcvr 8Mb 8 1 8 0.024 1 0.5 50"
    ("eval" body line 1)
    invoked from within
"eval create-topology ns WDMNode SessionTrafficRcvr $val(link_bw) $val(link_wvlen_num) \
        $val(wvlen_conv_factor) $val(wvlen_conv_dist) $val(wvl..."
    (file "/home/rihab/ns-allinone-2.34/ns-2.34/OWNS/demos/owns_demo.tcl" line 177)                      Can anyone tell me what's the matter with this code?
And what is the instruction
> [catch "$self cmd $args" ret                      supposed to do exactly?
Thanks

---

### Post by ahso186 on 2010-11-25
[SIZE=2]Hello&#65292;I am a collage students ,and recently I am doing the research of OWNS ,too. I have experienced the same problem, and I want to know whether you have solved it ? If you have done, I wish for your help.[/SIZE]
[SIZE=2]  I have tried many ways to solve it, for example,I made the two lines useless by using "#" in front of them:(in the "ns-lib.tcl" file,line 1495/1496)[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]# set queue [$link_([$n1 id]:[$n2 id]) queue][/SIZE]
[SIZE=2]# $queue attach-nam-tracs $n1 $n2 $file" [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]then I can pass this error, but a segment fault appeared, so I am not sure of this solutiong[/SIZE][SIZE=2]. So if you have solved this problem , can you show me how to get rid of this problem.

[/SIZE][SIZE=2]my Emil is : [/SIZE][EMAIL="ahso186@yahoo.com.cn"][SIZE=2]ahso186@yahoo.com.cn[/SIZE][/EMAIL] 
 
[SIZE=2][/SIZE] 
[SIZE=2]Thank you! waiting for your reply[/SIZE]
[SIZE=2]Roland [/SIZE]

---

### Post by alok.gundgurthi on 2010-12-04
I use ubuntu 10.04 LTS. i installed ns-allinone-2.34 in my system. during installation i did not get any kind of errors, but when i tried to run a simulation program i got following error...

alok@alok-laptop:~/Desktop/Simulation$ set ns
alok@alok-laptop:~/Desktop/Simulation$ ns cwsim.tcl -rlen 2
ns: 
[code omitted because of length]
: invalid command name "Node/DelayBox"
    while executing
"Node/DelayBox instproc init args {
eval $self next $args
$self instvar db_classifier_

set db_classifier_ [new Classifier/DelayBox]

$self insert-entr..."
    invoked from within
"if {[ns-hasSTL] == 1} {

Simulator instproc set-nix-routing { } {
Simulator set nix-routing 1
Node enable-module "Nix"
}

Simulator instproc get-link-..."

Please help me to resolve this issue...
Thank you.

---

