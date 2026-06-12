---
title: "Firefox greys out when uploading?"
date: 2009-07-01
forum: General Help
---

### Post by GreenMeanie on 2009-07-01
Why does Firefox and Epiphany GREY out when uploading to Mediafire and the other upload websites making the Browser useless while waiting for it to finish uploading?

---

### Post by colau on 2009-07-01
> **GreenMeanie said:**
> Why does Firefox and Epiphany GREY out when uploading to Mediafire and the other upload websites making the Browser useless will waiting for it to finish uploading?
```

firefox --version

```

---

### Post by oldsoundguy on 2009-07-01
Could also be a slow internet connection (do not believe what they advertise .. check it yourself at any number of speed check sites.)

And you don't have to use terminal to find out your version of either browser .. just go to help> about.

---

### Post by GreenMeanie on 2009-07-01
Mozilla Firefox 3.0.11

But like I said Epiphany does it too.
I think it is Flash related not sure thou.


> **colau said:**
> ```

firefox --version

```

---

### Post by colau on 2009-07-01
> **GreenMeanie said:**
> Mozilla Firefox 3.0.11

But like I said Epiphany does it too.
I think it is Flash related not sure thou.
```

sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree

```

---

### Post by CatKiller on 2009-07-01
> **GreenMeanie said:**
> Why does Firefox and Epiphany GREY out when uploading to Mediafire and the other upload websites making the Browser useless while waiting for it to finish uploading?

You have it backwards. It's not useless because it's grey, it's grey because it's useless. It's a Compiz feature so that you can easily see which windows are not currently responding to input.

If you don't like it, turn it off:

System -> Preferences -> CompizConfig Settings Manager -> Fade Windows -> Dim Unresponsive Windows.

It won't make your browser any more responsive while it's waiting for the upload to finish though.

---

### Post by GreenMeanie on 2009-07-01
The compiz suggestion stops the greying but didn't help with the upload freezing firefox.
I also tried the flash-nonfree didn't help either.
I usually use the adobe flash plugin from their website.

---

