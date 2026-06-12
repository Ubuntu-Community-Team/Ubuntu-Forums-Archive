---
title: "Ubuntu and Finance"
date: 2006-01-20
forum: General Help
---

### Post by larry on 2006-01-20
Dear All,
I am starting to learn quantitative methods for finance. The industry requires strong C++ development skills and I am new to this language.
I am interested in using open-source libraries, in particular QuantLib ([http://quantlib.org/)](http://quantlib.org/)).
I would like any help/info/suggestions about IDEs for C++ and this specific library.
At the moment I am on Ubuntu and Anjuta, but some people told me that KDE is actually better suited for development.
I like Gnome, but it is not a religious thing for me, so I would switch to KDE if proper.
Just as a test, I created a Hello World C++ project and I included in the main code the line:

  #include <ql/quantlib.hpp>
which should have allowed me to use the library, but I rather got tons of errors.
Thanks for any suggestions.

Larry

---

### Post by hajk on 2006-01-21
I doubt very much that learning C++ will be worth the trouble when you're planning a career in quantitative finance. Learning Matlab, Python or even Fortran may be better bets.

Signed: finance prof...

---

### Post by adamonduty on 2006-01-21
Are you sure you have the library installed correctly? Does the /usr/include/qt/ dir exist? Are you able to compile a program just by compiling the source with gcc or g++ at the terminal?

---

### Post by larry on 2006-01-21
[QUOTE=hajk]I doubt very much that learning C++ will be worth the trouble when you're planning a career in quantitative finance. Learning Matlab, Python or even Fortran may be better bets.

Signed: finance prof...[/QUOTE]


Well, if you have a look at [www.efinancialcareers.co.uk](www.efinancialcareers.co.uk), you appreciate that for a real quantitative position you are asked to know C++.
I had the same experience in my country (Italy), though here the financial world is simply primitive compared to what you can find e.g. in London.
I already know Fortran and Matlab, but everybody wants C++ (they rather do not care about whether you have any idea of what Black and Scholes is as long as you can code in C++).
That is why I am surprised by your reply.
Cheers

Larry

---

### Post by larry on 2006-01-21
[QUOTE=adamonduty]Are you sure you have the library installed correctly? Does the /usr/include/qt/ dir exist? Are you able to compile a program just by compiling the source with gcc or g++ at the terminal?[/QUOTE]

Yes, I am able to use g++ both from the command line and inside Anjuta IDE.
Furthermore, I can see that a built-diagnostic which tests some QuantLib examples can be run (without showing the output) from the command line finally reporting that the examples had run correctly.

Cheers

Larry

---

### Post by adamonduty on 2006-01-21
Maybe you should post your exact source file....

---

### Post by Viro on 2006-01-21
[QUOTE=larry]
I had the same experience in my country (Italy), though here the financial world is simply primitive compared to what you can find e.g. in London.
[/QUOTE]

Agreed. In the financial sector in the UK, C++ seems to have a very strong foothold.

---

### Post by larry on 2006-01-21
[QUOTE=adamonduty]Maybe you should post your exact source file....[/QUOTE]

Right. This is the code I try to get working:

/* Created by Anjuta version 1.2.4 */
/*	This file will not be overwritten */

#include <iostream>
#include <ql/quantlib.hpp>
int main()
{
	std::cout << "Hello world" << std::endl;
	return 0;
}

the quantlib reference manual says to add the line 
#include <ql/quantlib.hpp>
to be able to use the quantlib library.

From the command line I can run a test suite by:

larry@mypc:~$ quantlib-test-suite
Running 199 test cases...

Tests completed in 6 m 55 s


*** No errors detected
larry@mypc:~$

So I think the problem is that Anjuta does not simply "see" the library.
Anyone comes forward with a suggestion?
Cheers

Larry

---

### Post by kanem on 2007-05-11
Hi Larry,

I hope you're still around. I'm having the same problem you were over a year ago. I guess from [this later thread](http://ubuntuforums.org/showthread.php?t=156993&highlight=quantlib) that you eventually got quantlib working. 

I tried compiling the source downloaded from their website, but after installing I got the same kinds of errors as with the Ubuntu packaged one. I'd really appreciate some insight into how you got this working.

Kanem

Edit: Could a mod please move this thread to the Programming Talk section?

---

### Post by gyroid on 2007-10-25
I've just had a similar problem and it turned out that I was missing a -lQuantLib.
i.e. to compile use
g++ my_code.cpp -lQuantLib

---

### Post by Nasky on 2007-12-22
Hey all,

 I can't get it work ! I get lots of errors using the compilation command : 
```
g++ -o testql testQL.cpp -lQuantLib
```
Usually, we should add something like : "-L/usr/lib" but there's nothing in this folder related to "QuantLib" or "QL" or anything else with "q" :mad:

How to fix that ? Anyone got a solution ?

[COLOR="Red"]EDIT : well, actually I managed it. I've added "-L/usr/lib". So the working command is : **g++ testQL.cpp -L/usr/lib -lQuantLib** [/COLOR]

Thanks

---

