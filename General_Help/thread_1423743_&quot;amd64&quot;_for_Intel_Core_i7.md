---
title: "&quot;amd64&quot; for Intel Core i7?"
date: 2010-03-07
forum: General Help
---

### Post by GhodMode on 2010-03-07
I'm buying a new computer which has an Intel Core i7 processor.  It's an Alienware M15x.  This is the first 64-bit capable computer I've owned and I was planning to load a 64-bit version of Ubuntu 9.10 (Karmic Koala).

When I used [Ubuntu's download page]("http://www.ubuntu.com/getubuntu/download") to download the 64-bit version, I ended up with "ubuntu-9.10-desktop-amd64.iso" even though there isn't a place to select the processor family.

Since I'm using an Intel processor, I don't think that the "amd64" version is right, but I can't find anything like an "i686" or "x86-64" version anywhere that I've looked.

Is there a 64-bit version of Ubuntu available for Intel processors?

If not, can someone suggest a good 64-bit distro for Intel-based processors?

Thank you.

--
Ghodmode
[www.ghodmode.com]("http://www.ghodmode.com")

---

### Post by karthick ayyapillai on 2010-03-07
> **GhodMode said:**
> I'm buying a new computer which has an Intel Core i7 processor.  It's an Alienware M15x.  This is the first 64-bit capable computer I've owned and I was planning to load a 64-bit version of Ubuntu 9.10 (Karmic Koala).

When I used [Ubuntu's download page]("http://www.ubuntu.com/getubuntu/download") to download the 64-bit version, I ended up with "ubuntu-9.10-desktop-amd64.iso" even though there isn't a place to select the processor family.

Since I'm using an Intel processor, I don't think that the "amd64" version is right, but I can't find anything like an "i686" or "x86-64" version anywhere that I've looked.

Is there a 64-bit version of Ubuntu available for Intel processors?

If not, can someone suggest a good 64-bit distro for Intel-based processors?

Thank you.

--
Ghodmode
[www.ghodmode.com]("http://www.ghodmode.com")


Hi
I think they havent released a version for intel 64 bit am not sure but you can find ubuntu 9.04 for intel 64 bit in the following link
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
try this
NOTE : there are some wireless issues with 9.1 version .

---

### Post by mockingbird on 2010-03-07
Short answer is - yes.  AMD64 is the one you want.

64 bit code was supposedly released by AMD (Though I think it's just for show) so just like Intel got to brand their CISC instruction set "x86", AMD was allowed to call the new 64-bit instructions AMD64 though I believe it is all for show.

The place where you will set your processor family is when you recompile your kernel.

---

### Post by GhodMode on 2010-03-07
Ok, so I've been doing a little more research and I may have answered my own question.

It's a bit over my head, but it seems like what Intel currently calls "[Intel® 64]("http://www.intel.com/technology/intel64/")" is actually the same as what Ubuntu's "amd64" version calls "EM64T".

ref: [http://en.wikipedia.org/wiki/X86-64#Intel_64_Implementations](http://en.wikipedia.org/wiki/X86-64#Intel_64_Implementations)

So, I should be able to just install the "amd64" version.  Can someone confirm this?

I guess I've been caught in the crossfire between Intel and AMD.

-- Ghodmode

---

### Post by Bachstelze on 2010-03-07
> **GhodMode said:**
> 
So, I should be able to just install the "amd64" version.  Can someone confirm this?


Yes, "amd64" is what you want.

---

