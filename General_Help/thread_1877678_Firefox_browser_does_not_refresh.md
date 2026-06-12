---
title: "Firefox browser does not refresh"
date: 2011-11-08
forum: General Help
---

### Post by Randy Schilling on 2011-11-08
Hello -

I'm setting up newly installed U11.10 and working under its Unity desktop.

My Firefox does not seem to refresh webpages regularly.  Do I need to change a setting or add a plug-in?  I can't find a refresh command to do this manually.

Many thanks and regards - Randy

---

### Post by vasa1 on 2011-11-08
From what I understand, the "refresh" part is governed by page code but we can control it by going into Edit, Preferences, Advanced and there we have a "General" tab and under Accessibility we can set the browser to warn if a page attempts a reload or redirect.

Is it possible that you are blocking scripts and hence not seeing a reload?

Oh, and pressing control+R should refresh the page.

---

### Post by critin on 2011-11-08
pressing F5 also refreshes

---

### Post by Randy Schilling on 2011-11-08
I tried logging in as root user with the command,
    sudo passwd root,
started the TexLive installer as before,
        install-tl -gui wizard,
and got the same response.
 
- Randy

---

### Post by Randy Schilling on 2011-11-08
Sorry, ignore previous post.

---

### Post by vasa1 on 2011-11-08
> **critin said:**
> pressing F5 also refreshes

And, IIRC, control+F5 does a reload totally ignoring cache.

---

### Post by Randy Schilling on 2011-11-08
Both Ctrl+R and F5 work, thanks.

vassa1: 
My "warn if a page attempts a reload or redirect" is unchecked.
How can I tell if I'm blocking scripts?  Under the Content tab, I'm blocking
scripts, loading images automatically, and JavaScript is enabled.

---

### Post by vasa1 on 2011-11-08
> **Randy Schilling said:**
> ...  Under the Content tab, I'm blocking
**scripts**, loading images automatically, and JavaScript is enabled.

You mean pop-ups?

Do you have the NoScript extension installed and enabled?

---

### Post by Randy Schilling on 2011-11-09
vasa1:  I've installed the Noscripts extension to Firefox and it's enabled. I find its not easy reading about security.  I don't understand the choices under Noscripts' Preferences. Is the Whitelist the list of trusted websites and do I have to constantly update it? Generally, if I go to a website, I trust it. I don't pirate anything or go to XXX sites.    Under the Content tab, I'm blocking pop-up windows (not scripts(sorry)!) loading images automatically, and JavaScript is enabled.    In your first response to my post you asked:  "Is it possible that you are blocking scripts and hence not seeing a reload?"  and I don't know how to answer this.  If by "scripts" you are referring to "JavaScripts" then they are enabled (checked under the Content tab).    Many thanks vasa1 - Randy

---

### Post by Randy Schilling on 2011-11-09
My apologies vasa1 for the formatting of the last post.  Its tough reading. I tried editing it but no help.  -Randy

---

### Post by Randy Schilling on 2011-11-09
Vasa1: My status bar contains the message "Scripts currently forbidden" and Firefox is not responding the way I expect when I ask it for a new website.

---

### Post by Randy Schilling on 2011-11-09
Hello Vasa1:

I installed the Noscripts extension to Firefox and while it was enabled
Firefox's status bar said something like Scripts currently forbidden.
Things were happening that I did not understand (like that poorly formatted post)
so I DISABLED Noscripts.

As I said before, I find its not easy reading about security. 
I don't have the time right now to do a thorough reading of NoScripts' FAQ so could you please tell me
simply how to set it up.  Here is what I think you might want to know.
Generally, if I go to a website, I trust it. I don't pirate anything or go to XXX sites. 

Is the Whitelist the list of trusted websites and do I have to constantly update it? 



Here is my response to your earlier questions (repeat of what was in my unreadable post)
Under the Content tab, I'm blocking pop-up windows (not scripts(sorry)!) loading images automatically, and JavaScript is enabled. 


In your first response to my post you asked: "Is it possible that you are blocking scripts and hence not seeing a reload?" and I don't know how to answer this. If by "scripts" you are referring to "JavaScripts" then they are enabled (checked under the Content tab). 


My apologies for delayed response.  My job intervened.

Many thanks vasa1 - Randy

---

### Post by Randy Schilling on 2011-11-09
Hello Vasa1:

I installed the Noscripts extension to Firefox and while it was enabled
Firefox's status bar said something like Scripts currently forbidden.
Things were happening that I did not understand (like that poorly formatted post)
so I DISABLED Noscripts.

As I said before, I find its not easy reading about security. 
I don't have the time right now to do a thorough reading of NoScripts' FAQ so could you please tell me
simply how to set it up.  Here is what I think you might want to know.
Generally, if I go to a website, I trust it. I don't pirate anything or go to XXX sites. 

Is the Whitelist the list of trusted websites and do I have to constantly update it? 

Here is my response to your earlier questions (repeat of what was in my unreadable post)
Under the Content tab, I'm blocking pop-up windows (not scripts(sorry)!)  loading images automatically, and JavaScript is enabled. 


In your first response to my post you asked: "Is it possible that you  are blocking scripts and hence not seeing a reload?" and I don't know  how to answer this. If by "scripts" you are referring to "JavaScripts"  then they are enabled (checked under the Content tab). 


My apologies for delayed response.  My job intervened.

Many thanks Vasa1 - Randy
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11440897") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11440897")

---

