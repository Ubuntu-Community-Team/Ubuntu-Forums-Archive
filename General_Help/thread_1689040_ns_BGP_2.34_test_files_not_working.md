---
title: "ns BGP 2.34 test files not working"
date: 2011-02-16
forum: General Help
---

### Post by municeg on 2011-02-16
karthick@ubuntu:~/Desktop/ns-allinone-2.34/ns-2.34/tcl/bgp/test$ ns drop-peer2.tcl
DROP-PEER2 Validation Test:
  Three ASes connected in a line, each with one router.
   AS 1       AS 0       AS 2
   n1 }——{ n0 }——{ n2
     (_o10 cmd line 1)
    invoked from within
“_o10 cmd get-bgp-agent”
    invoked from within
“catch “$self cmd $args” ret”
    invoked from within
“if [catch "$self cmd $args" ret] {
set cls [$self info class]
global errorInfo
set savedInfo $errorInfo
error “error when calling class $cls: $args” $…”
    (procedure “_o10&#8243; line 2)
    (SplitObject unknown line 2)
    invoked from within
“$n0 get-bgp-agent”
    invoked from within
“set bgp_agent0 [$n0 get-bgp-agent]”
    (file “drop-peer2.tcl” line 27)
karthick@ubuntu:~/Desktop/ns-allinone-2.34/ns-2.34/tcl/bgp/test$
This error comes when executing test scripts in the  ns-allinone-2.34/ns-2.34/tcl/bgp/test$ Directory… Please help me to  clear out this error…
                                                                            Regards,
                                                                          S.Muniyappan

---

### Post by yashwanthmaddur58 on 2013-02-20
Hi have you got the output for above script..i too working on it..if you know please tell me..:p

---

### Post by oldos2er on 2013-02-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

