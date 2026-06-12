---
title: "Need good English dictionary"
date: 2009-11-13
forum: General Help
---

### Post by shenchen8571 on 2009-11-13
Is there anyone know that a good English dictionary can be use on Ubuntu?

---

### Post by arnab_das on 2009-11-13
the default one's pretty nifty. at least works for me.

accessories>office>dictionary

---

### Post by audiomick on 2009-11-13
Mine has already got one installed.
It is part of the Gnome desktop utilities package.
It can be started from the applications menu under "office"
The only catch is, it looks up the words in the internet

---

### Post by doas777 on 2009-11-13
teh inTarweb si teh roxzors 4 lookin up stuffz. u cans b 1337 lik mii

---

### Post by audiomick on 2009-11-13
> **doas777 said:**
> teh inTarweb si teh roxzors 4 lookin up stuffz. u cans b 1337 lik mii
not actually funny mate.
Schenchen is obviously living in a country whose language is not his mother tongue. That is not all that easy. I know. I've been doing it for 14 years too.

---

### Post by shenchen8571 on 2009-11-13
> **audiomick said:**
> not actually funny mate.
Schenchen is obviously living in a country whose language is not his mother tongue. That is not all that easy. I know. I've been doing it for 14 years too.

Thank you.
;)

---

### Post by shenchen8571 on 2009-11-13
> teh inTarweb si teh roxzors 4 lookin up stuffz. u cans b 1337 lik miiActually, I do NOT really understand that what does he mean.

---

### Post by audiomick on 2009-11-13
Don't worry mate, neither did I. Something smart about looking things up in the web. Have you found the dictionary that should already be there?

---

### Post by Kdar on 2009-11-13
Fanasticdic is another application for linux.

Also there are all those Firefox add-ons that you can use.
[https://addons.mozilla.org/en-US/firefox/search?q=dictionary&cat=all&advancedsearch=1&as=1&appid=1&lver=3.5&atype=0&pp=20&pid=2&sort=&lup=](https://addons.mozilla.org/en-US/firefox/search?q=dictionary&cat=all&advancedsearch=1&as=1&appid=1&lver=3.5&atype=0&pp=20&pid=2&sort=&lup=)

I also often use sites like [http://dictionary.reference.com/](http://dictionary.reference.com/) or [http://www.thefreedictionary.com/](http://www.thefreedictionary.com/) if I need to look up some word.

---

### Post by doas777 on 2009-11-13
sorry, sorry. things are usually funnier in my head,,,

---

### Post by tubunu on 2009-11-13
Add Longman English Dictionary to your Firefox search engines.

---

### Post by shenchen8571 on 2009-11-13
> **audiomick said:**
> Don't worry mate, neither did I. Something smart about looking things up in the web. Have you found the dictionary that should already be there?

I use Collins dictionary on Windows, but in ubuntu, I try to use Dictionary.com.
In Collins, explanations of each word are listed by this dictionary and the software also gives more details for the word that I am looking up to help me to use words in a correct way.

---

### Post by audiomick on 2009-11-13
I've added the longman one to Firefox, and it looks ok, and the one the comes with Ubuntu seems pretty ok too. As I already wrote, you can find it in your applications under office.

I've just had a quick look at collins on the web. My Collins English - German is fantastic ( old fashioned one with paper inside... ), and I can imagine that their Software ones are great too. I doubt if you will get one for free that is that good.

You could try installing your collins one on the Ubuntu machine using wine. It might work. Wine seems to be able to get heaps of stuff running these days. You'll have look up wine though, I can't help you there. I have got around to trying it yet.

Oh, and don't forget Wikipedia....

---

### Post by ubuntu27 on 2009-11-13
Here is a solution to all of you.

Use **[Artha]("http://artha.sourceforge.net")** ~ The Open Thesaurus: There is a deb file for Ubuntu in their homepage.

[http://artha.sourceforge.net/wiki/index.php/Home](http://artha.sourceforge.net/wiki/index.php/Home)

---

### Post by audiomick on 2009-11-13
> **ubuntu27 said:**
> Here is a solution to all of you.

Use **[Artha]("http://artha.sourceforge.net")** ~ The Open Thesaurus: There is a deb file for Ubuntu in their homepage.

[http://artha.sourceforge.net/wiki/index.php/Home](http://artha.sourceforge.net/wiki/index.php/Home)

Great. I'll take two!!;)

Thanks for the tip

Edit: got it installed. took about 2 minutes. It's a cool thing, particularly the function of highlighting a word from a text passage on the screen, and calling up Artha with a hotkey combination.

---

### Post by shenchen8571 on 2009-11-13
> **audiomick said:**
> I've added the longman one to Firefox, and it looks ok, and the one the comes with Ubuntu seems pretty ok too. As I already wrote, you can find it in your applications under office.

I've just had a quick look at collins on the web. My Collins English - German is fantastic ( old fashioned one with paper inside... ), and I can imagine that their Software ones are great too. I doubt if you will get one for free that is that good.

You could try installing your collins one on the Ubuntu machine using wine. It might work. Wine seems to be able to get heaps of stuff running these days. You'll have look up wine though, I can't help you there. I have got around to trying it yet.

Oh, and don't forget Wikipedia....

I buy a hard-copy of Collins dictionary and the disk is free to attach with the book.

---

### Post by shenchen8571 on 2009-11-13
> **audiomick said:**
> Great. I'll take two!!;)

Thanks for the tip

Edit: got it installed. took about 2 minutes. It's a cool thing, particularly the function of highlighting a word from a text passage on the screen, and calling up Artha with a hotkey combination.

After using "./configure", a problem happens below:

chen@chen-ubuntu:~/Desktop/artha-0.9.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking wn.h usability... no
checking wn.h presence... no
checking for wn.h... no
[COLOR=Red]configure: error: You must have wordnet development headers (wordnet-dev) to build. ([http://wordnet.princeton.edu/obtain](http://wordnet.princeton.edu/obtain)). Refer INSTALL file for further details.[/COLOR]

[COLOR=Black]Do you know how to solve it (The red words).[/COLOR]

---

### Post by audiomick on 2009-11-14
Looks like you tried to do it the hard way. 
What the message means is that a tool is missing that the computer would need to do what you asked it to. Don't worry about it.

You are using Ubuntu, which is based on Debian. This means you can use .deb packages, and should where possible to stop your system's package management getting confused.

Go back to the Artha site, and go to the download link.

Get the appropriate .deb download from the bottom half of the page under where it says "Binaries"
either the i386 one for a 32 bit Ubuntu, or the AMD64 one for a 64 bit.

Once it is on the computer, you should just have to click on it. A thing called gdebi should start and want to install it for you.

That is how it worked for me.
Good Luck. I probably wont be back here for a few days :-)

PS. with the 32 or 64 bit thing: I you are unsure and don't know how to find out which one you have, don't panic. I am pretty sure gdebi will not allow you to install the wrong one.

---

### Post by shenchen8571 on 2009-11-14
> **audiomick said:**
> Looks like you tried to do it the hard way. 
What the message means is that a tool is missing that the computer would need to do what you asked it to. Don't worry about it.

You are using Ubuntu, which is based on Debian. This means you can use .deb packages, and should where possible to stop your system's package management getting confused.

Go back to the Artha site, and go to the download link.

Get the appropriate .deb download from the bottom half of the page under where it says "Binaries"
either the i386 one for a 32 bit Ubuntu, or the AMD64 one for a 64 bit.

Once it is on the computer, you should just have to click on it. A thing called gdebi should start and want to install it for you.

That is how it worked for me.
Good Luck. I probably wont be back here for a few days :-)

PS. with the 32 or 64 bit thing: I you are unsure and don't know how to find out which one you have, don't panic. I am pretty sure gdebi will not allow you to install the wrong one.

Thank you very much audiomick. It is my honour that I can recognize you here and happy to see you later.
;)

---

