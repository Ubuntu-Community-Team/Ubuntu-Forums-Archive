---
title: "Mencoder converting files"
date: 2009-07-12
forum: General Help
---

### Post by gavoby on 2009-07-12
I tried to convert an MKV file to AVI and used a command I got from a website this is what i got.
gavin@gavin-desktop:~$ mencoder Dan.Henderson.vs.Michael.Bisping.mkv -ffourcc xvid -ovc lavc -lavcopts vcodec=xvid:vhq:vbitrate=1800 -oac mp3lame -lameopts vbr=5 -o output_video.avi
MEncoder SVN-r29333-4.3.3 (C) 2000-2009 MPlayer Team
MPlayer was compiled without libmp3lame support.
-lameopts is not an MEncoder option

Exiting... (error parsing command line)

I tired to download the libmp3lame support but couldnt open the pakage.
any help?

---

### Post by geirha on 2009-07-12
Did you build mencoder yourself? If so you may want to build it again, with lame support. ```
sudo apt-get build-dep mencoder
``` should install all the necessary dev packages.

The mencoder in the repositories has lame support btw.

---

### Post by gavoby on 2009-07-12
I  just tried it but same thing came up.

---

### Post by Hobgoblin on 2009-07-12
> **geirha said:**
> 
The mencoder in the repositories has lame support btw.

I thought Ubuntu didn't have mp3 support by default.

IRT gavboy.  have you added the [medibuntu](http://packages.medibuntu.org/) repositories?

---

### Post by gavoby on 2009-07-12
no how do i do that?

---

### Post by andrew.46 on 2009-07-13
Hi gavoby,

> **gavoby said:**
> no how do i do that?

Details of how to enable the Medibuntu repository for your version of Ubuntu can be found here:

Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

But as geirha has mentioned it looks like you have picked up a more recent version of MEncoder? Your version appears to be:

```
MEncoder SVN-r29333-4.3.3 (C) 2000-2009 MPlayer Team
```

 In this case the Medibuntu version will be a lot older. Have you compiled your own or is this from the pre-rc3 stream adopted by Debian and Ubuntu? If so it is a rather older compilation as the current version is:

```
MEncoder SVN-r29417-4.2.4 (C) 2000-2009 MPlayer Team
```

All the best,

Andrew

---

