---
title: "Pan Newsreader problem in 9.10"
date: 2009-11-04
forum: General Help
---

### Post by Waddle on 2009-11-04
Not able to see images in Pan. When I click on a .jpg file I get the following message:

Attachment not shown: MIME type image/jpeg; filename EC-085A.jpg

Can any kind soul tell how I can fix this so I can view images within Pan? 

Regards...

---

### Post by jasondean on 2009-11-04
> **Waddle said:**
> Not able to see images in Pan. When I click on a .jpg file I get the following message:

Attachment not shown: MIME type image/jpeg; filename EC-085A.jpg

Can any kind soul tell how I can fix this so I can view images within Pan? 

Regards...

Yeah I have the same error and found it very annoying to have to download the image first to view it. I tried compiling from source, but kept getting an error during the make process. The way I "fixed" the problem was to install the windows version of Pan via WINE.  You will need to install gtk-runtime libraries(which is on site) It works perfect. Hopefully the regular Linux version will be fixed soon. 

[http://paninstall.googlepages.com/](http://paninstall.googlepages.com/)

---

### Post by thewarlock on 2009-11-10
single part images work fine for me, but multi-part do not.
(can save and decode them just fine, but will not display)

This looks like a very old bug is back.

---

### Post by BCtom on 2009-12-07
Hello all, 

After doing some lurking in the PAN archives I found this: [http://lists.gnu.org/archive/html/pan-users/2009-10/msg00009.html](http://lists.gnu.org/archive/html/pan-users/2009-10/msg00009.html)

> Yes, this is a known bug.  AFAIK, K. Haley has a patch in his git 
repository for it, if you'd like to compile from source, and there's 
likely to be a new official version upstream in not /too/ long as well, 
if you'd like to wait for it. ...

Here's K Halay's GIT URI if you'd like to try it.  Note that you'll need 
git installed and will need to know how to update it, etc, unless you're 
doing just a one-time pull.

git://github.com/lostcoder/pan2.git
And...,

> I just got this and built it. I had to get the latest gmime (2.4.9 it  appears) as it was not happy with the older one in my Ubuntu 8.10  installation, and the 'make install' option of that put the libraries in  /usr/local/lib and not /usr/lib where the built pan expected them!

However, I noticed that this git version lacks the patch in  pan/tasks/decoder.cc to prevent "saving as executable" (see Walt's post  20/02/09 16:42 or my report  [https://bugs.launchpad.net/ubuntu/+source/pan/+bug/374097](https://bugs.launchpad.net/ubuntu/+source/pan/+bug/374097)).

It also still borks the multi-part uuencoded JPEG images (fix in Walt's  post 13/08/09 17:34) that are not strictly pan's fault, but something  that is kind of nice to be sorted by the change to uulib/uunconc.c
line 476.

Is that git repository the latest set, or have the above (at least, the  security patch) been included in another?

Regards,
PaulAnd..., here: [http://lists.gnu.org/archive/html/pan-users/2009-10/msg00008.html](http://lists.gnu.org/archive/html/pan-users/2009-10/msg00008.html)

> In any case, for the past few months we pan users have been blessed
with several patches submitted by K. Hailey, including a bug-fix
update to the code responsible for decoding multi-part jpegs.
I don't know whether the ubuntu devs have imported those patches
to their own pan package, but I suspect they have not.
The author of pan, Charles Kerr, announced in this group that he
will be including K. Hailey's patches in his next release of pan,
so I expect the jpeg problem will be fixed (fairly) soon, as long
as the ubuntu devs keep up with the latest pan code.
If you care to file an ubuntu bug, you can point the devs to the
posts from K. Hailey in this mailing list over the past few months.
Duncan? :o)Hope this helps, and answers some of your questions. I haven't tried the patch yet, but I may wait for the next version of pan to come out before then. 

Cheers!

---

### Post by jasondean on 2010-02-23
Just to update, I had been using the wine version since my last post but decided to try the git version listed in last post. I was able to compile and the multi-part bug is gone.

---

### Post by lan_rogers_book on 2010-12-20
It seems like the new GTK+ is causing the issue. I had the same problem but then I downgraded to version 2.10.13 and it worked like a charm.

---

### Post by RobHK on 2011-03-16
> **lan_rogers_book said:**
> It seems like the new GTK+ is causing the issue. I had the same problem but then I downgraded to version 2.10.13 and it worked like a charm.

How does one go about doing that?

---

