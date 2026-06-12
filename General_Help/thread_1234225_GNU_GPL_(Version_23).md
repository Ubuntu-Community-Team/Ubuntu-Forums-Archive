---
title: "GNU GPL (Version 2/3)"
date: 2009-08-07
forum: General Help
---

### Post by Happyisgood on 2009-08-07
I was reading through the terms of the GPL, which is a daunting task at best, and was running into an issue.

GCC is licensed under GPL, does that mean that the source of any program I compile with GCC would have to be made available to the public?  I ask this, because I assume that the header files are part of GCC and are covered under the license, and, because the headers are included (in binary format) in my program, I am technically using part of GCC and redistributing it as my own.

My question is simple (I don't really mind the answer either way.)  If I decide to distribute any programs I write and compile using gcc, do I have to license it under GPL and allow users to read the source code upon request?

---

### Post by yeeeev on 2009-08-07
No.
If you incorporate GCC's code into your app, and compile your app with that code (probably using GCC to do it :P), then you would have to distribute your app's code.
Using a GPL software does not mean that all the work you did with it is now GPLed as well. Only software derived from GPL software is.

---

### Post by Happyisgood on 2009-08-07
But if I recall correctly, GCC compiles itself (what came first, the compiler or the source code? (Sorry my personal attack at philosophy.))  So technically the header files are part of the code of GCC.  Is this kind of an exception, like are the headers free to distribute as long as I dont steal blocks of the actuall compiler?

---

### Post by yeeeev on 2009-08-07
OK, Now I get your philosophical question:)
The headers are not part of the GCC.
They are located (at least most of them) in the /usr/include directory and from a brief look, it seems that most are release under either BSD or LGPL license, both of which a not copy-left, which means no need for code distribution of derived work.

---

### Post by Happyisgood on 2009-08-07
Thank you so much.  I haven't distributed things, nor do I plan to in the near future (I'm not that good yet.) But I'm trying to get an idea of this whole open-source thing.  I'm REALLY loving it!  Anyway, anything I code will probably be open source anyway, I support free sharing of knowledge.

---

### Post by asmoore82 on 2009-08-08
> **Happyisgood said:**
> GCC is licensed under GPL, does that mean that the source of any program I compile with GCC would have to be made available to the public?

Another good point of interest here is that if you don't distribute any binaries,
you don't have to release any sources. You can do absolutely anything for "in-house" use.

---

### Post by CatKiller on 2009-08-08
> **Happyisgood said:**
>  So technically the header files are part of the code of GCC.

Technically they aren't. As has already been pointed out, those header files came from elsewhere anyway, but even if they hadn't and they'd been written specifically along with gcc, specific magic numbers to make something work cannot be copyrighted. No copyright, no need for a license. See, for example, the SCO vs the World coverage on Groklaw.

---

