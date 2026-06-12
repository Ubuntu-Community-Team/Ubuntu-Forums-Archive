---
title: "Problems installing TrueCrypt."
date: 2010-11-19
forum: General Help
---

### Post by A Traveller on 2010-11-19
Hi all.

I'm using Ubuntu 9.10 Karmic and have downloaded and extracted the following files.

truecrypt-7.0a-setup-x64
truecrypt-6.3a-setup-x64

If I double click on either of them, I get an error message "Could not open the file /home/*****/truecrypt-6.3a-setup-x64. gedit has not been able to detect the character encoding. Please check that you are not trying to open a binary file. Select a character encoding from the menu and try again."

I have also tried choosing the other option from the Character encoding list, which is Western ISO....., however, got the same results.

I also tried pasting the following into the Terminal, but got a "command not found" error.

sudo ./truecrypt-6.3-setup-ubuntu-x86

Same problem with sudo ./truecrypt-7.0-setup-ubuntu-x86

I also found the following when searching the forums for an answer. Would anything here be of any help?

[http://www.apt-get.org/search/?query=truecrypt&submit=Search](http://www.apt-get.org/search/?query=truecrypt&submit=Search)

Does anyone know of anything else I could try?

Thanks.

---

### Post by dino99 on 2010-11-19
directly use package from synaptic

---

### Post by Big Ed on 2010-11-19
I just tried installing Truecrypt and didn't run into any problems on Ubuntu 10.10.  You don't want to open the file from within Nautilus.  That will try to open it with an application; in your case it's gedit, which is a text editor.  So in the terminal window, cd to the directory you have the unpacked file saved and run:

$ ./truecrypt-7.0a-setup-x64

Just type ./t and press Tab.  That will complete the command for you (if only one file starts with t).  That eliminates spelling errors.  It will ask for your password during the install process.  

Hope this helps,
Ed

---

### Post by Dave_L on 2010-11-19
dino99: Is truecrypt in a repository? I didn't see it.

A Traveller: Did you make the file executable?

I installed Truecrypt on Ubuntu 10.04 like this:

$ cd (to directory containing the file truecrypt-7.0a-setup-x86)
$ sudo sh ./truecrypt-7.0a-setup-x86

---

### Post by Soul-Sing on 2010-11-19
> **Dave_L said:**
> dino99: Is truecrypt in a repository? I didn't see it.

A Traveller: Did you make the file executable?

I installed Truecrypt on Ubuntu 10.04 like this:

$ cd (to directory containing the file truecrypt-7.0a-setup-x86)
$ sudo sh ./truecrypt-7.0a-setup-x86

Afaik truecrypt isn't in the [COLOR="Red"]off.[/COLOR] Ubuntu repository's. (And I don't see it happen in the near future)

---

### Post by A Traveller on 2010-11-19
Thanks for all the helpful replies.

I had already checked Synaptic but couldn't find it there.

I still am not very familiar with Terminal terminology, but managed to find out how to do as you all advised, so this is what I did.

Place the truecrypt-7.0a-setup-x64 file on the Desktop
Open the Terminal
Type cd ~/Desktop and press Enter
Type ./truecrypt-7.0a-setup-x64

It brought up an 'xmessage' window which allowed me to 'install' the program, however, when I click the TrueCrypt icon which has appeared under the Applications, Accessories menu, it appears on the taskbar at the bottom of the screen, however, nothing else happens.

I read somewhere that this program came with a GUI already built in? Am I missing something?

Thanks.

No, I did not make the file executable (whatever that means, haha).

---

### Post by A Traveller on 2010-11-19
UPDATE!

Sorry, I've just figured out what the problem was. I have two monitors, one of which is usually turned off and the TrueCrypt program appeared on the second monitor instead of my main one. So, found it! Now I'll be back when I can't figure out how to use the thing! Haha.

Thanks for all the help. I really appreciate it all!

---

### Post by Splatus on 2011-01-21
> **Dave_L said:**
> dino99: Is truecrypt in a repository? I didn't see it.

A Traveller: Did you make the file executable?

I installed Truecrypt on Ubuntu 10.04 like this:

$ cd (to directory containing the file truecrypt-7.0a-setup-x86)
$ sudo sh ./truecrypt-7.0a-setup-x86


Worked 100%.  Thank you.  :D

---

