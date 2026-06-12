---
title: "Can't Install ffmpeg"
date: 2012-10-03
forum: General Help
---

### Post by khoraski on 2012-10-03
I want to use ffmpeg, but when I try to use "apt-get install ffmpeg" I get this as a result:

```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (< 4:0.5.1-99) but it is not going to be installed or
                   libavcodec-extra-52 (< 4:0.5.1-99) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed
          Depends: libavdevice52 (>= 4:0.5.1-1ubuntu1) but it is not going to be installed or
                   libavdevice-extra-52 (>= 4:0.5.1-1ubuntu1) but it is not going to be installed
          Depends: libavdevice52 (< 4:0.5.1-99) but it is not going to be installed or
                   libavdevice-extra-52 (< 4:0.5.1-99) but it is not going to be installed
          Depends: libavfilter0 (>= 4:0.5.1-1ubuntu1) but it is not going to be installed or
                   libavfilter-extra-0 (>= 4:0.5.1-1ubuntu1) but it is not going to be installed
          Depends: libavfilter0 (< 4:0.5.1-99) but it is not going to be installed or
                   libavfilter-extra-0 (< 4:0.5.1-99) but it is not going to be installed
          Depends: libavformat52 (< 4:0.5.1-99) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed or
                   libavformat-extra-52 (< 4:0.5.1-99) but it is not going to be installed
          Depends: libavutil49 (< 4:0.5.1-99) but it is not going to be installed or
                   libavutil-extra-49 (< 4:0.5.1-99) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed
          Depends: libpostproc51 (< 4:0.5.1-99) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed or
                   libpostproc-extra-51 (< 4:0.5.1-99) but it is not going to be installed
          Depends: libswscale0 (< 4:0.5.1-99) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed or
                   libswscale-extra-0 (< 4:0.5.1-99) but it is not going to be installed
E: Broken packages
```

I tried looking it up, but I can't find any solutions. I've never really had broken package errors, so I don't know how to deal with them.

I also tried installing it via Synaptic but that didn't work either.

---

### Post by raja.genupula on 2012-10-03
[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)

---

### Post by oldos2er on 2012-10-04
> **khoraski said:**
> I also tried installing it via Synaptic but that didn't work either.

In Synaptic, click menus Edit, Fix Broken Packages.

---

### Post by khoraski on 2012-10-04
> **oldos2er said:**
> In Synaptic, click menus Edit, Fix Broken Packages.

Not working. None of these solutions are working.

---

### Post by Stonecold1995 on 2012-10-04
Try running this:

```
sudo apt-get -f install
```

---

### Post by oldos2er on 2012-10-04
> **khoraski said:**
> Not working. None of these solutions are working.

Do you see any error messages?

---

### Post by Stonecold1995 on 2012-10-05
If you can't get ffmpeg to install, you could try using avconv instead.  In fact, ffmpeg is deprecated (when you run it, it gives the warning "This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.").

You can install avconv by running:

```
sudo apt-get install libav-tools
```

---

### Post by spaceshipguy on 2012-10-05
If you want ffmpeg, make sure you get all the codecs that you'll need. 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by khoraski on 2012-10-05
> **Stonecold1995 said:**
> If you can't get ffmpeg to install, you could try using avconv instead.  In fact, ffmpeg is deprecated (when you run it, it gives the warning "This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.").

You can install avconv by running:

```
sudo apt-get install libav-tools
```

```
Package libav-tools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libav-tools has no installation candidate
```

---

### Post by mc4man on 2012-10-05
Should mention what release of Ubuntu you are on, seems like lucid (10.04

open up Software Sources, (software-properties-gtk),  make sure that under the 'Updates' tab that the 1st 2 are enabled, (security & updates
Then reload the sources & or run 
sudo apt-get update

---

### Post by khoraski on 2012-10-05
> **mc4man said:**
> Should mention what release of Ubuntu you are on, seems like lucid (10.04

open up Software Sources, (software-properties-gtk),  make sure that under the 'Updates' tab that the 1st 2 are enabled, (security & updates
Then reload the sources & or run 
sudo apt-get update

That was a rather... simple solution. 

Thanks.

---

