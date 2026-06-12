---
title: "I can get Java working in Firefox 3.5 but NOT 3.6"
date: 2009-08-18
forum: General Help
---

### Post by Kraust on 2009-08-18
Java applets work fine in Firefox 3.5, and they also worked fine in 3.0. My problem is with 3.6, I have it installed alongside 3.5 (because 3.5 can't be upgraded into 3.6 to my knowledge. If it can tell me how!) so I can prove that Java can be running in one but not the other. To my knowledge 3.5 and 3.6 both share the same plugins directory but even so I have libjavaplugin_oji.so symbolically linked in numerous moz / firefox plugin folders. I'm using Sun Java 6 on a 32 bit OS. I do have some Open JDK installed but that's for javac when doing something in another program.

Can anyone help?

EDIT: For future readers, I'm on 3.7 now, and the download is from Mozilla's Repositories on Synaptic. I'm going to bed shortly.

---

### Post by starcraft.man on 2009-08-18
I can tell you for certain Java works in Namaroka (i.e. 3,6). I just downloaded and extracted it to my desktop, then *suffered* through playing two crappy java apps. I didn't do anything fancy like symlinking plugins, just ran it from the desktop. A few of my older extensions broke,  but not java.

You want to ensure the package **sun-java6-plugin** is installed? Only thing I can think of. Not a big java user tbh.

---

### Post by Kraust on 2009-08-18
Yes, sun-java6-plugin is already installed. And I installed Namoroka when it was still Minefield via Mozilla's Nightly Repositories in Synaptic (which I had to add myself). I don't think that's the problem though.

So if you can get it to work, I don't see why I can't.

---

### Post by starcraft.man on 2009-08-18
Humour me as a test. Download the [alpha1]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/3.6a1-candidates/build1/linux-i686/en-US/namoroka-3.6a1.tar.bz2") here, then extract to desktop. Simply run it by launching the firefox bin inside the firefox folder extracted. i.e. in terminal type:

```
~/Desktop/firefox/firefox
```

Ignore the compatibility check and continue, then test java/look at about:plugins.

If it does work, something you've done with symlinks must be messing up your install of 3.6.

Also, just a note, but the nightlies are now 3.7 eh?

---

### Post by Kraust on 2009-08-18
The about:plugins on both the 3.6s are the same exact thing except the one that you told me to download had a nullplugin, but that once again wasn't anything special.

I downloaded 3.7 to see if that would help at all but it doesn't.

I really think that if I'm able to update to 3.6 / 3.7 from 3.5 that I could solve this problem but I don't know if that's possible.

---

