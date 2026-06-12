---
title: "Cannot compile Firefox"
date: 2009-11-17
forum: General Help
---

### Post by waj1122 on 2009-11-17
I tried to compile Firefox from source to no avail. I used the same .mozconfig file on a wubi install on this same computer and everything worked. Now after taking the plunge and installing ubuntu to the hard drive and using the same technique I get "Segmentation fault" and Firefox will not load. I've searched the web and can't find any solution to this problem. Any help in this matter will be appreciated. I wasn't sure whether to post here or in a Firefox forum.

---

### Post by RedSingularity on 2009-11-18
Thats odd.  Have you tried to install it from the repositories.  That way everything is put where it needs to be.

---

### Post by waj1122 on 2009-11-18
That's NOT the problem. The repository version works, I just don't care for the time it takes to update itself and I like to build it the way I want for my processor. That way I'm as current as possible. Installing Firefox also works using Ubuntuzilla, that's just not what I wanted to do. My memory checks out ok. I would just like to be able to compile it from source (tried downloading and compiling 3 times with the exact results).

---

### Post by t0p on 2009-11-18
> **waj1122 said:**
> I tried to compile Firefox from source to no avail. I used the same .mozconfig file on a wubi install on this same computer and everything worked. Now after taking the plunge and installing ubuntu to the hard drive and using the same technique I get "Segmentation fault" and Firefox will not load. I've searched the web and can't find any solution to this problem. Any help in this matter will be appreciated. I wasn't sure whether to post here or in a Firefox forum.

I don't understand what is happening.  You say you can't compile Firefox, that you get a "segmentation fault" message.  When exactly is it that you get the "segmentation fault" error?  At what stage of compilation?

**EDIT:**  I just noticed, you said you're using the same .mozconfig file as you used on a wubi install.  Are you sure that's the right .mozconfig to use?  A wubi installation is not the same as installation of Ubuntu to the hard disk.  So maybe the .mozconfig file is the problem? (This is speculation as I've never used wubi and I've never compiled Firefox.)

Are you following the instructions from [here]("https://developer.mozilla.org/en/Build_Documentation")?  If not, maybe you should.  If you *are* following those instructions... I dunno...

---

### Post by waj1122 on 2009-11-18
After everything finishes and I try to run firefox is when the "segmentation fault" shows up. I've tried backing up my profile and deleting it and I get the same results.

Like I said earlier, it worked in a wubi install and yes I did follow all of the directions from [https://developer.mozilla.org/en/Build_Documentation](https://developer.mozilla.org/en/Build_Documentation)

---

### Post by ibuclaw on 2009-11-18
Could you post the output of the make command you use to build firefox?

It may give a clue as to where it goes wrong.

Regards
Iain

---

### Post by waj1122 on 2009-11-18
Here's my .mozconfig file:

    . $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"
ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-optimize 
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-mochitest
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls

And here's how I run the commands:

Code:

cd ~/mozilla-1.9.1
make -f client.mk build

Code:

cd ~/mozilla-1.9.1/obj-i686-pc-linux-gnu

Code:

make
sudo checkinstall

---

