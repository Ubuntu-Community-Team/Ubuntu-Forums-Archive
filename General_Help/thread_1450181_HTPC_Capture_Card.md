---
title: "HTPC: Capture Card"
date: 2010-04-08
forum: General Help
---

### Post by Failboat88 on 2010-04-08
I'm not sure what kind of tuner I need. I live in Indiana, do I pick up ntsc, atsc, or something else? My cable comes from the wall to the tv, there is no box receiver. 
 
I have had real bad luck with the acermedia duet and the hauppage hvr-1250. Aperently, the aver duet has 0 support and I can't get the hvr-1250 to work. I'm running mythbuntu 10.04. I can't even get avi's I downloaded to play in mythtv. 
 
Anyone help me fix what I have or make a suggestion for a tuner-card that will work out of the box that is less then $100? I can't watch HD so I'm not concerned with that.

---

### Post by Psumi on 2010-04-08
[http://www.hauppauge.com/site/products/data_hvr850.html](http://www.hauppauge.com/site/products/data_hvr850.html)

---

### Post by Failboat88 on 2010-04-09
Thanks Psumi, for the info. Does this card work out of the box on linux? I may just do another return to newegg on my hvr-1250.


Edit: I just read some articles and it appears the 850 has bad support, unless those articles are out of date. Anyone else got some suggestions? Is non-hd cable NTSC, that is something I really want to know?

---

### Post by srs5694 on 2010-04-09
In the US, most cable and over-the-air TV is delivered in one of three forms:


[list]
[*]ATSC -- used for broadcast (over-the-air) digital TV
[*]QAM -- used for cable digital TV
[*]NTSC -- used for analog cable channels
[/list]


NTSC is the old analog standard. It used to be used for broadcast TV, but analog broadcasts were shut off some months ago in the US. (I believe some low-power stations are an exception to this rule, but I'm not positive of that.) Many cable companies still use NTSC for their basic-tier channels. ATSC and QAM are both pure-digital and can carry both standard definition (SD) and high definition (HD). If you don't put up an antenna, you won't need ATSC support; however, most or all cards that handle QAM can also handle ATSC. Whether you'll benefit from QAM depends on how many (if any) channels your cable provider delivers unencrypted. Whether you'll benefit from NTSC depends on whether your cable company still delivers analog signals, and if so for how long this support will continue. (Once they drop analog support, you'll need a converter box, which will complicate your DVR configuration.) So there really is no easy answer to which you need, although if you're using an old NTSC TV, all you're seeing now is NTSC. You might get fewer, the same, or more channels via QAM.

Unfortunately, I'm not familiar with the latest products, so I can't offer specific recommendations. I've got an old pcHDTV 3000 and an AVerMedia AVerTV A180 for QAM content and some older Hauppauge products for NTSC. My cable company (Cox) still delivers an analog basic cable tier, as well as unencrypted local HD and some local SD channels.

You may want to subscribe to the [MythTV mailing list](http://www.mythtv.org/mailman/listinfo/mythtv-users/) and/or check the [MythTV wiki](http://www.mythtv.org/wiki) for information on the latest cards; however, be aware that the wiki may not have the most up-to-date information.

---

