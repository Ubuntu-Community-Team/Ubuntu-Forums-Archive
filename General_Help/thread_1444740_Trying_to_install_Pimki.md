---
title: "Trying to install Pimki"
date: 2010-04-01
forum: General Help
---

### Post by StolenPie on 2010-04-01
I have been trying to install a wonderful bit of PIM software called pimki, and it is one of the most frustrating things I have ever done :/
After a few hours of work I managed to fulfill steps 1-3 of the installation instructions here [http://pimki.rubyforge.org/INSTALL]("http://pimki.rubyforge.org/INSTALL")

However, the final step doesn't seem to work.

When I run the file pimki.rb in Ruby (thru terminal), I get this output:

```
/home/mydirectory/pimki-2.0/pimki.rb:3:in `load': /home/mydirectory/pimki-2.0/script/server:20: formal argument cannot be a constant (SyntaxError)
          'Default: 2500') { |OPTIONS[:port]| }
                                     ^
/home/mydirectory/pimki-2.0/script/server:20: syntax error, unexpected '[', expecting '|'
          'Default: 2500') { |OPTIONS[:port]| }
                                      ^
/home/mydirectory/pimki-2.0/script/server:23: formal argument cannot be a constant
          'Default: 0.0.0.0') { |OPTIONS[:ip]| }
                                        ^
/home/mydirectory/pimki-2.0/script/server:23: syntax error, unexpected '[', expecting '|'
          'Default: 0.0.0.0') { |OPTIONS[:ip]| }
                                         ^
/home/mydirectory/pimki-2.0/script/server:26: formal argument cannot be a constant
          'Default: production') { |OPTIONS[:environment]| }
                                           ^
/home/mydirectory/pimki-2.0/script/server:26: syntax error, unexpected '[', expecting '|'
          'Default: production') { |OPTIONS[:environment]| }
                                            ^
/home/mydirectory/pimki-2.0/script/server:36: formal argument cannot be a constant
          'Default: ./storage/[port]') { |OPTIONS[:storage]| }
                                                 ^
/home/mydirectory/pimki-2.0/script/server:36: syntax error, unexpected '[', expecting '|'
          'Default: ./storage/[port]') { |OPTIONS[:storage]| }
                                                  ^
/home/mydirectory/pimki-2.0/script/server:40: formal argument cannot be a constant
          "Default: 3.0.3\n") { |OPTIONS[:redcloth]| }
                                        ^
/home/mydirectory/pimki-2.0/script/server:40: syntax error, unexpected '[', expecting '|'
          "Default: 3.0.3\n") { |OPTIONS[:redcloth]| }
                                         ^
/home/mydirectory/pimki-2.0/script/server:48: formal argument cannot be a constant
          ) { |OPTIONS[:notex]| }
                      ^
/home/mydirectory/pimki-2.0/script/server:48: syntax error, unexpected '[', expecting '|'
          ) { |OPTIONS[:notex]| }
                       ^
	from /home/mydirectory/pimki-2.0/pimki.rb:3:in `<main>'

```

I am wondering if the dependencies are installed properly, because when I ran gem install rails --version 1.0.1 (for example), I got this message:

```
WARNING:  Installing to ~/.gem since /var/lib/gems/1.9.1 and
	  /var/lib/gems/1.9.1/bin aren't both writable.
WARNING:  You don't have /home/mydirectory/.gem/ruby/1.9.1/bin in your PATH,
	  gem executables will not run.
```

Followed by a series of installation messages.

How can I fix this? I really want this software, lol.

---

### Post by km0r3 on 2010-04-01
> IMPORTANT NOTES
===============

[snip]

*** Email me (direct or on the pimki-users mailing list) for more help.**Actually using the mailing list would have been a better place to ask this.
> 
WARNING:  You don't have /home/mydirectory/.gem/ruby/1.9.1/bin in your PATH,
      gem executables will not run.
I highly suspect you haven't read this... Quick fix:

Add this directory to your $PATH like that:

[LIST=1]
[*]Open your *~/.bashrc* for editing.
[*]Add this line:
```
PATH=$PATH:~/.gem/ruby/1.9.1/bin
export PATH
```
[*]Save file.
[*]Restart your shell.
[/LIST]
**Still showing up with errors?** Ask.

---

### Post by StolenPie on 2010-04-02
That seems to have cleared up the first WARNING message, but the second warning message still comes up when I try to install the dependencies, and I get the same error message on trying to run pimki.rb

Thanks for the help and attention though :)

---

### Post by km0r3 on 2010-04-02
> **StolenPie said:**
> That seems to have cleared up the first WARNING message, but the second warning message still comes up when I try to install the dependencies, and I get the same error message on trying to run pimki.rb

Thanks for the help and attention though :)
If you have really done like I said, then at least those warning messages should have disappeared...
I warmly remind you again to use the mailing-list. :)

Have you tried installing it with *gem*, too?

```
gem install --include-dependencies pimki
```

[FONT=Verdana]**Tried this here and it just works fine.!**[/FONT]

---

### Post by StolenPie on 2010-04-02
I tried the gem install and it still didn't work (it told me that it "could not find gem pimki locally or in a repository").

Anyway, I will go to the mailing list and try there. (btw I misunderstood your "Still showing up with errors? Ask." as an invitation to ask you, rather than the mailing list. Lol.)

Thanks for your help once again.

---

### Post by km0r3 on 2010-04-02
Strange. I some time ago had similar error messages, but that was solved when I added the mentioned directory to the $PATH.

> **StolenPie said:**
> 
Anyway, I will go to the mailing list and try there. (btw I misunderstood your "Still showing up with errors? Ask." as an invitation to ask you, rather than the mailing list. Lol.)

No! *Now* you misunderstood me. That was both an invitation to ask here *and *query the mailing-list! This was not meant as rejection; I'm glad to help, like most of us here, but I'm at the end with my Latin. Now we understand us :) . I apologize for the confusion.

Nonetheless others may be able to help you.

If you get the solution, please be so kind and post it here.

---

