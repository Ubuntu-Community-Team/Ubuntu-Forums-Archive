---
title: "Thunderbird links to websites are inactive"
date: 2006-05-25
forum: General Help
---

### Post by bturrie on 2006-05-25
I have two machines running Kubuntu. I'm using Firefox as my browser and Thunderbird for email in both. The problem I'm having is that when I click on weblinks in an email Firefox is supposed to open and display the website. Instead nothing happens. I've checked through my Thunderbird configuration and nothing appears incorrect. Any suggestions?

---

### Post by Scubes13 on 2006-05-25
I can verify this behaviour on my current kubuntu breezy install. I am using the latest of both Firefox and Thunderbird.

When I click on a link in Thunderbird, nothing happens either.

Kevin L.

---

### Post by treris on 2006-05-26
Have you checked the file associations?? If I remember correctly this was something I had to set up properly as well when I first installed breezy

The problem is that for doing that you can't go through System Settings, because there's just no entry for that, instead you'll have to go into the 'normal' kde control center. To do that just open a terminal and type *kcontrol* then go to *KDE Components* and then of course *file associations*.

now you can search for *html* and make sure that firefox is listed as the top entry in the applications preference order

I don't know whether this will fix it, but that's how I've got it set up and it seems to be working here

I do know that there is a large amount of info about this issue on the mozillazine forums as well, if this doesn't help maybe you can take a look over there

---

### Post by bturrie on 2006-05-26
When I say your post I was sure that was it, unfortunately that didn't fix the problem. But thanks, I'll try mozillazine.

---

### Post by shane2peru on 2006-05-26
I don't know much about KDE, however I had the same problem in Gnome!  I was looking for the answer.  I didn't find it here, but I did accidently stumble upon it.  In Gnome you can go to System - Preferences - Prefered Applications - My first tab shows web and Firefox was written in the custom command.  I unchecked this box and selected the actual drop down box that contained Firefox as an option.  I'm sure that KDE has a very similar feature, I just can't remember how to get to it.  The custom command for mine was, ```
 firefox %s 
```  I don't know why this wouldn't have worked, but when I choose the other option from the drop down box it worked right away.  Good luck.  - I'm sure the problem has to do with the Firefox/Thunderbird 1.5 upgrade.  

Shane

---

### Post by [S|G] on 2006-05-27
Hello, you could try this: in firefox type 'about:config' in the address bar. Then right-click on a blank space and choose "new -> string". On the dialog box type:
```

network.protocol-handler.app.mailto

```

Then on the second dialog type the full path of your thunderbird (mine is /opt/thunderbird/thunderbird but it's not default; on a terminal type whereis thunderbird and you should see its location).

Try clicking on a mailto: link then :)

---

### Post by bturrie on 2006-05-28
Some of these other things might work but I found something that fixed my problem on Mozillazine. Here it is:
Create a text file called user.js containing the following 4 lines:

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox"); 
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox"); 
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox"); 

Then save into your Thunderbird profile folder. The right folder will already have a file called prefs.js

---

