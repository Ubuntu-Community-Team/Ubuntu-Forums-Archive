---
title: "Problems with Tweak and login screen background"
date: 2011-05-23
forum: General Help
---

### Post by SwingKid on 2011-05-23
I have been trying to make it so I will have the same login screen background as I have on my desktop since it looks better. But it doesn't seem to work. In tweak it looks like I have changed the login screen background but when I restart the changes I've made do not seem to have been saved. What can I do to fix the login screen background? Thank you.

---

### Post by freds3251 on 2011-05-23
PM me and I can give you a tutorial that will get you ur background for login without using any software.

---

### Post by freds3251 on 2011-05-23
> **SwingKid said:**
> I have been trying to make it so I will have the same login screen background as I have on my desktop since it looks better. But it doesn't seem to work. In tweak it looks like I have changed the login screen background but when I restart the changes I've made do not seem to have been saved. What can I do to fix the login screen background? Thank you.

Send me an email...It wont let me send the tutorial through private message. =(  my email is [email]fricks@caraudio.com[/email]

---

### Post by freds3251 on 2011-05-23
actually I could just send it this way. lol 


Changing Login Screen Ubuntu 10.10

	To get started I needed to use one program to help achieve a new login background. This program is called GIMP Image Editor. Not sure if it comes pre-installed, if not get it at Ubuntu Software Center. I had to use this program to change the extension of the image from .JPG to .PNG. 

	Now you may not need this program if the image you want to use is already a .PNG image. One thing that I made sure of with the image I selected was that it consisted of my screen resolution. I don't know if this is important, but I found a picture of that size anyway. So here is the steps to find the Standard login screen picture. 

	Step one bring up Terminal and run in Nautilus. You have to do this in order to have permission to change images and what not. Next, Navigate through file system. Should be this exact pattern: File System- USR- Share-Backgrounds. Once you are at this folder you will see the login picture called warty-final-ubuntu.png. You will want to either write down this images name or copy and paste method. Go back and grab your new picture and rename it to this. Your new image must be .PNG extension in order for this to work. So you either use the image editor previously listed or you may have a picture which is already .PNG. If you need to change extension simply bring up image editor with your new picture and save as. There you can have the chance to change the file extension. 

	Now that you have your new image named and what not, you can place this image in the backgrounds folder. One thing to keep in mind is to delete stock login picture from backgrounds folder. After that simply just exit all folders and log out. Once to login screen your new image will appear. 

	I HOPE THIS TUTORIAL WORKS  FOR EVERYONE USING 10.10!! 



Reminder!! If you still cannot get new picture, please feel free to email me and I can help you through it.  My email is [email]fricks@caraudio.com[/email]

---

### Post by SwingKid on 2011-05-23
Whoa..I had about 5 mails from you now :D everything went through I guess. You spammed me good. So anyways, I followed the tutorial but ran in to some minor problem. Looks like I don't have the authority on my own computer to change anything in "usr/share/backgrounds". 
I have done everything correct but when I want to replace the old file with my new one I only get an error message saying:

Error moving file: Permission denied

---

### Post by freds3251 on 2011-05-23
Did you make sure you were running as root? You got to run as root in order to change anything in that backgrounds folder. By the way sorry about that. It kept showing that I had sent nothing. lol

---

### Post by SwingKid on 2011-05-23
> **freds3251 said:**
> Did you make sure you were running as root? You got to run as root in order to change anything in that backgrounds folder. By the way sorry about that. It kept showing that I had sent nothing. lol

How do I change it so I run as root?

---

### Post by freds3251 on 2011-05-23
Bring up terminal window and type in "sudo nautilus" minus the quotations...lol Then a window will come up where you can navigate to the backgrounds file. just make sure you don't exit out of terminal and its windows. This is the way you are getting permission to change things in that folder.

---

### Post by SwingKid on 2011-05-23
> **freds3251 said:**
> Bring up terminal window and type in "sudo nautilus" minus the quotations...lol Then a window will come up where you can navigate to the backgrounds file. just make sure you don't exit out of terminal and its windows. This is the way you are getting permission to change things in that folder.


This solved it! Thank you so much! :) Now it looks pure awesome. :guitar:

---

### Post by freds3251 on 2011-05-23
Excellent!!! Yeah I used to run Ubuntu 9.10 and did just about the same thing of that tutorial,but image was in a different folder. When I upgraded to 10.10 I just did some searching and found the new folder. I have seen people asking about login screen and using Tweak. I prefer to do things without downloading programs if I can.

---

