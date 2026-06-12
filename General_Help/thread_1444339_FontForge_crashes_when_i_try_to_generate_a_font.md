---
title: "FontForge crashes when i try to generate a font"
date: 2010-04-01
forum: General Help
---

### Post by Xendric on 2010-04-01
Hi there

I've been using a .fon font under windows for a work application environment, and since it's a greek font, I can't replace it with something else that is already ttf.

So I tried converting it to ttf with FontForge, but whenever I get to the point to "Generate Font", the FF window disappears and no font is created.

I ran it from a terminal window, in order to see what happens behind the scenes when it crashes, and this is what I'm getting:

[SIZE=1]*** stack smashing detected ***: fontforge terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x4:cool:[0x206bed8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0x206be90]
/usr/lib/libgunicode.so.3[0x7a77c4]
/usr/lib/libgunicode.so.3[0x7a6304]
[0x36312c33]
======= Memory map: ========
00110000-002ff000 r-xp 00000000 08:05 305        /usr/lib/libpython2.6.so.1.0
.
.
.
.
.
00be2000-00be3000 r--p 00022000 08:05 2830       /usr/lib/libpng12.so.0.37.0
00be3000-00be4000 rw-p 00023000 08:05 2830       /usr/lib/libpng12.so.0.37.0
00be4000-00bf8000 r-xp 00000000 08:05 676        /lib/libz.so.1.2.3.3
00bf8000-00bf9000 r--p 00013000 08:05 676        /lib/libz.so.1.2.3.3
00bf9000-00bfa000 rw-p 00014000 08:05 676        /lib/libz.so.1.2.3.3Aborted"[/SIZE]  
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9054528") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=9054528") 		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9054528") 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9054528") 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9054528") 		 		 		 		 		 			 		 		 		 	       	 	 		Xendric 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=1045009") 	 	 		[Send a private message to Xendric]("http://ubuntuforums.org/private.php?do=newpm&u=1045009") 	 	 	 	 		[Find More Posts by Xendric]("http://ubuntuforums.org/search.php?do=finduser&u=1045009") 	 	 	[Add Xendric to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=1045009") 	 	 	 
  	                 	 	 		 	       	   	 		  	 	      
Now, I've already tried removing and reinstalling FF, didnt work.
I'm getting this message every time I try to convert a font to some other format, no matter what the initial and final formats may be. It always crashes and no font is generated.

Not sure if it's important, but when i try to rerun FF, it says there is a pending project that refers to my last attempt to convert something. But that could be after like 3 hours, so it's not like it's gonna make it eventually.

Any ideas?

---

