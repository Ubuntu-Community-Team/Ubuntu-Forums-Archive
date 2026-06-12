---
title: "Delete and Reinstall MX860 Wireless?"
date: 2011-11-15
forum: General Help
---

### Post by mcman56 on 2011-11-15
After switching wireless routers, I had a issue where only partial pages would get printed.  Using windows mentality, I though I would delete and reload the driver.  I deleted but when I went to reload, the printer was not seen.  After switching back to my original router, the issue still exists.  I can print to it wirelessly from a windows system.  This is 10.04 and the wireless Internet works.  Did I miss a step or??

I loaded the drivers like this:  
 				 				**Re: Canon MX printer installation on Kubuntu Lucid 10.04 AMD64** 			
 			 			 		   		 		 		[FONT=Trebuchet MS][SIZE=2][COLOR=Navy]Excellent  thread and work; very helpful.  I had explored the same about a year  ago and the following has worked for me several times after performing  clean Ubuntu installs including Ubuntu 10.10.  I too have a Canon MX860  configured wirelessly.  The procedure is similar to the original post,  just slightly simpler:

[SIZE=3]Go to the Canon site in Australia and download the [Linux debian driver for the MX860]("http://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwMTg3NzAx&cmp=ABS&lang=EN").  After unpackaging the compressed driver:
[/SIZE][/COLOR][/SIZE][/FONT][INDENT][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]1. First, install cnijfilter-common_3.10-1_i386.deb[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]2. Second, install cnijfilter-mx860series_3.10-1_i386.deb[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]3. Restart Ubuntu[/COLOR][/SIZE][/FONT][SIZE=3]

[/SIZE][FONT=Trebuchet MS][SIZE=3][COLOR=Navy]4. System -> Adminstration -> Printing -> New[/COLOR][/SIZE][/FONT]
[FONT=Trebuchet MS][SIZE=2][COLOR=RoyalBlue]It  should search for and find the Canon- MX860 printer as a Network Printer  with a device URI that looks like: cnijnet:/00-1E-8F-72-E6-2H[/COLOR][/SIZE][/FONT]
[/INDENT][SIZE=2][COLOR=Navy]Using the procedure above, both the printing and scanning functions work for me on the MX86[/COLOR][/SIZE]

---

