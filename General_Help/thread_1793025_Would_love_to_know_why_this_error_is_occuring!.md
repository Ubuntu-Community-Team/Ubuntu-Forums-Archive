---
title: "Would love to know why this error is occuring!"
date: 2011-06-28
forum: General Help
---

### Post by Antipacket on 2011-06-28
I removed _zlib 1:1.2.3.3.dfsg-15ubuntu1_ and installed _zlib 1.2.5_.

Now when I try to start gdm (and what appears to be anything that uses python), I get:

> /usr/bin/python: error while loading shared libraries: /lib/libz.so.1: file too short

Why is this occurring?

Is this occurring because Canonical modified Python in Ubuntu, and now Ubuntu Python expects to see Canonicals modified version of zlib (1:1.2.3.3.dfsg-15ubuntu1), and doesn't recognize the official version, which is why the error is occurring?

---

### Post by andrewthomas on 2011-06-28
Because python was built against zlib-1.2.3 not 1.2.5.

What did you expect?

You cannot just upgrade packages with no regard for the consequences.  

Are you planning on rebuilding everything on your system that depends on zlib?

Why, exactly, did you decide that you required zlib-1.2.5?

---

### Post by Antipacket on 2011-06-29
> **andrewthomas said:**
> 

Why, exactly, did you decide that you required zlib-1.2.5?


To compile Firefox 5.

---

### Post by andrewthomas on 2011-06-29
Why do you want to compile it from source?

---

### Post by Antipacket on 2011-06-29
I want to remove the modified version of Firefox in Ubuntu and install the official version.

---

### Post by dFlyer on 2011-06-29
Well you have two choices, recompile everything or revert back.

---

### Post by Antipacket on 2011-06-29
What do you mean recompile everything?... or revert back to what? Ubuntu Firefox?

---

### Post by Bachstelze on 2011-06-29
Why build it from source when you can download a compiled version from mozilla.com?

---

### Post by Antipacket on 2011-06-29
Fun.

---

### Post by Bachstelze on 2011-06-29
Then have fun recompiling everything that depends on zlib. :) You can't have your cake and eat it too.

---

### Post by Bachstelze on 2011-06-29
No, since you ate your cake, you'll have to compile a new one if you want to have one again. It is certainly possible, that's why I'm sure you will have a lot of fun doing it. :)

---

### Post by Antipacket on 2011-06-29
So, to get Zlib 'accepted' on my system, I will need to re-compile Python?... and chances are I will need to re-compile Python dependencies also, yeah?

---

### Post by Bachstelze on 2011-06-29
The Python package in Ubuntu was compiled against the zlib version that is in the Ubuntu zlib package.  Since you installed a new zlib, you will have to recompile Python against the new zlin.  Since Python is an interpreted languages, you may not have to recompile the Python dependencies (they may work just as well with the new Python).

By the way, you're going to mess up your system big time. :)   But that's fine, it's how you learn.

---

### Post by andrewthomas on 2011-06-30
> **bachstelze said:**
> 

by the way, you're going to mess up your system big time. :)   but that's fine, it's how you learn.
+1

---

