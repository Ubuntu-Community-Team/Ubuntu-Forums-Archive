---
title: "uninstall Firefox build"
date: 2010-07-23
forum: General Help
---

### Post by evolmachine on 2010-07-23
I tried building Firefox for S&Gs following these instructions

[https://developer.mozilla.org/En/Simple_Firefox_build]("https://developer.mozilla.org/En/Simple_Firefox_build")

Now I have multiple versions of Firefox all over my system. I just want to revert to the 3.6.6 in the Repositories, but whenever I try to launch "Firefox" from a terminal, I get one of my build versions instead.

I've tried completely uninstalling and reinstalling Firefox, and Synaptic says I have the right version installed, but I can't launch that version.  Instead I get a build version. 

How can I remove all these builds and just start over?

---

### Post by lovinglinux on 2010-07-24
See the last item on [my tutorial](http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html). Next time use **checkinstall** instead of **make install**, so you can easily remove it from Synaptic.

---

### Post by evolmachine on 2010-07-24
Hey right on thanks! That got rid of 3.7a5pre

Can I just also "sudo rm -fr ~/mozilla-central" to get rid of 4.0b2pre?  How do I check if there are other instances of firefox anywhere else?

Thanks for the tip on checkinstall too, much easier.

---

### Post by lovinglinux on 2010-07-24
> **evolmachine said:**
> Can I just also "sudo rm -fr ~/mozilla-central" to get rid of 4.0b2pre?

If you havn't compiled ot yet, then yes. Removing the source folder will not remove the installed packages tho.

> **evolmachine said:**
> How do I check if there are other instances of firefox anywhere else?

```
locate firefox.sh
```

> **evolmachine said:**
> Thanks for the tip on checkinstall too, much easier.

You are welcome. You might also like my extension [FoxTester](http://foxtester-extension.blogspot.com). Is not for compiling source code, but for testing various versions of Firefox without disrupting your default installation and user profile.

---

### Post by evolmachine on 2010-07-24
I ran make -f client.mk from the mozilla-central folder when I did the 4.0b2pre build, so nothing really got installed right? I ended up just creating a shortcut to the firefox executable found in objdir-ff-release/dist/bin/ and using that.  So deleting the mozilla-central folder would remove that build of Firefox, no?

locate firefox.sh came back with nothing... which is weird I think since it should find and display Firefox 3.6.7 (what I'm using right now), yes?

I believe I'll just be using Foxtester from now on to check out the new stuff... I got in over my head :)

---

### Post by lovinglinux on 2010-07-24
> **evolmachine said:**
> I ran make -f client.mk from the mozilla-central folder when I did the 4.0b2pre build, so nothing really got installed right? I ended up just creating a shortcut to the firefox executable found in objdir-ff-release/dist/bin/ and using that.  So deleting the mozilla-central folder would remove that build of Firefox, no?

In this case, yes.

> **evolmachine said:**
> locate firefox.sh came back with nothing... which is weird I think since it should find and display Firefox 3.6.7 (what I'm using right now), yes?

Try:
```
locate firefox
```

This will give lots of results, including your profile folder, but what you want will probably on under /usr/lib/firefox-3* or /opt/firefox

> **evolmachine said:**
> I believe I'll just be using Foxtester from now on to check out the new stuff... I got in over my head :)

Yeah, compiling is overkill unless you need specifically to optimize it with especial compilation flags. FoxTester makes a lot easier if you want to test different versions.

---

