---
title: "Need help finding a driver and C Compiler"
date: 2010-03-23
forum: General Help
---

### Post by GhostToast on 2010-03-23
Hi all,

I've got two questions.  My first one is does anybody know of a driver for my old Linksys LNE100TX-G1 ethernet card?  I've searched Google and can't find one.  Second, does anybody know of a good C Compiler that can compile C code and run it?

Thanks a lot,

-GhostToast

---

### Post by l.billon on 2010-03-23
Hi!
GCC is the main C compiler in Linux, it is used by many IDEs.

---

### Post by GhostToast on 2010-03-23
> **l.billon said:**
> Hi!
GCC is the main C compiler in Linux, it is used by many IDEs.

Hi 1.billion!

Thanks for the reply.  Can you tell me how to use GCC to create, compile, and run C code?  And do you know of any drivers for my Linksys LNE100TX-G1 ethernet card?

Thanks,

-GhostToast

---

### Post by Iowan on 2010-03-23
There are a couple of threads around ([here]("http://ubuntuforums.org/showthread.php?t=6762") is one, [this]("http://ubuntuforums.org/showthread.php?t=1420979") is another) discussing various IDEs. Unless I'm (once again) mistaken, GCC is a compiler - it will *only* compile. Creating (text editor) and running are outside it's realm.

---

### Post by srs5694 on 2010-03-23
> **GhostToast said:**
> I've got two questions.  My first one is does anybody know of a driver for my old Linksys LNE100TX-G1 ethernet card?  I've searched Google and can't find one.  Second, does anybody know of a good C Compiler that can compile C code and run it?

Linux drivers are almost always written for *chipsets,* not specific consumer devices. The distinction is this: Manufacturers of boards, like Linksys, buy chips or sets of chips ("chipsets") from manufacturers of chipsets, like Intel or VIA. These manufacturers in turn sell their chips to many manufacturers, so you might find the same chipsets on boards from Linksys, D-Link, ASUS, and many others. Drivers almost invariably work with the chips on the boards, so Linux chipset drivers may work with anywhere from one to hundreds of different boards. Board manufacturers sometimes tweak their Windows drivers so that they only work with their own products, but such shenanigans are rare in the Linux world.

If memory (and a quick Google search) serve, the Linksys LNE100TX series used a clone of the "Tulip" Ethernet chipset. This was very common a decade or so ago, and Linux has excellent standard support for it, so you shouldn't need to find a separate driver. If your board isn't working, though, it could be that your "G1" revision used something else, or perhaps you need to jump through some unusual extra hoops to get it working. You might try posting the output of the "lspci" command on your computer; that might provide some extra clues about your board.

---

### Post by GhostToast on 2010-03-24
Hi all,

Thank you for all of your replies.  So basically what you're saying is Ubuntu has GCC compiler which can compile C but can't run it.  And for drivers you're saying I shouldn't need an extra driver but it's possible I might since I have the "G1" model?  Let me know if I missed anything.

Thanks, I really appreciate this,

-GhostToast

---

### Post by srs5694 on 2010-03-24
GCC compiles software, the ln linker links compiled software into an executable, and the kernel runs it. So GCC doesn't need to run the programs it compiles.

---

### Post by GhostToast on 2010-03-24
Hi all,

I have successfully installed Ubuntu 9.10 on my old brick and am using it now with a working internet connection.  Now all I need help with is GCC and I'll be all set.  Can anybody give me a tutorial on how to compile with GCC?

Thanks!

-GhostToast

---

### Post by kesken88 on 2010-03-24
howdy,

this is particular point i just started exploring myself.  
```

gcc -o outputfilename inputfile.h inputfile.c anotherinput.c  

```

works for simple programs.  GTK programs require a few more flags.

Good luck

---

### Post by Iowan on 2010-03-24
[Here]("http://linuxhelp.blogspot.com/2006/04/steps-to-compile-c-c-programs-using.html") is one article I found about compiling C programs (using gnu compiler).

---

### Post by egalvan on 2010-03-24
Compilers are for compiling.
Editors are for editing.
This is the *nix way of doing things.
One program, doing one thing, and doing it well.
There *are* integrated environments (IDE) in *nix,
but I have no experience or knowledge of these.
Others will have to chime in.

Your library should have some books/manuals on editing and compiling C code, look in the Unix section.


Use a good code-friendly text editor, such as vim, to create the code.

Then use a good compiler, such as gcc, to compile the code.

Executing the code is dependent on how it's supposed to run.

A search for *compiling C programs using gnu compiler* in Google turned up the following...

[http://www.wikihow.com/Compile-a-C-Program-Using-the-GNU-Compiler-(GCC](http://www.wikihow.com/Compile-a-C-Program-Using-the-GNU-Compiler-(GCC))


Another note....

Linux Is Not Windows

Microsoft has a different outlook on the computing world than the *nix community.

here is a good article on this...

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by GhostToast on 2010-03-25
Hi all,

Thank you for all of your helpful replies.  I have figured out everything I need to and really appreciate your help.  

Thanks!

-GhostToast

---

