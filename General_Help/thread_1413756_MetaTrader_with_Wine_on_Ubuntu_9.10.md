---
title: "MetaTrader with Wine on Ubuntu 9.10"
date: 2010-02-22
forum: General Help
---

### Post by heylookitsmewow on 2010-02-22
In early 2009 I was running MetaTrader on Kubuntu 8.04. It installed and ran perfectly. I never paid attention to which version of Wine it was using. It was whatever was in the repositories.

A while back I did a clean install of Kubuntu 9.10 and never could get MetaTrader to work. It would appear to install fine but when I try to start it I get the dancing cursor for a few seconds but the program never opens. I tried several versions of Wine with no change.

I went back to Kubuntu 8.04 with a clean install and tried several versions of Wine and it did the same thing.

Now I just did a clean install of Ubuntu 9.10. According to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2893](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2893) MetaTrader works with Wine 1.1.28. It also refers to a site with installation instructions but they are from 2007 so maybe out of date.

Before I give this a try on this install I want to know now is how can I get MetaTrader to work today with Ubuntu 9.10.

Which version of Wine will work?

Where can I get that version of Wine and what is the best way to install it?

---

### Post by BrianElliott0218 on 2010-02-28
Hello!
I have been working to help Linux users get the MT4 platform running as well.  I found what could very well be the best answer to the issue on this site:  [http://articles.mql4.com/416]("http://articles.mql4.com/416")

Follow the instructions given there, and report your results.  I will do the same.
:P

My main tester is using Ubuntu 9.10 and has had the MT4 system running, but with some issues.  I will report on progress for those issues after he re-installs the Wine, and MT4 platform using the install instructions from the link above.

Some of the issues we have run into thus far:
*  The "Expert Advisors" button at the top is grayed out.
*  EA properties cannot be changed in either StratTester, or in trading.
*  The Date and Visual Mode selection buttons cannot be checked.

That's all we have issue with for now.  After install with the new instructions, I'll post again.:popcorn:

---

### Post by heylookitsmewow on 2010-03-02
Thanks for the reply. Back when I was using MT before with Hardy I do remember some problems with something being grayed out with the expert advisor settings. I found out how to fix that before and it worked fine so if I can get it running hopefully I can remember how I did that.

The article you posted says to use wine-0. 9.21. I went to the source they linked to to downloaded it but I am not sure what to do with the tarballs they have. So I fond [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) through wineHQ but they don't have that version for 9.10.

I found these instructions on this forum

> bunzip2 [the filename]
tar -xvf [the unzipped tarball]
cd [the new wine directory]
./configure
make
sudo make install

When I got to the > ./configure command I got the following with the error at the end

> me@acer:~/wine-0.9.21$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for cpp... cpp
checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for :... no
checking for flex... no
checking for lex... no
configure: error: no suitable lex found. Please install the 'flex' package.


Any idea what that means? Or is there an easier way to install the right version of wine?

---

### Post by bluntknife on 2010-05-26
I was going to start mucking about getting MetaTrader 4 working under wine in Ubuntu 10.04 but thought hang on, I have a windows XP license, just install Oracle (SUN) Virtualbox, create a new XP virtual machine, install MT4 in there and run the XP VM in Seamless mode. Hey presto you can now set your monitors up however you need them without trying to fudge MT4 on Ubuntu...

---

### Post by tersogar on 2010-08-03
The attachments included work for me on Ubuntu 9.10 and 10.04 with metatrader 4. Hope this help.:popcorn:

---

### Post by soyatti on 2010-10-14
thanks tersogar,

"Metatrader 4 Instalation.pdf" worked for me on Ubuntu 10.10, wine-1.2.1.

---

### Post by kidcoder on 2011-01-01
Thanks tersogar, very useful document. :D

---

