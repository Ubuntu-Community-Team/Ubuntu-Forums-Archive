---
title: "Please help me get away from Windows"
date: 2011-07-15
forum: General Help
---

### Post by OK-WTF on 2011-07-15
Hello,


I own a Windows-based server that serves as a web and mail server for my business website.

I am soon going to build a new dedicated server and looking to put Linux on it, but every time I try to do something productive with Ubuntu, I am being left in the dark, by design.

I have found web server software to use, so thats all sorted.
What I am on the hunt for a mail server software, and this is where the dramas and headaches have hit boiling point.

I installed Postfix via the Synaptic Package manager, then spent several hours digging through, manuals, configuration files and online tutorials.

I've finally got the mail server receiving and sending mail, but I have no idea how to setup user accounts, change user passwords, etc, etc, etc.

Now for the biggest drama: I am going to need something to talk to my mail client Thunderbird, so I installed Dovecote IMAP server.

So it installed, hung for about 5 minutes... then expanding the little box thing only to see it had no hung, and required user input. OK, thanks for failing to auto-expand and waste my time!
SO, I answered the question. Installation completed and closed.
FFS, OK, NOW WHAT? What am I suppose to be running, or even doing?
So.. I get to console "man dovecote"... Yes, its telling me all the commands etc, but where is the configuration file?

No guidance what so ever.

I come from Windows, where you don't have to read a user manual every time you want to do something.

Isn't there any mail suites for Linux with a 21st century graphical user interface? I'm a busy person and don't have time to read 1000 thousand page manuals and play guessing games with configuration files.

Someone please help!
Closed source, open sourced, pay for license, I don't care. I just want something that doesn't require me to read a user manual every time I want to do something!

This might seem like I sound arrogant, but how would you expect someone to be feeling after hours of digging through manuals for something which should be simple.
I don't want a program that holds my hand for everything I do, I am quite advanced in computers, but I shouldn't have to be pulling out a user manual every time I want to do something. I have much better things to do in life!

Thank you.

---

### Post by nothingspecial on 2011-07-15
> **OK-WTF said:**
> 

Now for the biggest drama: I am going to need something to talk to my mail client Thunderbird, so I installed Dovecote IMAP server.


So.. I get to console "man dovecote"... Yes, its telling me all the commands etc, but where is the configuration file?



Hi

The example one is at /usr/local/etc/dovecot-example.conf

You should copy it to /usr/local/etc/dovecot.conf

and edit it to your needs.

Never used it though so I can't offer much more guidance.

Cheers

---

### Post by OK-WTF on 2011-07-15
> **nothingspecial said:**
> 
The example one is at /usr/local/etc/dovecot-example.conf

No its not.
The version in the repository is not the official version, its Canonicals version modified for Ubuntu. It doesn't come with an example configuration file.

---

### Post by OK-WTF on 2011-07-15
Bump.

---

### Post by smurphy_it on 2011-07-15
```
sudo find / -name dovecot
```

---

### Post by snowpine on 2011-07-15
Welcome to the forums OK-WTF (cute user name ;))!

I understand learning Ubuntu can be frustrating if you're new, not sure where to get your information, who to trust, etc. One site tells you to do this, another site tells you to that, and so forth.

May I suggest following the Ubuntu Server Guide step-by-step as your primary how-to guide?

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

(I'm assuming you're using the 10.04 Long Term Support release, if not, please use the Server Guide appropriate to your release.)

---

### Post by linuxuser12345 on 2011-07-15
A Windows-based *server*?? Well that's just stupid. :P

---

### Post by alliance1975 on 2011-07-15
There are rocks that have more knowledge about Ubuntu than I do but consider:
Ubuntu Server + Webmin + Woodel's guide.

His, (Elwood's), guide is at:

[http://woodel.com/](http://woodel.com/)

---

### Post by kevinthecomputerguy on 2011-07-19
I love that guy :- )

---

