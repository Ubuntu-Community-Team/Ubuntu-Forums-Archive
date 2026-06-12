---
title: "help with firefox 4"
date: 2011-03-27
forum: General Help
---

### Post by anbaary on 2011-03-27
Hi
I downloaded ff 4 tar.bz.2 file ,extaracted to root opened firefox folder and ran from there,but ff 3.6 was still there so i used sudo nautilus to remove the old ver.
Now to run ff i have to open root/firefox and there is a script file i use to run ff,if i type firefox in the terminal i get command not found msg.
Please help.
I am on ubuntu 10.04.

---

### Post by Script Warlock on 2011-03-27
heres the easiest way to install/upgrade to ff4

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by anbaary on 2011-03-28
I dont need to install or upgrade now, i just want to fix the mess i made.

---

### Post by Razorback on 2011-03-28
You could try synaptic and see if you can reinstall the version in the repositories.  Then, use the link above to get 4 installed.  I just upgraded mine to 4 and it worked great.

---

### Post by comicosmos on 2011-03-28
Hello you cannot open firefox in the terminal because the OS do not know where to locate the "script file ".
There's an easy work-around however:
1. at your home directory(that is "/home/[username]", or "~"), make a new dir called "bin"
2. create a soft link of your script file in this folder, rename "firefox"
3. restart your computer
now you can type "firefox" directly in terminal to start firefox.

You can google environment variable PATH to find the principle behind the phenomenon.
I had just found a page FYR: [http://osr600doc.sco.com/en/USE_oview/Setting_your_path.html](http://osr600doc.sco.com/en/USE_oview/Setting_your_path.html)

But this is not recommend. You are encouraged to try to admin your program via Ubuntu software center.

---

### Post by anbaary on 2011-03-28
Thank you comicosmos,done.
Thank you all.

---

