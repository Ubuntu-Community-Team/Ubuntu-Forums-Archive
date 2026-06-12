---
title: "alien to install novell groupwise rpm"
date: 2009-09-24
forum: General Help
---

### Post by whatch on 2009-09-24
I installed alien so I could convert the .rpm Novell Groupwise email client to a .deb.  When it is making the conversion in the terminal window it says:

Warning: Skipping conversion of scripts in package novell-groupwise-client: postinst postrm
Warning: Use the --scripts parameter to include the scripts.

The .deb package appears in the tmp folder where I did the conversion and I can install it with the debian package installer, but when I try to run the program nothing happens.  

What am I doing wrong and how do I fix?  Thanks.

---

### Post by ncweber on 2010-12-14
> **whatch said:**
> I installed alien so I could convert the .rpm Novell Groupwise email client to a .deb.  When it is making the conversion in the terminal window it says:

Warning: Skipping conversion of scripts in package novell-groupwise-client: postinst postrm
Warning: Use the --scripts parameter to include the scripts.

The .deb package appears in the tmp folder where I did the conversion and I can install it with the debian package installer, but when I try to run the program nothing happens.  

What am I doing wrong and how do I fix?  Thanks.

I realize that this is an old post, but I thought I'd respond to help people searching for answers in the future.  In this case, the system is actually telling you what to do.  When running alien, you need to add the --scripts parameter.

**[FONT=Courier New]sudo alien [/FONT]****[FONT=Courier New]--scripts [/FONT]****[FONT=Courier New]novell-groupwise-client-xxxxx.i586.rpm[/FONT]**

That should give you a working .deb file with which to properly install GroupWise into Ubuntu.  You can type **[FONT=Courier New]alien --help[/FONT]** to get more info about alien.

---

