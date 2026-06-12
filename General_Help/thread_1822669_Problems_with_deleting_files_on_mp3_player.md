---
title: "Problems with deleting files on mp3 player"
date: 2011-08-10
forum: General Help
---

### Post by CoyoteUK5 on 2011-08-10
Hello 
I have kubuntu 11.04 the file manager is Thunor and the environment is based on Xfce.

I am a complete novice in linux I orginally had linux mint 10 but this was installed by a friend but the updates were not working so I had a disk from a magazine that had various distros of unbuntu , I decided to install the kubuntu as my system is old.
I am glad I did as apart from one or two hiccups my computer is working well.
I am slowly learning but I do realise I have a lot to learn but I loook forward ot it but I would say I am complete newbie to kubuntu and linux.
Now I have a creative stone mp3 player with 2 gb of memory I loaded it as I normally do but when I deleted the files the memory shown still shows it as full.
I like to think about things before asking for help so decided to look at the hidden files and lo and behold they were all there. They were in the .trash files but no matter how I tried it they refused to be deleted as you probably realised..
I had gone to the mirc room for kubuntu and a person there told me to do control h , I assumed jhe meant that would show the hidden files the do control +delete all I got was a dialogue box saying files cannot be moved to waste.
In the end I got out of the cupboard my old windows computer and  reformated and reinstalled the firmware so now I once again got a empty  mp 3 player.
I do not really want to do that again
Please forgive the long peramble but I am trying to give as much detail as possible.
Can anyone tell me a way I do not have to do this .
I am going to ask for a detailed reply as I said I am new to this.
:sad:
I hope someone can help.

---

### Post by flipper T on 2011-08-10
in ubuntu in nautilus there is an option to add "delete" to your right click menu...edit/preferences/behaviour

i assume you have something similar in thunor

do this and you can bypass the waste basket stage of deleting

this should solve your problem

ps shift + delete also works...again in ubuntu

---

### Post by Johnb0y on 2011-08-10
> **flipper T said:**
> in ubuntu in nautilus there is an option to add "delete" to your right click menu...edit/preferences/behaviour

i assume you have something similar in thunor

do this and you can bypass the waste basket stage of deleting

this should solve your problem

ps shift + delete also works...again in ubuntu


sorry for busting in but... loving the signature...lol!

---

### Post by flipper T on 2011-08-10
was torn between that & 

"That gives us exactly... forty minutes to get the f**k out of Dodge. Which, if you do what I say when I say it, should be plenty. Now, you've got a corpse in a car, minus a head, in a garage. Take me to it."

or

"Get it straight buster - I'm not here to say please, I'm here to tell you what to do and if self-preservation is an instinct you possess you'd better f******g do it and do it quick. I'm here to help - if my help's not appreciated then lotsa luck, gentlemen"

:)

---

### Post by Johnb0y on 2011-08-10
> was torn between that & 

"That gives us exactly... forty minutes to get the f**k out of Dodge.  Which, if you do what I say when I say it, should be plenty. Now, you've  got a corpse in a car, minus a head, in a garage. Take me to it."

or

"Get it straight buster - I'm not here to say please, I'm here to tell  you what to do and if self-preservation is an instinct you possess you'd  better f******g do it and do it quick. I'm here to help - if my help's  not appreciated then lotsa luck, gentlemen"

:smile:
 		                   		  		  		 		 			 				__________________
				If I'm curt with you it's because time is a factor. I think fast, I  talk fast and I need you guys to act fast if you wanna get out of this.  So, pretty please... with sugar on top. Clean the f*****g car. 			
 		 		  		  		 		 			 				 				* 					 						Last edited by flipper T; 5 Minutes Ago at 03:28 AM.. 					 					 				* 			
hahaha epic. think we should set up a thread all about quirky signatures...lol!

---

### Post by Avoozl on 2011-08-10
You should've been able to permanently delete the files as root.  You can hit alt-F2 and 
```
gksudo thunar
```
to open the file browser as root.  You should be able to delete stubborn files that way.

---

### Post by flipper T on 2011-08-10
certainly in ubuntu, its not an ownership issue, more the fact that when you try to delete files from .trash on an mp3 player, there is no identified waste basket to put them in

thats my understanding / experience anyway

---

### Post by Avoozl on 2011-08-10
Maybe.  I can actually delete files from my MP3 player though without being root.  I do have to delete them twice (the first time they move to .trash, then I delete .trash and they are permanently gone).

---

### Post by flipper T on 2011-08-10
exactly my point

you delete them, not "move to rubbish bin"

---

### Post by CoyoteUK5 on 2011-08-11
Thanks to everyone.
I just tried it and it shift plus delete works.:)

---

### Post by tredegar on 2011-08-18
In nautilus:
Edit, Preferences, Behaviour and under "Wastebasket" enable "Include a delete command that bypasses the wastebasket".

Now, when you R-click a file, you'll get a proper **Delete** option.

When I want my files to go, I want them **gone**. "Wastebaskets" are for wimps ;)

---

