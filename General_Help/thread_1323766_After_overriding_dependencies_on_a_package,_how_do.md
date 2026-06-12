---
title: "After overriding dependencies on a package, how do you keep it?"
date: 2009-11-12
forum: General Help
---

### Post by skullmunky on 2009-11-12
I'm trying to build something from source that relies on the ffmpeg dev packages (libavcodec-dev, etc).  

Since I use Kdenlive and other video apps, I have the "unstripped" versions of these libs installed (libavcodec-unstripped, etc. because they contain extra codecs).  

Unfortunately libavcodec-dev requires libavcodec, and the dependency is not satisfied by libavodec-unstripped.  I think this is now fixed in 9.10 but I'm still using 9.04 for the moment.  I installed libavcodec-dev using dpkg to override the unresolved dependency and everything works fine - BUT, now whenever I try to install anything else, it says that I have broken packages and insists on removing them as part of any other install or update action.  

Is there a way to hold packages even if the system thinks they're broken?

---

### Post by slakkie on 2009-11-12
You could try pinning packages.

man apt_preferences


or set it via 

echo "package-name hold" | sudo dpkg --set-selections

---

### Post by jocko on 2009-11-12
> **skullmunky said:**
> I'm trying to build something from source that relies on the ffmpeg dev packages (libavcodec-dev, etc).  

Since I use Kdenlive and other video apps, I have the "unstripped" versions of these libs installed (libavcodec-unstripped, etc. because they contain extra codecs).  

Unfortunately libavcodec-dev requires libavcodec, and the dependency is not satisfied by libavodec-unstripped.  I think this is now fixed in 9.10 but I'm still using 9.04 for the moment.  I installed libavcodec-dev using dpkg to override the unresolved dependency and everything works fine - BUT, now whenever I try to install anything else, it says that I have broken packages and insists on removing them as part of any other install or update action.  

Is there a way to hold packages even if the system thinks they're broken?
That's weird.
I can install libavcodec-dev and the unstripped packages without problem (in karmic).
The dependencies for the libavcodec-dev package says "libavcodec52 | libavcodec-extra-52" (in this case the "|" means "or"), and the "-unstripped" package is just a meta package that installs the "-extra-52" package.
Maybe you are using an older ubuntu version? In that case you should really file a bug report on the libavcodec-dev package and hope that they fix the dependencies to include the "-unstripped" package as an alternative.

---

### Post by Techsnap on 2009-11-12
I discussed this issue in my videos, it's an apt thing and you can fix it by editing the following file:

/var/lib/dpkg/status

Look for the package, go to the depends line and take out everything apart from the name of the package you're trying to get the system to keep. For example lets use your **libavcodec52** package.

You'd open the above file in nano, gedit, kate or whatever you're comfortable using and then you'd search for the package named libavcodec52. Then you go down to the depends line and remove everything in their place put libavcodec52. apt will be satisfied with this because it would think that libavcodec52 depends on it's self and of course it's installed.

---

### Post by skullmunky on 2009-11-12
Great, thanks!  that should fix it.  

@jocko: that's correct, I'm using Jaunty.  There is a bug report and it is fixed in Karmic, I just need a temporary fix 'til I can upgrade.

---

### Post by skullmunky on 2009-11-18
One other question about hacking /var/lib/pkg/status .. I want to make sure I'm doing this right.

I have libavcodec-unstripped-52 installed.

I want to install libavcodec-dev, which depends on libavcodec52 but is not satisfied by libavcodec-unstripped-52.  

Can I edit the description for libavcodec-unstripped-52 so that it provides libavcodec52?  

like instead of this:
```

Replaces: libavcodec52
Depends: libavutil-unstripped-49 (>= 3:0.svn20090303), libavutil-unstripped-49 (<< 3:0.svn20090303-99), libc6 (>= 2$
Conflicts: libavcodec52

```

do this:
```

Provides: libavcodec52
Depends: libavutil-unstripped-49 (>= 3:0.svn20090303), libavutil-unstripped-49 (<< 3:0.svn20090303-99), libc6 (>= 2$

```

(sorry about the truncation, that's from pico)

Or should I uninstall it, then install libavcodec52 and libavcodec-dev, then remove the dependencies for libavcodec-dev and replace libavcodec52 with -unstripped?

(ugh!)

---

### Post by jocko on 2009-11-20
> **skullmunky said:**
> One other question about hacking /var/lib/pkg/status .. I want to make sure I'm doing this right.

I have libavcodec-unstripped-52 installed.

I want to install libavcodec-dev, which depends on libavcodec52 but is not satisfied by libavcodec-unstripped-52.  

Can I edit the description for libavcodec-unstripped-52 so that it provides libavcodec52?  

like instead of this:
```

Replaces: libavcodec52
Depends: libavutil-unstripped-49 (>= 3:0.svn20090303), libavutil-unstripped-49 (<< 3:0.svn20090303-99), libc6 (>= 2$
Conflicts: libavcodec52

```do this:
```

Provides: libavcodec52
Depends: libavutil-unstripped-49 (>= 3:0.svn20090303), libavutil-unstripped-49 (<< 3:0.svn20090303-99), libc6 (>= 2$

```(sorry about the truncation, that's from pico)

Or should I uninstall it, then install libavcodec52 and libavcodec-dev, then remove the dependencies for libavcodec-dev and replace libavcodec52 with -unstripped?

(ugh!)
The only safe way I can see would be to change the dependencies for the -dev package so that it accepts either of libavcodec52 and libavcodec52-unstripped.
The way you suggested would mean you install both libavcodec52 and libavcodec52-unstripped on the same system, which is not possible as some of the files they contain are the same (unless you create a diversion of the files in one package to another location).

Here's the important part of the control file from the Karmic package:
```
Depends: [COLOR=Blue]libavcodec52 (>= 4:0.5+svn20090706-2ubuntu2) [COLOR=Red]|[/COLOR] [COLOR=Lime]libavcodec-extra-52 (>= 4:0.5+svn20090706)[/COLOR][/COLOR], [COLOR=Blue]libavcodec52 (<= 4:0.5+svn20090706-99)[COLOR=Lime] [COLOR=Red]|[/COLOR] libavcodec-extra-52 (<= 4:0.5+svn20090706-99)[/COLOR][/COLOR], libavutil-dev (= 4:0.5+svn20090706-2ubuntu2)
Suggests: libfaad-dev, libgsm1-dev, libogg-dev, libschroedinger-dev, libspeex-dev, libtheora-dev (>> 0.0.0.alpha4), libvorbis-dev, libx11-dev, libxext-dev, zlib1g-dev, libraw1394-dev, libdc1394-22-dev
```

---

### Post by skullmunky on 2009-12-02
Ah, yes, that makes more sense and is easier anyway.  Worked great - thanks!

---

