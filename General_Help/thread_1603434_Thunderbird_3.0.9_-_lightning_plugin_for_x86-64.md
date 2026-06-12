---
title: "Thunderbird 3.0.9 - lightning plugin for x86-64"
date: 2010-10-22
forum: General Help
---

### Post by zenon222 on 2010-10-22
With the most recent upgrade of Thunderbird to 3.0.9 I was unable to find a 64-bit version of the lightning calendar plug-in.

I tried compiling my own copy of thunderbird v3 from source (3.0.10pre) and it loaded into 3.0.9 perfectly!

Rename the attached files to drop the last ".bz2" (files should end in ".00" and ".01") then combine both files with the command ```
cat lightning.tar.bz2.* >lightning.tar.bz2
```If you want to try compiling your own copy instead, just read the websites quoted in the header to ensure you have all dependencies then simply run this batch file
```
#/bin/sh
#Compile Thunderbird c/w lightning
#script compiled from: https://developer.mozilla.org/index.php?title=en/Simple_Thunderbird_build&action=print
#source from: https://developer.mozilla.org/en/Comm-central_source_code_%28Mercurial%29
#  http://www.mozilla.org/projects/calendar/releases/

# Get the source
nice hg clone http://hg.mozilla.org/releases/comm-1.9.1/
cd comm-1.9.1
nice python client.py checkout

# Setup a basic .mozconfig file
echo 'ac_add_options --enable-application=mail' > .mozconfig                   # let's build Thunderbird...
echo 'mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/objdir-tb-release' >> .mozconfig   # ...in this directory...

# USE THIS ONLY IF NOT ON WINDOWS!  Parallel compilation on Windows is
# unreliable now due to bug 524149.
echo 'mk_add_options MOZ_MAKE_FLAGS="-j4"' >> .mozconfig                       # ...quickly.

# Compile lightning support
echo 'ac_add_options --enable-calendar' >> .mozconfig                          # BUT! don't forget lightning.

# Build
nice -n18 make -f client.mk
```Enjoy!

---

### Post by jdevora on 2010-10-27
I installed perfectly,

But I was looking to integrate it with Google Calendar y the google-data-provider  isn't available either.

Did you compile it as well by  any chance?

Cheers
 JD

---

### Post by matzenit on 2010-10-28
Worked perfectly. Thank you!

---

### Post by zenon222 on 2010-11-02
I use the zindus software to sync my google contacts.
The whole system works perfectly too, everything is in sync from my ipod touch to thunderbird.
I can't recall how I setup the google calendar, search the web and you'll find a few sites describing the process.  What worked for me was:```
https://www.google.com/calendar/dav/[xxxxxxxxx]@gmail.com/events
```With the new 3.0.10 you have to recompile with the above code (don't change anything), I'll post the new version later since people are finding it useful.

Compiling the whole piece of software really is a breeze, but the complete directory will balloon to 2GB after it's finished, and after all that you only care about a single 1MB file.  Boo to the Mozilla team for neglecting the 64-bit community!

---

### Post by zenon222 on 2010-11-04
64-bit Lighting plugin for thunderbird 3.0.10

---

### Post by jeffmoore87 on 2010-11-08
The above worked for 3.0.10. Thank you for posting it.

---

### Post by mtg on 2010-11-09
> **zenon222 said:**
> 64-bit Lighting plugin for thunderbird 3.0.10

Thank you very much. It works great.

---

### Post by spambin on 2010-11-14
Thanks for the plugin. Like jdevora I'm also looking for the Google Calendar plugin for TB 3.0.10 x86-64.  You don't happen to have this around?

Edit: Using the most recent version (0.7.1) from the official addons page modified as mentioned [in this article]("http://ubuntuforums.org/showpost.php?p=10038156&postcount=108") works like a charm.

---

### Post by zenon222 on 2010-11-18
I didn't use any plugins, just add a "on the network calendar" use the https format I posted above and select calDAV.

calDAV is the same data format my iPod touch uses, the whole setup works perfectly, reminders beeping and everything.

---

### Post by zenon222 on 2010-12-12
Here are the files to use with Thunderbird 3.1.7.

---

### Post by jro on 2010-12-21
Thanks zenon, works great on 10.10. I appreciate your work to get these files out for everyone.

---

