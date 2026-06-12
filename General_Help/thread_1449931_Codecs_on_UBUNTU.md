---
title: "Codecs on UBUNTU"
date: 2010-04-08
forum: General Help
---

### Post by hugo007 on 2010-04-08
Does anyone can tell me how can I install codecs like mp4 and divx for my ubuntu can play media files.
I tryied to find in web but I still have problems with codecs.

---

### Post by rcayea on 2010-04-08
You might be able to do so by going to [www.medibuntu.org](www.medibuntu.org)

---

### Post by jimmers on 2010-04-08
Try This:-
  	 	 	 	 	 	  

  	**[[COLOR=#000080][IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/logo.png[/IMG][/COLOR]]("http://help.ubuntu.com/")**

 
  	 	 		
   	 	document.write('<form 	action="https://help.ubuntu.com/search.html" 	id="cse-search-box">');
 document.write('  <div>');
	document.write('    <input type="hidden" name="cof" 	value="FORID:9" />');
 document.write('    <input 	type="hidden" name="cx" 	value="004599128559784038176:vj_p0xo-nng" />');
	document.write('    <input type="hidden" name="ie" 	value="UTF-8" />');
 document.write('    <input 	type="text" name="q" size="27" />');
	document.write('    <input type="submit" name="sa" 	value="Search" />');
 document.write('  </div>');
	document.write('</form>'); 	 		
   	[[COLOR=#000080][IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/help-faq.png[/IMG][/COLOR]]("https://help.ubuntu.com/community")[Community 	Documentation]("https://help.ubuntu.com/community")
 
 
[LIST]
[*][Login 	to Edit]("https://help.ubuntu.com/community/RestrictedFormats?action=login")
[/LIST]
  	

	
 	 		[Ubuntu 		Documentation]("https://help.ubuntu.com/") > [Community 		Documentation]("https://help.ubuntu.com/community") > [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=linkto%3A%22RestrictedFormats%22") 				
 	
 	
[LIST]
[*][RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats?action=fullsearch&context=180&value=linkto%3A%22RestrictedFormats%22") 		 		
[/LIST]
 	 		 		
		
 		 			 			 				 					Contents
 					
[LIST=1]
[*][Introduction]("https://help.ubuntu.com/community/RestrictedFormats#Introduction")
[*][Playing 						Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats")

[LIST=1]
[*][Ubuntu 							9.04 (Jaunty Jackalope) and 9.10 (Karmic Koala)]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04%20%28Jaunty%20Jackalope%29%20and%209.10%20%28Karmic%20Koala%29")
[*][Ubuntu 							9.04, 8.10, 8.04]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04,%208.10,%208.04")
[/LIST]
 						
[*][Detailed 						Instructions and Troubleshooting]("https://help.ubuntu.com/community/RestrictedFormats#Detailed%20Instructions%20and%20Troubleshooting")

[LIST=1]
[*][Audio]("https://help.ubuntu.com/community/RestrictedFormats#Audio")
[*][DVD]("https://help.ubuntu.com/community/RestrictedFormats#DVD")
[*][Web]("https://help.ubuntu.com/community/RestrictedFormats#Web")
[*][Video]("https://help.ubuntu.com/community/RestrictedFormats#Video")
[*][Other]("https://help.ubuntu.com/community/RestrictedFormats#Other")
[/LIST]
 						
[*][The 						Ubuntu and Kubuntu Media Players]("https://help.ubuntu.com/community/RestrictedFormats#The%20Ubuntu%20and%20Kubuntu%20Media%20Players")
[*][See 						also]("https://help.ubuntu.com/community/RestrictedFormats#See%20also")
[/LIST]
 				 			 		 		** 		Introduction**

 		 		**See ****[Multimedia 		Codecs]("https://help.ubuntu.com/8.04/musicvideophotos/C/codecs.html")**** and ****[Playing 		proprietary formats]("https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-badformats")**** for 		official documentation on this issue.** 		 		
 		Ubuntu 		strives to make all software that meets the licensing terms in the 		[Ubuntu 		License Policy]("http://www.ubuntu.com/ubuntu/licensing") available. However patent and 		copyright restrictions complicate free operating systems 		distributing software to support proprietary formats.  		
 		 		Ubuntu's commitment to only include completely free software by 		default means that proprietary media formats are not configured 		'out of the box'.  		
 		 		Ubuntu can play the most popular non-free media formats, including 		DVD, MP3, Quicktime, Windows Media, and more by following the 		instructions below. If this seems like unnecessary work, remember 		that Ubuntu is a distribution of free software and these packages 		are (at least arguably) affected by patents and license 		restrictions in some countries. Avoid formats suppressed by DRM 		(Digital Rights Management, or Digital Restrictions Management), as 		they are often unplayable.  		
 		See 		Ubuntu's [Free 		Software Philosophy]("http://www.ubuntu.com/ubuntu/philosophy") and the [Free 		Formats]("https://help.ubuntu.com/community/FreeFormats") page for a more comprehensive 		discussion of these issues.  		
 		
[LIST]
[*] 			**Legal Notice** 			*Patent and copyright laws operate 			differently depending on which country you are in. Please obtain 			legal advice if you are unsure whether a particular patent or 			restriction applies to a media format you wish to use in your 			country.*  			
[/LIST]
 		** 		Playing Restricted Formats**

 		 		Follow these steps to play and record most common multimedia 		formats, including MP3, DVD, Flash, Quicktime, WMA and WMV, 		including both standalone files and content embedded in web pages.  		
 		** 		Ubuntu 9.04 (Jaunty Jackalope) and 9.10 (Karmic Koala)**

 		 		**[Click 		here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")** 		 		
 		If you are using 		a different derivative of Ubuntu, install one of these instead:  		
 		
[LIST]
[*][kubuntu-restricted-extras]("apt:kubuntu-restricted-extras?section=universe?section=multiverse") 			 			
[*] 			[xubuntu-restricted-extras]("apt:xubuntu-restricted-extras?section=universe?section=multiverse") 			 			
[/LIST]
 		 		To play DVDs, you also need to install libdvdcss by opening a 		terminal and entering the following in addition to installing the 		restricted extras package:  		
 		 sudo /usr/share/doc/libdvdread4/install-css.sh 		 		*The instructions below for 8.10 and 8.04 should 		still also work.*  		
 		** 		Ubuntu 9.04, 8.10, 8.04**

 		** 		Synaptic**

 		
[LIST]
[*] 			Go to **Applications** 			&#8594; **Add/Remove...** 			 			
[*]Set 			Show: to **All available applications** 			 			
[*] 			Search for **ubuntu-restricted-extras** 			and install it. Note that there is also **xubuntu-restricted-extras** 			(for Xubuntu) and **kubuntu-restricted-extras** 			(for Kubuntu.)  			
[/LIST]
 		Or open the 		Terminal, and execute the following command:  		
 		
[LIST]
[*]sudo apt-get install ubuntu-restricted-extras
[/LIST]
 		** 		Detailed Instructions and Troubleshooting**

 		** 		Audio**

 		
[LIST]
[*] 			[Ripping CDs]("https://help.ubuntu.com/community/CDRipping") 			 			
[*][Converting 			your audio files and video to open formats]("https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen")  			
[*][Using 			the iTunes Music Store]("https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore")  			
[*][MP3]("https://help.ubuntu.com/community/RestrictedFormats/MP3") 			 			
[*][Playing 			or ripping CDs to AAC (.m4a) files]("https://help.ubuntu.com/community/RestrictedFormats/AAC")  			
[/LIST]
 		**DVD**

 		
[LIST]
[*] 			[Playing 			DVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")  			
[*][Ripping 			DVDs]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs")  			
[*][Playing 			Blu Ray and HD DVD]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")  			
[/LIST]
 		**Web**

 		
[LIST]
[*] 			[Playing 			Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")  			
[*] 			[Adobe 			Shockwave]("https://help.ubuntu.com/community/Shockwave") No native version.  			
[/LIST]
 		**Video**

 		
[LIST]
[*] 			[Streaming 			Video]("https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo")  			
[*][HelixPlayer]("https://help.ubuntu.com/community/HelixPlayer") 			 			
[*][Realplayer]("https://help.ubuntu.com/community/RealPlayerInstallationMethods") 			 			
[*][Smil]("https://help.ubuntu.com/community/RestrictedFormats/Smil") 			 			
[*] 			[Apple 			Quicktime and RealVideo]("https://help.ubuntu.com/community/Medibuntu")  			
[/LIST]
 		**Other**

 		
[LIST]
[*] 			[Java]("https://help.ubuntu.com/community/Java") 			 			
[*] 			[Installing 			popular fonts from Microsoft]("https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts")  			
[/LIST]
 		** 		The Ubuntu and Kubuntu Media Players**

 		
[LIST]
[*] 			**Ubuntu** 			comes with [Totem]("https://help.ubuntu.com/community/MultimediaApplications#totem") 			(a movie player) and [Rhythmbox]("https://help.ubuntu.com/community/MultimediaApplications#rhythmbox") 			(a music player)  			
[*] 			**Kubuntu** 			includes [Kaffeine]("https://help.ubuntu.com/community/MultimediaApplications#kaffeine") 			(a multimedia player) and [Amarok]("https://help.ubuntu.com/community/MultimediaApplications#amarok") 			(a music player)  			
[/LIST]
 		 		These media players support free formats (Ogg Vorbis, Ogg Theora, 		and similar formats) 'out of the box'. However, they can also play 		most non-free media formats if you install the additional gstreamer 		(for Ubuntu only) or libxine1 (for Kubuntu only) packages listed 		above.  		
 		[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=eyes.png[/IMG] 		See [Multimedia 		Applications]("https://help.ubuntu.com/community/MultimediaApplications") for an overview of the most 		popular media players for Ubuntu and Kubuntu.  		
 		**See also**

 		
[LIST]
[*] 			[InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware") 			 			
[*] 			[MultimediaApplications]("https://help.ubuntu.com/community/MultimediaApplications") 			 			
[*] 			[Multimedia 			How To from the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=766683")  			
[*] 			[MPlayer]("https://help.ubuntu.com/community/MPlayer") 			 			
[*] 			The [free 			formats]("https://help.ubuntu.com/community/FreeFormats") page  			
[*] 			Ubuntu's [Free 			Software Philosophy]("http://www.ubuntu.com/ubuntu/philosophy")  			
[*] 			[Wikipedia 			article on Open Formats]("http://en.wikipedia.org/wiki/Open_format")  			
[*] 			[Wikipedia 			article on CSS]("http://en.wikipedia.org/wiki/Content-scrambling_system")  			
[*] 			[Debian-Marillat 			Repositories]("http://www.debian-multimedia.org/")  			
[*] 			[GNU Gnash]("http://www.gnu.org/software/gnash/"), 			a GNU flash player (alpha)  			
[*] 			[Ubuntu 			Customization Guide]("http://www.ubuntuforums.org/forumdisplay.php?f=159") resembles Easy Ubuntu and 			Ubuntu Guide. But it has another focus as it tries to teach and 			link to existing documentation.  			
[/LIST]
 		 	
 	RestrictedFormats 	(last edited 2009-12-31 22:33:16 by [Jeremy 	Pallats (starcraft.man)]("https://launchpad.net/%7Estarcraft.man"))
 	
[LIST]
[*][Page 		History]("https://help.ubuntu.com/community/RestrictedFormats?action=info")  		
[/LIST]
 	 		

		
 	
 
  The material on this wiki is available under a free license, see [Copyright / License]("https://help.ubuntu.com/community/License") for details
**You** can contribute to this wiki, see [Wiki Guide]("https://help.ubuntu.com/community/WikiGuide") for details

---

### Post by uRock on 2010-04-08
Installing ubuntu-restricted-extras via Ubuntu Software Center or Synaptic Package Manager should do the job for you. If you are comfortable with running commands in a terminal, open one up and enter this code, ```
sudo apt-get install ubuntu-restricted-extras
```

Cheers,
Ronnie

---

### Post by cogier on 2010-04-08
Go to Application>Ubuntu Software Centre (This is on Ubuntu 9.10). Type **rest** in the search window and install the restrictive software.

Then follow this link [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")to add all the other code required to get DVDs etc working.

---

### Post by suyashpandit on 2010-04-08
its find itself man

this feature attracted me a lot

---

