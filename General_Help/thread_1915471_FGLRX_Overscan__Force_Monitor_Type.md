---
title: "FGLRX Overscan / Force Monitor Type"
date: 2012-01-26
forum: General Help
---

### Post by lakerssuperman on 2012-01-26
I just upgraded to the AMD 12.1 driver.  However, this driver still incorrectly detects my Sylvania LCD tv as a projector and, as a result, doesn't give me an overscan slider in the driver display options.

I have tried some of the work arounds on various forum posts without any success.  Is there a way to force the driver to see the tv as a tv so that I can adjust the overscan?  Any help is greatly appreciated.

---

### Post by Mark Phelps on 2012-01-26
I don't have an immediate answer for you -- but if you go over to the Phoronix forums, they do a LOT of detailed configuring of AMD/ATI cards and drivers, and may have the details you want.

Good Luck

---

### Post by lakerssuperman on 2012-01-26
Thanks for the quickly reply.  I have been looking through the posts over there as well and haven't found anything that works yet.  I will keep checking here and on Phoronix and I will report back if I find something that works.

---

### Post by mpsrig on 2012-06-26
Hello, Sorry to revive the thread but I have the exact same issue w.r.t. the TV being detected as a projector under fglrx.  Did you ever find a solution?

---

### Post by lakerssuperman on 2012-07-06
I never found a solution to this issue with FGLRX.  However, I haven't tried the absolute latest driver as I started using the open source driver and forced my tv parameters using the drivers over/under scan abilities.  Obviously, this is not ideal if you need the performance of the FGLRX driver, but on this particular machine I have no need of it as it is a lower end 4xxx series and I don't need massive 3D performance.

Depending on your situation, using the oss driver may work for you as well.

---

### Post by stderr on 2012-07-06
If you're looking to get rid of black borders around the image, then this is something I dealt with recently under Fedora, although the same will apply under Ubuntu. See the last point on my fixing underscan post, regarding DigitalHDTVDefaultUnderscan.

[http://nixnote.blogspot.co.uk/2012/06/amd-catalyst-fixing-underscan.html]("http://nixnote.blogspot.co.uk/2012/06/amd-catalyst-fixing-underscan.html")

---

### Post by mpsrig on 2012-07-07
Yes this is exactly what I just figured out (albeit from a different posting).  I forget the syntax, but I set DigitalHDTVDefaultUnderscan to false (0).  This gave me a result similar to the settings of the OSS driver.  I then used XBMC directly to correct for the overscan.  I needed the FGLRX because of the HDMI audio support.

---

### Post by lakerssuperman on 2012-12-18
[https://bbs.archlinux.org/viewtopic.php?id=146103](https://bbs.archlinux.org/viewtopic.php?id=146103)

---

