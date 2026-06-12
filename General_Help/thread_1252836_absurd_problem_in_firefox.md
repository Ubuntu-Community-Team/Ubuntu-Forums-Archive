---
title: "absurd problem in firefox"
date: 2009-08-29
forum: General Help
---

### Post by saahil10 on 2009-08-29
So on my jaunty install, I had no problems for 3 weeks. Then yesterday in firefox i did a google search for some ciphertext. After that I am getting all types of out of range ascii characters displaying on the screen for certain websites. 
 
 So if I visit google.com all I see is a page full of unreadable ascii characters, I tried changing the encodings manually on firefox to western from utf-8 and it changes the characters but it is still gibberish. (Attached screenshots)
 
 The same thing happens at espn.com and other web pages. But on some webpages it is completely fine (everything is printed as it should be). I have tried uninstalling firefox and reinstalling it. Changed the language settings,etc. To no avail. 
 
 Using Konqueror everything is fine, I downloaded opera and everything is fine there too. 
 
 But I like firefox and definitely don't want to abandon it because of this issue.
 
 my phpmyadmin also has these same issues. But if I visit tennis.com it works fine (attached screenshot)
 
 Please let me know if you need any more info to help me out.
 
 Thanks

---

### Post by gettinoriginal on 2009-08-29
Which western did you change it to, ISO or (windows).  Mine is set to ISO without problems.  I don't really understand how it changed just by doing a google search except that maybe firefox had to change your encoding to read the cyphertext pages :confused:  Have you checked the encoding on different pages, ie pages in ASCII and the "tennis" page to see if Firefox is reading them differently ??

---

### Post by jerrrys on 2009-08-29
a basic thing to do would be disable all add-ons and see what happens...

---

### Post by saahil10 on 2009-08-29
> **gettinoriginal said:**
> Which western did you change it to, ISO or (windows).  Mine is set to ISO without problems.  I don't really understand how it changed just by doing a google search except that maybe firefox had to change your encoding to read the cyphertext pages :confused:  Have you checked the encoding on different pages, ie pages in ASCII and the "tennis" page to see if Firefox is reading them differently ??

I changed it to ISO as well. It really makes no sense. I searched in google and maybe my query had some type of control characters but it is really strange. I dont' think its a character encoding problem because no matter which encoding i change it to it is still gibberish. 

And some pages work fine while others are don't work.

---

### Post by saahil10 on 2009-08-29
> **jerrrys said:**
> a basic thing to do would be disable all add-ons and see what happens...

did that. no avail. google and yahoo are all screwed up but I go to bing.com and its fine. :confused:

---

### Post by lovinglinux on 2009-08-29
Create a new profile and check if it works. If yes, then export/import passwords,cookies, extensions, preferences and so on, from the old profile to the new one..

For more info visit [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by saahil10 on 2009-08-29
that works thanks... still mystified on how it happened.

---

