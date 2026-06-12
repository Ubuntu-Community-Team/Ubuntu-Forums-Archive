---
title: "Problem With Enter Key and HTML"
date: 2010-08-06
forum: General Help
---

### Post by Antarctica on 2010-08-06
It's been a while since I last played around with HTML editing.  I made a practice webpage, and noticed when I do, for example...

[HTML]
<body>
This is some sample text.
This is some sample text.
</body>
[/HTML]

the text shows up as (in both Google Chrome and Firefox)...

> This is some sample text. This is some sample text.

instead of...

> 
This is some sample text.
This is some sample text.


The only workaround would be to put <br /> tags everywhere I want a carriage return or to press Enter.  I've only played around with HTML in Windows, so I'm wondering if this problem is a Linux thing.  I've tried both gedit and nano as my HTML editors and both display the same problem.  So what's up?  Is the Enter key in Linux registered as a space instead of a carriage return in HTML?

---

### Post by anglican on 2010-08-06
> **Antarctica said:**
> It's been a while since I last played around with HTML editing.  I made a practice webpage, and noticed when I do, for example...

[HTML]
<body>
This is some sample text.
This is some sample text.
</body>
[/HTML]the text shows up as (in both Google Chrome and Firefox)...

This is some sample text. This is some sample text.                      

instead of...

This is some sample text. 
This is some sample text.                      

The only workaround would be to put <br /> tags everywhere I want a carriage return or to press Enter.  I've only played around with HTML in Windows, so I'm wondering if this problem is a Linux thing.  I've tried both gedit and nano as my HTML editors and both display the same problem.  So what's up?  Is the Enter key in Linux registered as a space instead of a carriage return in HTML?
Nothing to do with the editor, that's html, you could put in as many line-braks as you like it would still show the same in the browser. A couple of other options are:
[HTML]
<body>
<p>This is some sample text.</p>
This is some sample text.
</body>
[/HTML]or
[HTML]
<body>
<pre>This is some sample text.
This is some sample text.</pre>
</body>
[/HTML]<p></p> defines a paragraph and <pre></pre> define pre-formatted text i.e. it preserves both spaces and line breaks.

H

---

### Post by Antarctica on 2010-08-06
Well I feel retarded.  I didn't know I was that rusty with HTML!  Thanks a lot!

---

