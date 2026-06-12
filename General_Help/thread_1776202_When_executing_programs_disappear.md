---
title: "When executing programs disappear"
date: 2011-06-05
forum: General Help
---

### Post by Lloyd Ewing on 2011-06-05
When you try to run a program and it appears briefly on the bottom line and then goes away without any explanation, is there a way to find out what is wrong?  

In the non-unix systems I have used, there was always a convention that when a program crashed or terminated abnormally, it would try to display some kind of error message or other indication that something was wrong, even if it is just a blue screen.  Are these types of error messages in Ubuntu recorded in a log file so I might have a chance to solve the problem?  If so, where can I go for information on how to find and/or interpret the messages?

There are several programs that do this on my system which runs 10.04 Lucid.  I apologize if I sound frustrated.  I would be grateful for any advice.

Lloyd

---

### Post by Mr. Shannon on 2011-06-05
If you try to run the programs from the terminal they will usually send their error messages to the terminal and you could then read them.

If you don't know how to run an application from the terminal tell us one of the programs you are trying to run and we will tell you how to run that application from the terminal.

---

### Post by Lloyd Ewing on 2011-06-06
Mr.S.,
Thanks for that advice.

I tried typing "rhythmbox" at the command prompt and it did display some cryptic error messages.  I can look for them on the Rhythmbox web site and ask if they know what is going on.

Another thing that does not work is the "Report a problem..." option from the "Application" menu.  I don't know what it is supposed to do but I clicked on it out of curiosity to see what would happen...  Nothing happens.  I went to the "Main Menu" option of the "System" -> "Preferences" menu and was able to find that the command line is:
/usr/share/apport/apport-gtk -c %f
I tried copying that command to the command prompt, and this time a little box is displayed which shows just this message:
"Invalid problem report
No such file of directory"
That is not much help but I see that the command "man apport-gtk" shows a man page, so I guess I would have to read that to find out what it is supposed to do.

It does seem like there should be an easier way to find out these kinds of secrets of Ubuntu without posting questions to a forum.  If it always works this way I should be able to enter my commands from the command line and go from there.  Thanks very much!

Lloyd

---

### Post by JHBrewer on 2011-06-20
*Catch-22*: what if it is the *Terminal* windows that keep disappearing?  My system, newly upgraded to 11.04, started out dropping **all **windows every time it went to sleep; then I switched to Gnome (I absolutely despise Unity) and it got better: now *only *Terminal windows are dropped, and only intermittently....  I suppose I should be grateful that my system is now useable *most* of the time -- sort of like running *Windows*....

---

