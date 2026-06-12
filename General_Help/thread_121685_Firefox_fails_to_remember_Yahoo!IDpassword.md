---
title: "Firefox fails to remember Yahoo!ID/password"
date: 2006-01-25
forum: General Help
---

### Post by Teddy-O on 2006-01-25
Using Firefox 1.5, when I check the "Remember my ID on this computer" box when signing on to Yahoo! Mail, it doesn't stick, even when I set my cookies, form fields, and password manager to their most permissive settings.

Is there a setting I'm missing that would prevent Firefox from remembering or prevent Yahoo! from setting a cookie?

Thanks.

--Teddy-O

---

### Post by nanotube on 2006-01-25
hey
are you sure you have not set firefox to delete all cookies on exit?

---

### Post by AmboyGuy on 2006-01-25
Yahoo Itself sends a code to prevent the password from working. There used to be an extension "remember password" you can try searching [http://www.extensionsmirror.nl/]("http://www.extensionsmirror.nl/") for it.

---

### Post by Teddy-O on 2006-01-26
nanotube--

I did set Firefox to accept all cookies and not delete on close, but it didn't help.

AmboyGuy--

I found the extension: Always Remember Password. Here's what the authors had to say about it:

"Some sites like Yahoo Mail, Hotmail, and banking sites instruct the browser to never allow your password manager to retain your information. If you use a shared workspace, then this is probably not desirable. If you are the sole user, then it's quite handy.

Note: Some forums sites that utilize a "quick reply" form may not work after this installation. You can safely uninstall it if you find you can't live without that feature. May break some heavy JS sites."

I might try it, but it sounds like it has a lot of side effects. I wonder if a GreaseMonkey script could more selectively deal with this problem.

Thanks for the help.

---

### Post by Teddy-O on 2006-01-26
I found this Greasemonkey script:

[http://blog.monstuff.com/archives/images/AllowPasswordRemembering.user.js](http://blog.monstuff.com/archives/images/AllowPasswordRemembering.user.js)

Here's what the author Julien Couvreur says about it:

"Sites can direct the browser not to save some password fields (for
increased security). They do it by tagging the password field with
autocomplete="off", in the HTML. "Allow Password Remembering" removes
these tags, so that the user can decide which password the browser 
should save."

No warnings about side effects, so we'll see...

---

### Post by AmboyGuy on 2006-01-26
Glad you found the info. I just looked up this extension I used sucessfully ( way back when ) [http://www.extensionsmirror.nl/index.php?showtopic=962]("http://www.extensionsmirror.nl/index.php?showtopic=962")
It doesn't have the side effects noted above. One problem, it only goes up to Firefox version 1.0. You can use MR Tech's Local Install ( an extension that everyone should have ) to ignore/bypass the extension max version checking. [http://www.mrtech.com/extensions/local_install/]("http://www.mrtech.com/extensions/local_install/")
I download all my extensions & themes to local directories on my hard disk and use Local Install to load them into Firefox. I also set the 'archive extensions' option in Local Install so when I use the extension managers 'find updates' any new versions are saved to my local directories.

---

### Post by Teddy-O on 2006-01-26
The Greasemonkey script is working okay, so I'll stay with that for now, but I installed Local Install and will explore its features. Thanks.

---

