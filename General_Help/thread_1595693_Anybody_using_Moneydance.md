---
title: "Anybody using Moneydance?"
date: 2010-10-13
forum: General Help
---

### Post by columbus2012 on 2010-10-13
Anybody using Moneydance on 10.04 ? can give me an idiots guide as how to install it.
 I downloaded the self installer with java *moneydance_linux_x86wj.sh*  from their site as they recommended but when I try to install all I get is a Gedit error :- 

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

Should I have downloaded another version

Tia.

---

### Post by rft183 on 2010-10-13
I don't recall actually having to install Moneydance.  It just runs.  However, usually when you have a file that ends in *.sh, to run them you have to go to the terminal.

First, make sure you are in the same directory as your file (cd /*directory/path*).
Then make the program executable:  Type in "chmod +x moneydance_linux_x86wj.sh" without the quotes.
Finally, type in command "sh moneydance_linux_x86wj.sh", without quotes.

That should run the program/script.

---

### Post by rft183 on 2010-10-13
I should add that if the script complains, try typing the command "sudo" before the last command ("sudo sh moneydance_linux_x86wj.sh").  This would make the command run as root.  I don't think Moneydance would require to run as root, but I figured I'd let you know for future reference!

---

### Post by columbus2012 on 2010-10-14
Thanks, the file was supposed to be an executable? but would not :( in the downloads dir so I'd dragged it to the desktop & tried to execute there both by clicking & then within Terminal no luck. I'd assumed that the terminal "desktop" referred to the *desktop* seems it does not.

After stumbling around for a while (I'm sure you've been there when you started with Linux) I just could not get to cd to the downloads or any other directory, kept getting *directory or folder does not exist*. I opened my home folder & dragged the downloaded file there then ran Sudo sh moneydance_linux . .. . . . .  & everything worked & loaded OK this time.

I had checked the manpages for more on the syntax of the cd command but they are not exactly helpful as they refer to syntax which is not detailed there / explained. I am still looking for a beginners explanation of Linux syntax. I'm not exactly stupid! I've been using Dos commands since the 1970's but everything I have read on linux so far assumes some previous knowledge or access to someone to ask which I don't have the luxury of out here.

---

### Post by rft183 on 2010-10-14
Well, it sounds like you got Moneydance working...  I hope the terminal wasn't too unfriendly.  I did some searching for tutorials and I found a link to a free pdf ebook.  It's for an older version of Ubuntu, but the chapter on the command line is still just as relevant today (actually, most of the book is still relevant!).  It is at [http://www.ubuntupocketguide.com/download_main.html]("http://www.ubuntupocketguide.com/download_main.html")

---

### Post by columbus2012 on 2010-10-15
> **rft183 said:**
> Well, it sounds like you got Moneydance working...  I hope the terminal wasn't too unfriendly.  I did some searching for tutorials and I found a link to a free pdf ebook.  It's for an older version of Ubuntu, but the chapter on the command line is still just as relevant today (actually, most of the book is still relevant!).  It is at [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)



Yes thanks had already found that.

Terminal is not unfriendly if you know the syntax, it is just frustrating haveing to try several different ways when you can not find a clear example of what you want to do.

I had one strange thing with Moneydance when it installed OK there was a launch icon under applications / other which I used. However after a re-boot it and the "other" category" vanished from the applications drop down had to reinstall then drag the icon to the desktop. weird !.

I'm slowly finding my way around though :)

---

### Post by rft183 on 2010-10-15
I'm not sure about the icon either.  Weird is right!  One trick I've found with the Gnome Terminal is that you can drag files to it, so if you have a file on the desktop that you need to work with, instead of typing everything in, you can type "sh " or whatever other command you're using, and then drag the file onto the terminal.  It then copies the file path in for you.  Kind of cool...

---

