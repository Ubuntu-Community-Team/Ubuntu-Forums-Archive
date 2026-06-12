---
title: "x-terminal-emulator broken with 2.6.11 custom kernel"
date: 2005-03-10
forum: General Help
---

### Post by amp_man on 2005-03-10
well, first off, here's the scoop: I need a custom kernel =>2.6.10 to even have a shot at getting my the amr winmodem in my laptop (thinkpad i1300) to work, not to mention that slimming down the kernel has gotten it booting quite a bit faster on the pitiful little 500MHz celeron. So, after messing around a bit and after many hours of compiling figuring out that IDE support can't be compiled as a module (remember this newbies), I have *finally* gotten it to boot and run. but now every time I try to load the terminal emulator under gnome, I get the error "There was an error creating the child process for this terminal." Every other program (except ones that run under the terminal, such as scripts files) runs perfectly, but without the terminal, I'm lost (it used to be that the terminal was what got me lost  :shock: ), and the terminal emulator works perfectly under the stock 2.6.8-5-i686 kernel, so I think this is probably my doing within the configuration (all my packages were up to date as of the friday before last, according to synaptic, so I don't think this is the issue). I can't currently upload my .config file (nowhere to upload it to), but if anyone knows what might have loaded wrong, please lend a hand to a guy still working his way out of the n00b stage.

---

