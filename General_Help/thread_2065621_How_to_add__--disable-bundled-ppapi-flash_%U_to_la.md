---
title: "How to add  --disable-bundled-ppapi-flash %U to launch script?"
date: 2012-10-02
forum: General Help
---

### Post by Ace..... on 2012-10-02
I recently had a problem with google-chrome - a problem that appears to be solved by launching chrome from terminal using the command below:

google-chrome --disable-bundled-ppapi-flash %U

The post I had read suggested that this should be added to the chrome command line.
Something like this:

/opt/google/chrome/google-chrome --disable-bundled-ppapi-flash %U

However, I don't know how to do this.
I had a look in /opt/google/chrome/
and saw the google-chrome shell script, but it wasn't apparent what the next step was.

Perhaps someone might help. :smile:

---

### Post by Ace..... on 2012-10-03
Okay.... I have found a way.
Whether this is how we are meant to do it I don't know, but it seems to work just fine.

Open Dash and Min size the window by hitting square.

type google in search, and drag the icon to the desktop.

Rclick on it, and choose properties.

Check out the command line google-chrome %U

Paste this line over it:

google-chrome --disable-bundled-ppapi-flash %U

close properties.

Unlock the chrome icon from the launch bar (if you have it locked there).

Now drag your new desktop icon to the launch bar and re-lock it.

You now have a faster more responsive chrome, without the display errors caused by ppapi  - pepper flash

This presumes that you have installed adobe flash from software centre.

Nice!

:P

---

