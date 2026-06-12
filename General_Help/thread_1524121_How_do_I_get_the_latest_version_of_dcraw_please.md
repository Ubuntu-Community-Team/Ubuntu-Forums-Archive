---
title: "How do I get the latest version of dcraw please?"
date: 2010-07-04
forum: General Help
---

### Post by cogvos on 2010-07-04
Dear all,

The packaged version of dcraw - the raw file conversion tool thing - that comes with Ubuntu 9.10 is (according to synaptic) 8.86-1. However I need a version of at least 8.88, which has support for .rw2 files (panasonic et al). The latest source on Dave Coffin's (the developer) web site is 9.03 -though thsi goes on about restricted functions - no idea if this is a problem I'm not a coder.

Can someone tell me, simply, where I can get a version of dcraw that is at least 8.88, or how to compile the version from Dave's web site?
I downloaded and

gcc dcraw-1.c -o dcraw

Gave 

dcraw-1.c:52:18: error: lcms.h: No such file or directory
dcraw-1.c: In function &#8216;apply_profile&#8217;:
dcraw-1.c:8080: error: &#8216;cmsHPROFILE&#8217; undeclared (first use in this function)
dcraw-1.c:8080: error: (Each undeclared identifier is reported only once
dcraw-1.c:8080: error: for each function it appears in.)
dcraw-1.c:8080: error: expected &#8216;;&#8217; before &#8216;hInProfile&#8217;
dcraw-1.c:8081: error: &#8216;cmsHTRANSFORM&#8217; undeclared (first use in this function)
dcraw-1.c:8081: error: expected &#8216;;&#8217; before &#8216;hTransform&#8217;
dcraw-1.c:8085: error: &#8216;LCMS_ERROR_SHOW&#8217; undeclared (first use in this function)
dcraw-1.c:8087: error: &#8216;hInProfile&#8217; undeclared (first use in this function)
dcraw-1.c:8099: error: &#8216;hOutProfile&#8217; undeclared (first use in this function)
dcraw-1.c:8116: error: &#8216;hTransform&#8217; undeclared (first use in this function)
dcraw-1.c:8116: error: &#8216;TYPE_RGBA_16&#8217; undeclared (first use in this function)
dcraw-1.c:8117: error: &#8216;INTENT_PERCEPTUAL&#8217; undeclared (first use in this function)

So I am baffled...

Duh! It does compile if you read the instructions - oops!

---

