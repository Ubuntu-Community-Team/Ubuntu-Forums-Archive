---
title: "Unison hangs in Natty"
date: 2011-04-29
forum: General Help
---

### Post by apwiggins on 2011-04-29
Unison-gtk on a new 11.04 machine talking to a 10.10 machine hangs.  It never connects to the rsync over ssh to the destination 10.10 machine.

---

### Post by wgarcia on 2011-04-30
Have you checked if the versions are the same? At least from the command line unison needs the same version in the two computer that ar being connected. Check

unison --version

from a command line.

---

### Post by c42105 on 2011-04-30
Same problem here. Unison was working fine till I upgraded to Natty. It's odd because ssh works fine!

---

### Post by tarator on 2011-04-30
Same here... 
since update to Kubuntu 11.04 unison hangs while "Contacting server..."
starting unison from konsole gives the following error message:

```

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x9fd2100)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-input-feedback-sounds' of type `gboolean' from rc file value "((GString*) 0x9fd2030)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-button-images' of type `gboolean' from rc file value "((GString*) 0x9fd2210)" of type `gboolean'


```Can anybody help?

[EDIT:] the command "**unison -version**" tells me following:
unison version 2.32.52

I'm using the same version on each machine...

How can i enable GTK_DEBUG?

I tried to set GTK_DEBUG to 1 or true, but without difference in the error message....

```

GTK_DEBUG=1
GTK_DEBUG=true

```

---

### Post by c42105 on 2011-04-30
It seems it's a bug:

[https://bugs.launchpad.net/ubuntu/+source/unison/+bug/696706](https://bugs.launchpad.net/ubuntu/+source/unison/+bug/696706)

---

### Post by wgarcia on 2011-04-30
I'm not experiencing this bug, maybe because I'm authenticating through keys.

---

### Post by c42105 on 2011-04-30
You're right! Authenticating through keys solves this problem:

[http://www.pclinuxos.com/forum/index.php?topic=86809.0](http://www.pclinuxos.com/forum/index.php?topic=86809.0)

Thanks!

---

### Post by tarator on 2011-04-30
Thanks, public key authentication also works for me but only without the optional passphrase. 

:P

---

### Post by earlra on 2011-05-10
Thanks!  I had the same problem but the solution above worked for me.  I also rely heavily on Unison so was quite disturbed until I found this thread.

---

### Post by george1984 on 2011-05-13
Thanks for the diagnosis.

Being not very clever, I took the easy path of substituting ssh client/server from the Maverick repository until the patch comes through. Seems to be working ok. 

Interesting how much I depend on Unison.

Cheers.

---

### Post by rwglefering on 2011-05-15
I did google some support web pages. Every time Ubuntu comes with a new os version the client-server software gets out of date.  Be very sure you have got the same version on both the client and server!
I use version 2.40.61 and everything runs without any problems! After installing  natty you have to install the client manually.
By the way  I use SSH.

Good luck!:)

---

### Post by Benchrest on 2011-05-23
I tried another solution.  I understand a newer level of Unison works fine on Natty from a bug post.  I always wanted to install from a tarball.  It was not difficult using the Unison manual for 2.40.63.  After installation I can start unison and don't get the message contacting server but actually connect.  Then I got the message that 2.40.63 on my Natty machine and 2.27.57 on my Lucid machine don't match. So I installed 2.40.63 on my Lucid machine.  Now it fails connecting to the server from my Natty machine. I am guessing that because 2.40.63 is not being recognized as installed on the Lucid machine.  I tried starting Unison on the Lucid  machine so it would be in memory, but it is still not recognized.  I guess this type of install doesn't register the software correctly. So now I will see if I can find how to register new software installed this way.
edit: Linux has a search path of directories it looks through for programs. The directory I had Unison installed in was not in one of the directories in the list. I copied the executable ( as the directions said in the last sentence) to /bin. Seems to be working .I downloaded 2.40.63 from [http://www.seas.upenn.edu/~bcpierce/unison//download/releases/stable/](http://www.seas.upenn.edu/~bcpierce/unison//download/releases/stable/)  also has the manual there with directions. I will try to put together a little more detail and post tomorrow.

---

### Post by j.r.d.silva on 2011-05-23
I installed Unison 2.32.52 on my Debian Squeez, Lucid and Natty.  I could use Unison from Lucid, however in Natty I kept experiencing the same problem.  

Then I remembered that in my Lucid installation I created RSA public key with the default encryption level, that is 2048 bit, but in Natty I created the key with 4096 bit encryption instead.  As soon I regenerated the key using 2048 bit encryption on Natty, the problem has gone.  Now I can use Unity on Natty without any problems.

Looks like unison-gtk does not like 4096 bit encryption.  I hope it helps, folks.

---

### Post by Benchrest on 2011-05-23
Installing the newest stable release of Unison from tarball

Natty has a problem with the shipped version of Unison not working.  Unison hangs with the message “Contacting Server”.  This is a known bug, [https://bugs.launchpad.net/ubuntu/+source/unison/+bug/696706](https://bugs.launchpad.net/ubuntu/+source/unison/+bug/696706)

The bug report indicated the newest version of Unison would work.  From  [http://www.seas.upenn.edu/~bcpierce/unison//download/releases/stable/](http://www.seas.upenn.edu/~bcpierce/unison//download/releases/stable/)    you can find both the manual giving installation instructions and a download of release 2.40.63 of Unison.

This was my first attempt at tar.gz file. 
I downloaded The Unison file unison-2.40.63.tar.gz from the above site. Use the instructions "Building Unison from Scratch".  "Unix"  
I installed the Ocaml package  This gave a total of 20 packages downloaded including requisites.
GTK2 was already installed
I installed 2 packages labled liblablgl-ocal and two packages libablgtk2- . I am not sure if all four are needed but this gave 100 small packages installed including requisites.
I moved  unison-2.40.63.tar.gz to  /usr/local/src I read somewhere to do this. (I'm a novice). In Natty I had access to this folder, but in Lynx I had to change its permissions with chmod.
From a terminal I changed directory to cd /usr/local/src 
entered tar xvf  unison-2.40.63.tar.gz
and it extracted the tar.gz into a folder /usr/local/src/unison-2.40.63
changed directory to /usr/local/src/unison-2.40.63
the following commands gave some errors but they worked just the same:
make configure
make
make opt
sudo make install
make

Looking in the directory  /usr/local/src/unison-2.40.63  you should see an executable named Unison 3.1 MB.  Copy this to /bin . To do this you will need to open a terminal and issue sudo nautilus.  This allows Nautilus to run as root to paste into /bin.

In the classic view, right click applications, Edit menus.  Select Accessories on the left (or where ever you want to install Unison in the menu, New Item on the right. Name the program what you want (Unison) and give directory info where it is. The directory may not be needed with it in /bin You are done.  Need to do this on all machines as Unison checks that all are the same release.

---

