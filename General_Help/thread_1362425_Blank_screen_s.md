---
title: "Blank screen :s"
date: 2009-12-23
forum: General Help
---

### Post by charlie1989 on 2009-12-23
Hi,
I'm having a problem with my webbook, when I turn it on all the start up images come up on screen "ubuntu logo etc" but it goes completely black at the log in screen, I'm completely new to the system so don't understand the majority of it, I think I may have made the problem worse by deleting my user account so can no longer log in (I could previously log in "blindly" despite the blank screen.

I've read through a few posts on this site and understand there's a way of changing settings e.t.c with root commands? I'm able to access all the start up menus but have no idea what I'm doing...

If anyone could give me a step by step walk through of how to fix it, would be hugely appriciated! need to get it back online a.s.ap :s


 		                   		  		  		  		  		  	   	
	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] []("http://ubuntuforums.org/editpost.php?do=editpost&p=8530933")    		 		 		 		 		 			 		 		 		 	       	 	 		charlie1989 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=981324") 	 	 		[Send a private message to charlie1989]("http://ubuntuforums.org/private.php?do=newpm&u=981324") 	 	 		[Send email to charlie1989]("http://ubuntuforums.org/sendmessage.php?do=mailmember&u=981324") 	 	 	 		[Find More Posts by charlie1989]("http://ubuntuforums.org/search.php?do=finduser&u=981324") 	 	 	[Add charlie1989 to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=981324") 	 	 	 
  	                 	 	 		 	       	  [CENTER] 	[LEFT] 		[LEFT]  	 	           				           	 		It's an Elonex Webbook, 
model:LNXWB1OLSFL2/090
I think the operating system is "Ubunto 8.04.1" 		
	   	thankyou in advance,
Charlie 	 	
  	 		
  		 		  	 	 	 	 		   		 		 		 		 		 			 		 		 		 	       	 	 		Gtklocker 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=981315") 	 	 		[Send a private message to Gtklocker]("http://ubuntuforums.org/private.php?do=newpm&u=981315") 	 	 	 		[Visit Gtklocker's homepage!]("http://rsync.wordpress.com/") 	 	 		[Find More Posts by Gtklocker]("http://ubuntuforums.org/search.php?do=finduser&u=981315") 	 	 	[Add Gtklocker to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=981315") 	 	 	 
  	
    
   
     
     	
 	 		[/LEFT]
 	[/LEFT]
 [/CENTER]

---

### Post by annasarp on 2009-12-23
are you running ubuntu as dual boot or from the cd ??
are any other OS installed in your system like windows??

---

### Post by charlie1989 on 2009-12-23
I'm completely new to the system so don't understand a lot about it :s
it's not running from a c.d though (no c.d drive) it may be running a duel boot though? I'm not really sure what one is.

and it definitely isn't running on windows, I haven't made any modifications so everything on it is the basic package (how it was brought) :)

---

### Post by nothingspecial on 2009-12-23
The first thing you need to do is create a new administrative user.

Restart the computer and when you see the "grub loading" dialogue press escape.

Log in to a root recovery shell (or whatever they called it in 8.04)

Type ```
adduser charlie
``` or whatever you want to call your account. Follow the prompts - you can leave them all blank except for the password.

Then type ```
adduser charlie admin
```

This will give your new account admin rights.

```
shutdown -r now
```

to reboot, then try to log in as charlie.

---

### Post by charlie1989 on 2009-12-23
OK I got as far as the password, when I type nothing comes on screen, also when I try to "shutdown -r now" the keys seem to change, i.e there is no (-) I tryed every key but cannot find -, though it was there previously

---

### Post by charlie1989 on 2009-12-23
ok ignore that I've managed to create a user, though the screen still goes black after loading the ubuntu logo, any idea? maybe screen resolution or something.

thanks for your help btw :)

---

### Post by annasarp on 2009-12-23
while restarting in the grub stage press escape and press 'e'

scroll using arrow keys till u find " quite splash" string now type "i915.modeset=0" (without quotes) after "quite splash" like this "quite splash i915.modeset=0" after this press ctrl+x
the system will boot.
this should solve if it is a graphic card issue.

---

