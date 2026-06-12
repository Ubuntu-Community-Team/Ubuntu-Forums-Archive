---
title: "I need help setting up start up programs."
date: 2010-08-05
forum: General Help
---

### Post by veilx on 2010-08-05
I'm not excacly a n00b with ubuntu, but I'm not very tech savvy with it.

I used [this guide](https://help.ubuntu.com/community/AddingProgramToSessionStartup), but I don't know any of the commends to start up the programs I wan't. I checked the default startup services and they seems to be very complicated and scattered everywhere (I.E. Not in a certain spot, but starting up from other random areas on my hard drive)

So, what I need is to start up these programs.

- xchat

- Skype

- Empathy


Any help would be greatly appreciated. Thanks :D - veilx.

---

### Post by veilx on 2010-08-05
C'mon, guys. This thread is in the second page with no responses. This happens every time I post a thread in this forum. Please, any help?

---

### Post by ajgreeny on 2010-08-05
Hey there, wait a second or two, please!

23 minutes and no answer is not too bad.  Don't forget we don't do this for anything other than the enjoyment of helping other users sort out problems, but we're not sitting here waiting for your questions.

OK, rant over!

Empathy and Skype should both be in your Applications->Internet menu, and I suspect xchat will be as well, but I don't use it so am not certain.

If they are not in the menu, for whatever reason, you can use the commands, **empathy**, **skype**, and I suspect **xchat** to start them from Alt+F2 run dialog.   However, using those command also works in the terminal and can be very useful if one of your programs will not start, as it will give an error message which may help sorting out the reasons.

---

### Post by veilx on 2010-08-05
> **ajgreeny said:**
> Hey there, wait a second or two, please!

23 minutes and no answer is not too bad.  Don't forget we don't do this for anything other than the enjoyment of helping other users sort out problems, but we're not sitting here waiting for your questions.

OK, rant over!

Empathy and Skype should both be in your Applications->Internet menu, and I suspect xchat will be as well, but I don't use it so am not certain.

If they are not in the menu, for whatever reason, you can use the commands, **empathy**, **skype**, and I suspect **xchat** to start them from Alt+F2 run dialog.   However, using those command also works in the terminal and can be very useful if one of your programs will not start, as it will give an error message which may help sorting out the reasons.

I was expecting the "30 minute" talk. :( It's just that I'm positive that no one was going to get to the topic if it was further than the 1st page. :/

Also, thanks! I didn't know that the commands were that simple, I though you had to actually locate the program file within the installation directory. I'll try now. Once again, thanks :)

---

### Post by sydbat on 2010-08-05
> **ajgreeny said:**
> Empathy and Skype should both be in your Applications->Internet menu, and I suspect xchat will be as well, but I don't use it so am not certain.

If they are not in the menu, for whatever reason, you can use the commands, **empathy**, **skype**, and I suspect **xchat** to start them from Alt+F2 run dialog.   However, using those command also works in the terminal and can be very useful if one of your programs will not start, as it will give an error message which may help sorting out the reasons.Alternately, if they do not show up right away in your Applications menu, you can right click on the menu title (Applications, that is) and it will give you a drop down that has "Edit Menus". Click this and it opens a window that allows you to choose what applications to have visible (if they are in the menu in the first place).

---

### Post by Rubi1200 on 2010-08-05
You could also write a bash script to run these programs at system startup (which I gather is what you want to do right?).
 
If you search the forum for keywords like bash script, startup, programs etc you will likely find something.

---

### Post by veilx on 2010-08-05
> **ajgreeny said:**
> Hey there, wait a second or two, please!

23 minutes and no answer is not too bad.  Don't forget we don't do this for anything other than the enjoyment of helping other users sort out problems, but we're not sitting here waiting for your questions.

OK, rant over!

Empathy and Skype should both be in your Applications->Internet menu, and I suspect xchat will be as well, but I don't use it so am not certain.

If they are not in the menu, for whatever reason, you can use the commands, **empathy**, **skype**, and I suspect **xchat** to start them from Alt+F2 run dialog.   However, using those command also works in the terminal and can be very useful if one of your programs will not start, as it will give an error message which may help sorting out the reasons.

Simple as it is, this actually worked! Thank you so much, I was making this way more harder that it really is... once again, sorry for bumping the thread so early. Thank you! :D - veilx

---

### Post by ajgreeny on 2010-08-05
No problem!  I'm happy you got the answer you needed.

If you want things to start at boot time just add those commands to the list at **System ->Preferences ->Startup Applications**

---

