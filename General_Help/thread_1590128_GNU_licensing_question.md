---
title: "GNU licensing question"
date: 2010-10-07
forum: General Help
---

### Post by COMTIBoy on 2010-10-07
Hi ,

I'm relatively new to Linux and had a question regarding the GCC compiler.

I realize that I can write an application and compile it using the GCC complier.  I can even sell it (or not) .  My question is do I have to make my source code public available also ?

---

### Post by Simian Man on 2010-10-07
> **COMTIBoy said:**
> Hi ,

I'm relatively new to Linux and had a question regarding the GCC compiler.

I realize that I can write an application and compile it using the GCC complier.  I can even sell it (or not) .  My question is do I have to make my source code public available also ?

No, you don't have to release your source code.  If GCC required that, it would not be nearly so popular.

The only caveat is that libc is licensed under the LGPL, so if you statically link to it, you have to provide source or object files so users can relink to a new version.  However the default is dynamic linking, so you probably don't have to worry about that.

---

### Post by COMTIBoy on 2010-10-07
Thanks!

---

### Post by gmargo on 2010-10-07
> **Simian Man said:**
> The only caveat is that libc is licensed under the LGPL, so if you statically link to it, you have to provide source or object files so users can relink to a new version.  However the default is dynamic linking, so you probably don't have to worry about that.

I am not a lawyer, so this is not legal advice.  This is my understanding:

The method of linking (static vs dynamic) is irrelevant.  You can use LGPL libraries (such as glibc) without causing your program to be GPLed.  If you use GPL libraries (such as readline), then your program is GPLed, and you must make source code available if you distribute the program.

To answer your original question: the compiler GCC is GPL, but the object code it generates is free of any inherited license.

See a lawyer for legal advice.  Read the licenses yourself here: [http://www.gnu.org/licenses/licenses.html](http://www.gnu.org/licenses/licenses.html)

---

### Post by Simian Man on 2010-10-07
> **gmargo said:**
> The method of linking (static vs dynamic) is irrelevant.  You can use LGPL libraries (such as glibc) without causing your program to be GPLed.

Nope, if you statically link to LGPL libraries, then you must provide the source or object code to your program so that the user can relink to newer versions of that library.  If you dynamically link, then it's not a problem since you can easily replace the library in question.

But that's kind of tangential to the OP's question since GCC doesn't put restrictions on the code it produces and he will likely dynamically link to libc anyway.

---

### Post by gmargo on 2010-10-08
> **Simian Man said:**
> if you statically link to LGPL libraries, then you must provide the source or object code to your program so that the user can relink to newer versions of that library. 

I stand corrected.  Thank you.

---

