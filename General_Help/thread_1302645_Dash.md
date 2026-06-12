---
title: "Dash"
date: 2009-10-27
forum: General Help
---

### Post by insia_linux on 2009-10-27
Hi,

I have just a little interrogation.

After read this : [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)
I have some question.

It's say : dash was selected for "The boot speed improvements" but today with our computer, bash is also very quick. So which optimisation dash do?
Ubuntu rewrite all it startup scrit with dash or they was add the ligne #! bin/bash on all script file?

Thanks you for your information

---

### Post by amingv on 2009-10-27
> **insia_linux said:**
> Ubuntu rewrite all it startup scrit with dash or they was add the ligne #! bin/bash on all script file?

From the article you linked to:
> Rather than change each of them individually to run explicitly under /bin/dash, a change which would require significant ongoing maintenance and which would be liable to regress if not paid close attention, the Ubuntu core development team felt that it was best simply to change the default shell.

/bin/sh is a link that points to the default shell, they just changed it to point to /bin/dash instead of /bin/bash.

I am not sure about the details regarding speed (never checked and didn't use Ubuntu when it still used bash), so I can't provide anything accurate about that. But I believe it has nothing to do with dash doing any optimization, it just runs (loads?) faster.

---

### Post by slakkie on 2009-10-27
[http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)

> 
Debian Almquist shell (dash) is a Unix shell, much smaller than bash but still aiming at POSIX-compliancy. It requires less disk space but is also less feature-rich.

Dash, like ash, executes shell scripts faster than bash and depends on fewer libraries. It is believed[1] to be more reliable in the case of upgrade problems or disk failures.


---

### Post by insia_linux on 2009-10-27
I agree about all is say about dash (much smaller than bash, less disk space ...) but the convention with all linux OS is default bourne shell. So ubuntu don't respect this rule.

And an exemple : if i want to make a script for all linux platform i will work fine with all except ubuntu (with dash shell at default of course).

---

### Post by amingv on 2009-10-27
I don't think there's such a convention, though I couldn't really say for sure.

In any case I've never experienced cross compatibility problems with scripts coming to and from Ubuntu.
If you wish to make a script, just set the shebang at the start of the script to indicate '#!/bin/bash' and it should work for most setups (you may use '#!/usr/bin/env bash' in some cases, too).

---

### Post by mcduck on 2009-10-27
> **insia_linux said:**
> I agree about all is say about dash (much smaller than bash, less disk space ...) but the convention with all linux OS is default bourne shell. So ubuntu don't respect this rule.

And an exemple : if i want to make a script for all linux platform i will work fine with all except ubuntu (with dash shell at default of course).

Bash is the convention for *user shells*, while POSIX standard actually says that system shells should be sh-compliant (so system shell scripts shouldn't contain any bashisms). If you want to make a script that runs on all Unix/Linux systems you definitely should not be using any bash-specific features on it.

Ubuntu *does* use Bash as default interactive shell for users.

edit: like amingv noted above, if you still want to use bash-specific features in your script then just use the correct shebang and the script will be executed with Bash. If you use "#!/bin/sh" your script definitely should be able to run with any sh-compliant shell instead of just Bash.

edit2: I almost forgot, the move to Dash indeed *did* result in easily noticeable decrease in boot time compared to previous Ubuntu versions.. :)

---

### Post by insia_linux on 2009-10-27
On Wikipedia Bash Reference Manual ([http://tiswww.case.edu/php/chet/bash/bashtop.html](http://tiswww.case.edu/php/chet/bash/bashtop.html)) it's write 
"Bash was created in 1987 by [Brian Fox]("http://en.wikipedia.org/wiki/Brian_Fox"). In 1990 [Chet Ramey]("http://en.wikipedia.org/wiki/Chet_Ramey") became the primary maintainer.[]("http://en.wikipedia.org/wiki/Bash#cite_note-Bourne_shell_grammar-3") Bash is the shell for the [GNU operating system]("http://en.wikipedia.org/wiki/GNU_operating_system") from the GNU Project. It can be run on most [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") operating systems. It is the default shell on most systems built on top of the [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") as well as on [Mac OS X]("http://en.wikipedia.org/wiki/Mac_OS_X") and [Darwin]("http://en.wikipedia.org/wiki/Darwin_%28operating_system%29")"

So bash need to stay the default shell since this time, is'n it?
Why don't suggest in ubuntu installation,  whitch shell must be select by default?

Sorry for the annoyance

---

### Post by mcduck on 2009-10-27
> **insia_linux said:**
> On Wikipedia Bash Reference Manual ([http://tiswww.case.edu/php/chet/bash/bashtop.html](http://tiswww.case.edu/php/chet/bash/bashtop.html)) it's write 
"Bash was created in 1987 by [Brian Fox]("http://en.wikipedia.org/wiki/Brian_Fox"). In 1990 [Chet Ramey]("http://en.wikipedia.org/wiki/Chet_Ramey") became the primary maintainer.[]("http://en.wikipedia.org/wiki/Bash#cite_note-Bourne_shell_grammar-3") Bash is the shell for the [GNU operating system]("http://en.wikipedia.org/wiki/GNU_operating_system") from the GNU Project. It can be run on most [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") operating systems. It is the default shell on most systems built on top of the [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") as well as on [Mac OS X]("http://en.wikipedia.org/wiki/Mac_OS_X") and [Darwin]("http://en.wikipedia.org/wiki/Darwin_%28operating_system%29")"

So bash need to stay the default shell since this time, is'n it?
Why don't suggest in ubuntu installation,  whitch shell must be select by default?

Sorry for the annoyance
No, it doesn't say anywhere there that bash should even exist on a Linux system.

The only rule is that the shell must be compatible with the original Sh shell. Using Bash is a common practice, but on the other hand avoiding any bash-specific stuff has always been recommended, so moving to any other Sh-compatible shell is not a problem at all.

Actually using bash-specific stuff in shell scripts is, and has always been, considered as bad practice. And any shell script that has no bash-specific code will run just as fine (actually better) with Dash than it would with Bash.

(And like I already said in my previous post, the *user shell* is still Bash.)

---

### Post by insia_linux on 2009-10-27
Thank you for all your explication !

---

