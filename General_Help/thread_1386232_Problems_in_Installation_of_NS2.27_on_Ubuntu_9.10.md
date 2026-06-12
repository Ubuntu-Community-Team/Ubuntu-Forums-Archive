---
title: "Problems in Installation of NS2.27 on Ubuntu 9.10"
date: 2010-01-20
forum: General Help
---

### Post by Scholar1987 on 2010-01-20
[SIZE=1][B]I have run through all the installation steps required for installation of NS2.27 onto my system. But I face following problems
[/B]
Nam has been installed successfully.
ln: creating symbolic link `ns': File exists
ln: creating symbolic link `nam': File exists
Please compile your xgraph separately.
Please compile your gt-itm & sgb2ns separately.
Ns-allinone package has been installed successfully.
Here are the installation places:
tcl8.4.5:    /home/sawyer/ns-allinone-2.27/{bin,include,lib}
tk8.4.5:        /home/sawyer/ns-allinone-2.27/{bin,include,lib}
otcl:        /home/sawyer/ns-allinone-2.27/otcl-1.8
tclcl:        /home/sawyer/ns-allinone-2.27/tclcl-1.15
ns:        /home/sawyer/ns-allinone-2.27/ns-2.27/ns
nam:            /home/sawyer/ns-allinone-2.27/nam-1.10/nam

**but when I give it returns the following  **

sawyer@sawyer:~$ nam
nam: 
[code omitted because of length]
: no event type or button # or keysym
    while executing
"bind Listbox <MouseWheel> {
%W yview scroll [expr {- (%D / 120) * 4}] units
}"

[B]
And when I click on to installation paths above tcl8.4.5,tk8.4.5,ns,nam does not open. [/B]

[B]What may be the problem !!! .

Next is when I go for validation that is after giving the command
[/B]

sawyer@sawyer:~/ns-allinone-2.27/ns-2.27$ ./validate

**I get this **

Test output agrees with reference output
All test output agrees with reference output.
*** ./test-all-rng
Tests: rngtest
Running test rngtest:
../../ns test-suite-rng.tcl rngtest QUIET
Test output agrees with reference output
All test output agrees with reference output.
These messages are NOT errors and can be ignored:
    warning: using backward compatibility mode
    This test is not implemented in backward compatibility mode


validate overall report: some tests failed:
     ./test-all-newreno ./test-all-red
to re-run a specific test, cd tcl/test; ./test-all-TEST-NAME
Notice that some tests in webcache will fail on freebsd when -O is turned on.
This is due to some event reordering, which will disappear when -g is turned on.


**Please let me know wat all are the extra packages to be installed. bcoz I am using old version of Ns2 on Ubuntu9.10**

[B]Thank you,
Sawyer[/B][/SIZE]

---

