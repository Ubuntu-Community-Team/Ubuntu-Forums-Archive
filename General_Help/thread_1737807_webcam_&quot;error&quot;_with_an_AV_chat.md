---
title: "webcam &quot;error&quot; with an AV chat"
date: 2011-04-23
forum: General Help
---

### Post by Comrade7 on 2011-04-23
Greetings.
So, I've got a Toshiba Satellite a505s6020 that's been running ubuntu  10.10 flawlessly for some time now. However I've come across something I  can't figure out.
My laptop has an internal web camera, but I'd like to use the Microsoft HD lifecam here > [http://www.darkstarlings.com/chat/](http://www.darkstarlings.com/chat/)

The microsoft usb cam works just fine in skype, and what gets me is the  chat rooms "options" let's me select the usb cam, but still runs the  internal.

Other than disabling the internal, does anyone have any ideas? Don't get  me wrong though, I'm all for disabling the internal if It'll make the  USB one work in the chat.

Thanks in advance.
 		                   		  		  		  		  		  	   	 		 
	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] []("http://ubuntuforums.org/editpost.php?do=editpost&p=10709212")

---

### Post by no2498 on 2011-04-24
see what cam's are listed in open a terminal type gstreamer-properties click enter

click video should have both listed pick the 1 you use
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

