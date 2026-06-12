---
title: "How do I compile GPASS manually?"
date: 2012-04-28
forum: General Help
---

### Post by WinRiddance on 2012-04-28
I'm sorry, I don't mean to step on any toes here, but compared to Gpass the replacement app. Revelation simply stinks. There's no doubt in my mind that many people would agree with me on this, especially anyone who's ever *REALLY* used Gpass for all that it had to offer. Sometimes a program doesn't need to be maintained, _if it's already attained perfection for what it is!_

**Case in Point:** Not only did Gpass provide "standard" password efficiency, but with Gpass I could manage my 2 eBay accounts along with my Paypal account _on the same page._ Page you say? That's right, because Gpass permitted multiple lines of text that could be separated by one or more lines for neatness & efficiency. Another example, I have 4 sites where I go Online shopping on a regular basis, same user and same password, consequently they're all on one page too. Or how about this, with my virtual server I keep all of the SQL user and password accounts on the same page. And so on, and so forth ...
I have more examples, that's why I'm certain that I'm not the only one one who used Gpass like that.

When I import my Gpass password file into Revelation, _those previous examples turn into huge wads of garbage text_ with no lines at all. To me, Revelation is an abomination, a fast "hurry up job" that could never stack up to Gpass, yet it's in the repositories **just because it's maintained** ??? What kind of logic is that? Replacing a great product with an inefficient one? That's the Ubuntu way? There was no reason to maintain Gpass any longer because it's evolved as far as it needed to go, and it meets *LINUX* criteria for being working software. Isn't that what Ubuntu is, LINUX ??? So here's the question (sorry about the rant, been depending on Gpass for the past 4 years).

_Instructions and breakdown of files_ are located at the author's website, but after using Windoze for 18 years this doesn't help me. I need someone to walk me through it step by step on an Ubuntu/Xubuntu 12.04 setup.
[http://projects.netlab.jp/gpass/en/about.html](http://projects.netlab.jp/gpass/en/about.html)

**How do I compile the .deb file for Gpass manually?** I should be able to force this Linux application to work, along with creating my own custom launcher for it. With Ubuntu 11.10 it was possible to force the installation of the .deb file. With Ubuntu 12.04 that's been taken away from us as well. So please, can someone please clue me in as to how I can manually compile Gpass on my system? To me, as I'm sure to others as well, this is an indispensable little program that I'd like to use indefinitely. Thank you so much for your help ...

.

---

### Post by WinRiddance on 2012-04-28
Okay, I tried a manual installation via terminal which didn't work .... It appears to install, folders and gui icon are created, when I click the gpass symbol in accessories I'm prompted to enter a master password, but then nothing happens after that ...

```
sudo dpkg -i --force-all gpass_0.5.0-2_amd64.deb
(Reading database ... 230482 files and directories currently installed.)
Preparing to replace gpass 0.5.0-2 (using gpass_0.5.0-2_amd64.deb) ...
Unpacking replacement gpass ...
Setting up gpass (0.5.0-2) ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for gconf2 ...
winriddance@winriddance:~/Desktop$ 

```.

---

### Post by dino99 on 2012-04-28
GPass is a password manager for the GNOME2 desktop.

but now gnome3 is used.  ):P

[http://linux.softpedia.com/get/Security/GPass-3639.shtml](http://linux.softpedia.com/get/Security/GPass-3639.shtml)

---

### Post by Cheesemill on 2012-04-28
You could try installing the .deb files from natty.

Files are at the bottom of the page:
[http://packages.ubuntu.com/natty/gpass](http://packages.ubuntu.com/natty/gpass)

---

### Post by WinRiddance on 2012-04-28
Thank you. I already have the 32 bit and 64 bit packages, and I found a page very similar to the natty page on the Debian site. But I can't find step by step understandable installation instructions that make sense for someone who used Windoze for 18 years. What are you proposing that I do?

**@dino99**

It shouldn't matter that gpass was designed for Gnome2 since I'm using Xubuntu which does not use Gnome3 at all, just FXCE. I was able to install my third party Komodo IDE without a problem too and you won't find that in the repositories either. I believe that Canonical "has done something" (for lack of better explanation) to keep Gpass from working since it's not being maintained nor provided any more. This is Linux though, so regardless if Gnome2 or Gnome3, it should be possible to make Gpass work again ... if only I had some help with this. Thank you.

.

---

### Post by Cheesemill on 2012-04-28
Run gpass from a terminal. What error messages does it give you (if any).

---

### Post by WinRiddance on 2012-04-28
Hah, I already tried that too ... but didn't pay attention to the terminal since the gpass login window popped right up on the screen.
Silly me, 'cuz otherwise I would have noticed this error ... :oops:

```
(gpass:20234): libglade-WARNING **: Could not load support for `bonobo': libbonobo.so: cannot open shared object file: No such file or directory

```.

---

### Post by Cheesemill on 2012-04-28
I'm guessing you need some of these then :)

[http://packages.ubuntu.com/search?keywords=bonobo&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=bonobo&searchon=names&suite=precise&section=all)

I think that
```
sudo apt-get install libbonoboui2-0
```
should do it.

---

### Post by WinRiddance on 2012-04-28
Thanks, but hmmmmm ... there has to be more to it than that. :confused:
Trying the apt-get install generated this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libbonoboui2-0 is already the newest version.
libbonoboui2-0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```[COLOR=DarkRed]**EDIT: **[/COLOR] Just tried installing every libbonoboui2-0 dependency but they were all there already. Every terminal message the same ... Already newest version, 0 upgraded, 0 installed. I guess there has to be something else that's missing. Bummer, I'd hate to have to go through every involved package with its dependencies ... ugh !!!

.

---

### Post by houbolovec on 2012-06-08
hallo WinRiddance,
did you resolve problem gpass with 12.04? i have the same problem...
is there any possibilities convert password file to another program ?  gpass is very nice :-( program.
thanks

---

