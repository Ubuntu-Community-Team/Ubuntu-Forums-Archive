---
title: "Restricted extras?"
date: 2012-05-05
forum: General Help
---

### Post by azangru on 2012-05-05
Sorry for a silly question. I've just clean-installed Precise after about two years of not installing Ubuntu, so I've forgotten the procedure (or rather the post-procedure) pretty much :-)

I remember, there used to be a code to download and install all the codecs, Microsoft fonts, unrar, ffmpeg, and whatnot. I believe, it was somehow related to installing the "restricted extras". I've googled for it and found the code line:

```
sudo apt-get install ubuntu-restricted-extras
```

However, if I enter it in the terminal, the output says that it will require:
> Need to get 6,909 kB of archives.
After this operation, 2,809 kB of additional disk space will be used.

So, the installed packeges will take less than 10 MB of space, right? But I distinctly remember that installing the restricted extras used to take like 200 megabytes of space. Am I doing something wrong? Do I need to look for some other packages?

What commands do *you* use to make Ubuntu get all the codecs, microsoft fonts, unrar and such?

---

### Post by Revolutionary101 on 2012-05-05
No, that is the right command that you have. I don't know why it has changed but it could be because less things are included with the ubuntu-restricted-extras and are now included with Ubuntu by default (or some other odd reason). No need for for any worry.

You should only worry if you install that and what you intended to have work, ends up not working.

---

### Post by sisco311 on 2012-05-05
Check out:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and
[http://psychocats.net/ubuntu/nonfree](http://psychocats.net/ubuntu/nonfree)

For legal reasons, Adobe's Flash plug-in and the Microsoft Fonts aren't stored in the Ubuntu repositories. The packages only contain some small scripts which will download the files from Adobe's and Microsoft's website. That's why the size of the packages installed by ubuntu-restricted-extras is less than the actual disk space used by the codecs, fonts, etc.

---

### Post by azangru on 2012-05-05
> **sisco311 said:**
> Check out:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and
[http://psychocats.net/ubuntu/nonfree](http://psychocats.net/ubuntu/nonfree)

Thank you!

For a moment there, after having run the code (I have not seen your message till then), I worried that I have not specifically enabled the multiverse repository. But apparently it wasn't necessary.

> **Revolutionary101 said:**
> You should only worry if you install that and what you intended to have work, ends up not working.

Everything seems to work so far :)

---

### Post by sisco311 on 2012-05-05
You're welcome!

---

