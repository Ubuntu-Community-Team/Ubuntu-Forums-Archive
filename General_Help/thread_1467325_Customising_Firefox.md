---
title: "Customising Firefox"
date: 2010-04-30
forum: General Help
---

### Post by SpongeBob SquarePants on 2010-04-30
I'm not keen on the text size of my Bookmarks toolbar in Firefox 3.6. It's too big, and my bookmarks are too numerous to fit comfortably across the top (I have to click on that double arrow thingy to access the end ones).

I did a bit of research and found out that adding the following to userChrome.css would do the job....

> tree {
font-family: verdana !important;
font-size: 8pt !important;
}

There isn't a userChrome.css file as such in my .mozilla/firefox/user.default/chrome folder, so I had to add one. It now reads....

> /*
 * Edit this file and copy it as userChrome.css into your
 * profile-directory/chrome/
 */

/*
 * This file can be used to customize the look of Mozilla's user interface
 * You should consider using !important on rules which you want to
 * override default settings.
 */

/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes 20 pt:
 *
 * * {
 *   font-size: 20pt !important
 * }
 */
/*
 * Make menu items in particular 15 pt instead of the default size:
 *
 * menupopup > * {
 *   font-size: 15pt !important
 * }
 */
/*
 * Give the Location (URL) Bar a fixed-width font
 *
 * #urlbar {
 *    font-family: monospace !important;
 * }
 */

/*
 * For more examples see [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)
 */

tree {
font-family: verdana !important;
font-size: 8pt !important;
}

 
But for some reason, Firefox doesn't recognise it. I've changed the text size a few times and restarted FF, but it just comes up the same text size as before.

Any ideas?

---

### Post by lovinglinux on 2010-04-30
```

menu.bookmark-item {
font-family: verdana !important;
font-size: 8pt !important;
}

```

---

### Post by Ihaveaproblem on 2010-12-02
> **lovinglinux said:**
> ```

menu.bookmark-item {
font-family: verdana !important;
font-size: 8pt !important;
}

```

it doesn't work for me :(
any idea?

---

### Post by lovinglinux on 2010-12-02
> **Ihaveaproblem said:**
> it doesn't work for me :(
any idea?

Which version of Firefox?

---

### Post by Ihaveaproblem on 2010-12-02
> **lovinglinux said:**
> Which version of Firefox?

3.6.12
I found it. it's work for me: [http://ubuntuforums.org/showthread.php?p=5380788](http://ubuntuforums.org/showthread.php?p=5380788)

anyway thank you very much for your interest lovinglinux :)

---

