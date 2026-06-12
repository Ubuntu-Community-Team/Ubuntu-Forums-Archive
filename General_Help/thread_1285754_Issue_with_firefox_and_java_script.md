---
title: "Issue with firefox and java script"
date: 2009-10-08
forum: General Help
---

### Post by grey fox on 2009-10-08
Hello

I have Eee PC 901 with Ubuntu netbook remix installed and I have Kubuntu on it, also I installed compiz.

From when I installed the flashplayer and java I get this error whenever opening firefox browser or click buttons on forums. ( screenshot in attachement) I dont receive this in Konqueror. 

I reinstalled second ago java to 6 using Sample Manager.

I am new to this system and community.

Please assist me because it really is annoying

I was trying to find this issue here from others but couldnt.  

Regards,
Grey Fox

---

### Post by grey fox on 2009-10-12
I went to edit the address provided in the error message: [COLOR=Green]
chrome://global/content/bindings/toolbar.xml[/COLOR]

I found out that between lines

255 and 262

there is a piece of script which is:
[COLOR=Red]
[/COLOR]   	 	 	 	 	 	  [COLOR=Red]<body>[/COLOR]
 [COLOR=Red]
[/COLOR] 
 [COLOR=Red]            if (!this._active)[/COLOR]
 [COLOR=Red]                return;[/COLOR]
 [COLOR=Red]            var newText = itemText ? itemText : this._originalStatusText;[/COLOR]
 [COLOR=Red]            if (newText != this._statusbar.label)[/COLOR]
              
 [COLOR=Red]                this._statusbar.label = newText;[/COLOR]
[COLOR=Red]</body>[/COLOR]
  

According to the openoffice lines the 259 line is one of those ( the indicator is between these two) :
[COLOR=Red]
[/COLOR]   	 	 	 	 	 	  [COLOR=Red]   var newText = itemText ? itemText : this._originalStatusText;[/COLOR]
 [COLOR=Red]            if (newText != this._statusbar.label)[/COLOR]




Please help with this!!


I am a total noob in scripts and I have no idea what is wrong in this !

The damn error is still appearing

---

