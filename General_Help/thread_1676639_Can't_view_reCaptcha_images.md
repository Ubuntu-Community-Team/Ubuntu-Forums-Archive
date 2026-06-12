---
title: "Can't view reCaptcha images"
date: 2011-01-27
forum: General Help
---

### Post by keith1 on 2011-01-27
I'm using version 10.10.

I just noticed yesterday that when I try to register at a site the reCaptsha images don't show. Would this have anything to do with the recent updates?

The images show fine on my Mint machine and Windows machine - all using Firefox.

---

### Post by domzz on 2011-01-27
Try a different browser.

---

### Post by keith1 on 2011-01-27
Thanks for the reply - but I don't see it as a browser issue. The images show fine in FF on both my Mint and Windows machines. The images displayed just fine with FF on my Ubuntu machine until recently.

---

### Post by perspectoff on 2011-01-27
Got any security?

ReCaptcha uses scripts, so you must have scripts turned on (and the ReCaptcha site can't be blocked by NoScript or AdBlock).

---

### Post by keith1 on 2011-01-27
Nothing I know of would have scripts blocked. No "special" security programs installed. There have been a lot of updates lately, I still wonder if one of them didn't cause the problem?

---

### Post by keith1 on 2011-01-27
Well, first of all I must apologize to domzz - I "assumed" since I was using the same version of Firefox ( 3.6.13 ) on my Mint machine and everything worked fine, that it was not a browser issue. But..... I did try using Opera on my Ubuntu machine and the images show just fine. I guess I had a "duh" moment :( 

So... with that said, I did try disabling every addon in Firefox to no avail. Does this show anything that may be the culprit? - - - - 


        Application Basics
      

      
      


        
          
            
              Name
            

            	Firefox
          


            
          
            
              Version
            

            	3.6.13
          

            
          

            
              Profile Directory
            

            	
              
                Open Containing Folder
               
            
          


          
            

              Installed Plugins
            

            	
              about:plugins
            
          

            
          
            

              Build Configuration
            

            	
              about:buildconfig
            
          

        
      


      

      

        Extensions
      


      

        
          

            
              Name
            
            	
              Version
            
            	
              Enabled
            

            	
              ID
            
          

        
        
        Ubuntu Firefox Modifications	0.9rc2	true	[email]ubufox@ubuntu.com[/email]
Xmarks	3.9.2	true	[email]foxmarks@kei.com[/email]
BetterPrivacy	1.48.3	true	{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}
Ghostery	2.4.2	true	[email]firefox@ghostery.com[/email]
Adblock Plus	1.3.3	true	{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}
TrackMeNot	0.6.721	true	[email]trackmenot@mrl.nyu.edu[/email]
Linkification	1.3.8	true	{35106bca-6c78-48c7-ac28-56df30b51d2a}
WOT	20100908	true	{a0d7ccb3-214d-498b-b4aa-0e8fda9a7bf7}
TinEye Reverse Image Search	1.0	true	[email]tineye@ideeinc.com[/email]
Beef Taco (Targeted Advertising Cookie Opt-Out)	1.3.2	true	[email]john@velvetcache.org[/email]

      


      

      

        Modified Preferences
      


      

        
          
            Name

          
          
          	
            Value
          
        

        
        browser.history_expire_days.mirror	180
browser.places.importBookmarksHTML	false
browser.places.smartBookmarksVersion	2
browser.startup.homepage	[http://my.yahoo.com/](http://my.yahoo.com/)
browser.startup.homepage_override.mstone	rv:1.9.2.13
extensions.lastAppVersion	3.6.13
network.cookie.prefsMigrated	true
places.last_vacuum	1294516655
print.print_bgcolor	false
print.print_bgimages	false
print.print_colorspace	default
print.print_command	lpr ${MOZ_PRINTER_NAME:+-P"$MOZ_PRINTER_NAME"}
print.print_downloadfonts	false
print.print_edge_bottom	0
print.print_edge_left	0
print.print_edge_right	0
print.print_edge_top	0
print.print_evenpages	true
print.print_footercenter	
print.print_footerleft	&PT
print.print_footerright	&D
print.print_headercenter	
print.print_headerleft	&T
print.print_headerright	&U
print.print_in_color	true
print.print_margin_bottom	0.500000012107193
print.print_margin_left	0.500000012107193
print.print_margin_right	0.500000012107193
print.print_margin_top	0.500000012107193
print.print_oddpages	true
print.print_orientation	0
print.print_pagedelay	500
print.print_paper_data	0
print.print_paper_height	279.40
print.print_paper_name	na_letter
print.print_paper_size_type	1
print.print_paper_size_unit	1
print.print_paper_width	215.90
print.print_plex_name	default
print.print_printer	DESKJET-930C
print.print_resolution_name	default
print.print_reversed	false
print.print_scaling	  1.00
print.print_shrink_to_fit	true
print.print_to_file	false
print.print_unwriteable_margin_bottom	56
print.print_unwriteable_margin_left	25
print.print_unwriteable_margin_right	25
print.print_unwriteable_margin_top	25
print.printer_DESKJET-930C.print_bgcolor	false
print.printer_DESKJET-930C.print_bgimages	false
print.printer_DESKJET-930C.print_colorspace	default
print.printer_DESKJET-930C.print_command	lpr ${MOZ_PRINTER_NAME:+-P"$MOZ_PRINTER_NAME"}
print.printer_DESKJET-930C.print_downloadfonts	false
print.printer_DESKJET-930C.print_edge_bottom	0
print.printer_DESKJET-930C.print_edge_left	0
print.printer_DESKJET-930C.print_edge_right	0
print.printer_DESKJET-930C.print_edge_top	0
print.printer_DESKJET-930C.print_evenpages	true
print.printer_DESKJET-930C.print_footercenter	
print.printer_DESKJET-930C.print_footerleft	&PT
print.printer_DESKJET-930C.print_footerright	&D
print.printer_DESKJET-930C.print_headercenter	
print.printer_DESKJET-930C.print_headerleft	&T
print.printer_DESKJET-930C.print_headerright	&U
print.printer_DESKJET-930C.print_in_color	true
print.printer_DESKJET-930C.print_margin_bottom	0.500000012107193
print.printer_DESKJET-930C.print_margin_left	0.500000012107193
print.printer_DESKJET-930C.print_margin_right	0.500000012107193
print.printer_DESKJET-930C.print_margin_top	0.500000012107193
print.printer_DESKJET-930C.print_oddpages	true
print.printer_DESKJET-930C.print_orientation	0
print.printer_DESKJET-930C.print_pagedelay	500
print.printer_DESKJET-930C.print_paper_data	0
print.printer_DESKJET-930C.print_paper_height	279.40
print.printer_DESKJET-930C.print_paper_name	na_letter
print.printer_DESKJET-930C.print_paper_size_type	1
print.printer_DESKJET-930C.print_paper_size_unit	1
print.printer_DESKJET-930C.print_paper_width	215.90
print.printer_DESKJET-930C.print_plex_name	default
print.printer_DESKJET-930C.print_resolution_name	default
print.printer_DESKJET-930C.print_reversed	false
print.printer_DESKJET-930C.print_scaling	  1.00
print.printer_DESKJET-930C.print_shrink_to_fit	true
print.printer_DESKJET-930C.print_to_file	false
print.printer_DESKJET-930C.print_unwriteable_margin_bottom	56
print.printer_DESKJET-930C.print_unwriteable_margin_left	25
print.printer_DESKJET-930C.print_unwriteable_margin_right	25
print.printer_DESKJET-930C.print_unwriteable_margin_top	25
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_colorspace	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_downloadfonts	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_jobtitle	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_num_copies	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_orientation	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_paper_size	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_plex	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_printincolor	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_resolution	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.can_change_spoolercommand	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.colorspace.0.name	default
print.tmp.printerfeatures.CUPS/DESKJET-930C.colorspace.count	1
print.tmp.printerfeatures.CUPS/DESKJET-930C.has_special_printerfeatures	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.orientation.0.name	portrait
print.tmp.printerfeatures.CUPS/DESKJET-930C.orientation.1.name	landscape
print.tmp.printerfeatures.CUPS/DESKJET-930C.orientation.count	2
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.0.height_mm	210
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.0.is_inch	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.0.name	A5
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.0.width_mm	148
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.1.height_mm	297
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.1.is_inch	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.1.name	A4
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.1.width_mm	210
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.2.height_mm	420
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.2.is_inch	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.2.name	A3
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.2.width_mm	297
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.3.height_mm	279
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.3.is_inch	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.3.name	Letter
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.3.width_mm	215
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.4.height_mm	355
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.4.is_inch	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.4.name	Legal
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.4.width_mm	215
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.5.height_mm	431
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.5.is_inch	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.5.name	Tabloid
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.5.width_mm	279
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.6.height_mm	254
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.6.is_inch	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.6.name	Executive
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.6.width_mm	190
print.tmp.printerfeatures.CUPS/DESKJET-930C.paper.count	7
print.tmp.printerfeatures.CUPS/DESKJET-930C.plex.0.name	default
print.tmp.printerfeatures.CUPS/DESKJET-930C.plex.count	1
print.tmp.printerfeatures.CUPS/DESKJET-930C.resolution.0.name	default
print.tmp.printerfeatures.CUPS/DESKJET-930C.resolution.count	1
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_colorspace_change	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_downloadfonts_change	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_jobtitle_change	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_orientation_change	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_paper_size_change	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_plex_change	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_printincolor_change	true
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_resolution_change	false
print.tmp.printerfeatures.CUPS/DESKJET-930C.supports_spoolercommand_change	false
print.tmp.printerfeatures.DESKJET-930C.can_change_colorspace	false
print.tmp.printerfeatures.DESKJET-930C.can_change_downloadfonts	false
print.tmp.printerfeatures.DESKJET-930C.can_change_jobtitle	false
print.tmp.printerfeatures.DESKJET-930C.can_change_num_copies	true
print.tmp.printerfeatures.DESKJET-930C.can_change_orientation	true
print.tmp.printerfeatures.DESKJET-930C.can_change_paper_size	true
print.tmp.printerfeatures.DESKJET-930C.can_change_plex	false
print.tmp.printerfeatures.DESKJET-930C.can_change_printincolor	true
print.tmp.printerfeatures.DESKJET-930C.can_change_resolution	false
print.tmp.printerfeatures.DESKJET-930C.can_change_spoolercommand	false
print.tmp.printerfeatures.DESKJET-930C.colorspace.0.name	default
print.tmp.printerfeatures.DESKJET-930C.colorspace.count	1
print.tmp.printerfeatures.DESKJET-930C.has_special_printerfeatures	true
print.tmp.printerfeatures.DESKJET-930C.orientation.0.name	portrait
print.tmp.printerfeatures.DESKJET-930C.orientation.1.name	landscape
print.tmp.printerfeatures.DESKJET-930C.orientation.count	2
print.tmp.printerfeatures.DESKJET-930C.paper.0.height_mm	210
print.tmp.printerfeatures.DESKJET-930C.paper.0.is_inch	false
print.tmp.printerfeatures.DESKJET-930C.paper.0.name	A5
print.tmp.printerfeatures.DESKJET-930C.paper.0.width_mm	148
print.tmp.printerfeatures.DESKJET-930C.paper.1.height_mm	297
print.tmp.printerfeatures.DESKJET-930C.paper.1.is_inch	false
print.tmp.printerfeatures.DESKJET-930C.paper.1.name	A4
print.tmp.printerfeatures.DESKJET-930C.paper.1.width_mm	210
print.tmp.printerfeatures.DESKJET-930C.paper.2.height_mm	420
print.tmp.printerfeatures.DESKJET-930C.paper.2.is_inch	false
print.tmp.printerfeatures.DESKJET-930C.paper.2.name	A3
print.tmp.printerfeatures.DESKJET-930C.paper.2.width_mm	297
print.tmp.printerfeatures.DESKJET-930C.paper.3.height_mm	279
print.tmp.printerfeatures.DESKJET-930C.paper.3.is_inch	true
print.tmp.printerfeatures.DESKJET-930C.paper.3.name	Letter
print.tmp.printerfeatures.DESKJET-930C.paper.3.width_mm	215
print.tmp.printerfeatures.DESKJET-930C.paper.4.height_mm	355
print.tmp.printerfeatures.DESKJET-930C.paper.4.is_inch	true
print.tmp.printerfeatures.DESKJET-930C.paper.4.name	Legal
print.tmp.printerfeatures.DESKJET-930C.paper.4.width_mm	215
print.tmp.printerfeatures.DESKJET-930C.paper.5.height_mm	431
print.tmp.printerfeatures.DESKJET-930C.paper.5.is_inch	true
print.tmp.printerfeatures.DESKJET-930C.paper.5.name	Tabloid
print.tmp.printerfeatures.DESKJET-930C.paper.5.width_mm	279
print.tmp.printerfeatures.DESKJET-930C.paper.6.height_mm	254
print.tmp.printerfeatures.DESKJET-930C.paper.6.is_inch	true
print.tmp.printerfeatures.DESKJET-930C.paper.6.name	Executive
print.tmp.printerfeatures.DESKJET-930C.paper.6.width_mm	190
print.tmp.printerfeatures.DESKJET-930C.paper.count	7
print.tmp.printerfeatures.DESKJET-930C.plex.0.name	default
print.tmp.printerfeatures.DESKJET-930C.plex.count	1
print.tmp.printerfeatures.DESKJET-930C.resolution.0.name	default
print.tmp.printerfeatures.DESKJET-930C.resolution.count	1
print.tmp.printerfeatures.DESKJET-930C.supports_colorspace_change	false
print.tmp.printerfeatures.DESKJET-930C.supports_downloadfonts_change	false
print.tmp.printerfeatures.DESKJET-930C.supports_jobtitle_change	false
print.tmp.printerfeatures.DESKJET-930C.supports_orientation_change	true
print.tmp.printerfeatures.DESKJET-930C.supports_paper_size_change	true
print.tmp.printerfeatures.DESKJET-930C.supports_plex_change	false
print.tmp.printerfeatures.DESKJET-930C.supports_printincolor_change	true
print.tmp.printerfeatures.DESKJET-930C.supports_resolution_change	false
print.tmp.printerfeatures.DESKJET-930C.supports_spoolercommand_change	false
privacy.sanitize.migrateFx3Prefs	true
privacy.sanitize.timeSpan	0
security.warn_viewing_mixed	false

---

### Post by keith1 on 2011-01-28
Alrighty, I found the problem. Under Preferences/ Content/ Load images Automatically - I, for some reason I don't recall, had Google.com as an exception. So I removed it and all works fine now. Well. I now know that Google owns ReCaptcha. 

Thanks for your input,     Keith

---

