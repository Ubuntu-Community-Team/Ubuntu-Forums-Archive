---
title: "Windows-Only Websites"
date: 2009-10-24
forum: General Help
---

### Post by andycastille on 2009-10-24
I have two websites that only work in Windows or Mac and I need to run them in Ubuntu. Like WINE for applications, is there a way to install a program that will make the website think it is in Windows?

Sites:
[www.officelive.com]("http://www.officelive.com") Microsoft Office Live
[www.netflix.com]("http://www.netflix.com")     Netflix Movie Rental (It works for renting but you can't watch the online
                                                           version, which requires Microsoft Silverlight)

Help!

Ubuntu Newbie
----------------------------------------------------------------------------------------------------------
"But where's the charm of Windows?" "I feel like this in Mac too." "It's just a little different."
I have only been using Ubuntu for one month. Could someone show me around?

---

### Post by falconindy on 2009-10-24
I don't know about the first, but Netflix is definitely a no go. It's not so much an issue of Silverlight -- Moonlight replaces it, but it comes down to the DRM. No amount of user-agent switching or hacking on Moonlight will solve it. Blame Netflix. They could have used Adobe's DRM (multi-OS supported) rather than Microshaft's.

---

### Post by 3rdalbum on 2009-10-24
You could try using the User Agent Switcher extension for Firefox:

```
sudo apt-get install useragentswitcher
```

And then change your new Firefox settings so it pretends to be Firefox on Windows. This might work for Office Live but it won't work for Netflix (because it requires Silverlight).

---

### Post by ranch hand on 2009-10-25
+1

---

### Post by andycastille on 2009-10-25
When I typed it into terminal, it installed. I still get the same error message from the Office Live website (shown below). Do I need to configure it or change a setting from the EDIT -> PREFERENCES menu in Firefox? The error message says that Firefox will work, but only in Windows or Mac. What do I do now?

       
                                                                                                                                                                                               	                                         [IMG]http://home.officelive.com/Misc/images/logo.gif[/IMG]                                                                                                                                            
                                        [RIGHT][/RIGHT]                                     
                                                                                           
             
                                               
                  					 					    [B]
To use Microsoft Office Live, your computer must meet one of the following requirements:

[/B]

[LIST]
[*]Microsoft Internet Explorer 6, 7, or 8 running on Microsoft Windows XP, Windows Server 2003, or Windows Vista. You can download Internet Explorer from the [Internet Explorer page]("http://www.microsoft.com/windows/downloads/ie/getitnow.mspx").
[*]Mozilla Firefox running on Windows XP, Windows Server 2003, Windows Vista, or Mac OS X 10.2.x and later. You can download Firefox from the [Firefox download page]("http://www.firefox.com/").
[/LIST]
© 2008 Microsoft Corporation. All rights reserved.

---

### Post by OpenGuard on 2009-10-25
You might want to take a look at [Moonlight]("http://mono-project.com/Moonlight") ( Silverlight port ).

---

