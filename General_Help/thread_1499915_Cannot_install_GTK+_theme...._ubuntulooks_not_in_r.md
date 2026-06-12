---
title: "Cannot install GTK+ theme.... ubuntulooks not in repo's"
date: 2010-06-02
forum: General Help
---

### Post by jac0117 on 2010-06-02
**** This is in Ubuntu Lucid ****

I have been trying to install this theme I like, but I keep getting the following error:

This theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed.

When I look in Synaptic for ubuntulooks I get gtk2-engines-murrine and murrine-themes are results only.

How can I get the GTK theme installed?

---

### Post by dino99 on 2010-06-02
[http://gnome-look.org/content/show.php/New+Wave+Lucid+theme?content=121184](http://gnome-look.org/content/show.php/New+Wave+Lucid+theme?content=121184)

sudo add-apt-repository ppa:bisigi && sudo apt-get update

---

### Post by mr.scissorkick on 2010-06-23
Sorry to drag this thread back out, but It addresses my concern, so I'm gonna trust my inner forum-ethics-voice and not start a duplicate.

I tried dino99's solution, but had no apparent success.  Was that supposed to add the ubuntulooks engine to the package manager? If so, mine didn't want to play nice.  All I can see that might have caused problems is an error message in my terminal, after the update, which reads > W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE


---

### Post by nilarimogard on 2010-06-23
The Ubuntulooks GTK engine is now a part of the gtk2-engines package so install it with:

```
sudo apt-get install gtk2-engines
```
@mr.scissorkick: Regarding the 

```
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 6E871C4A881574DE                      
```error...  that's a GPG key error, it just means you didn't import the key for a PPA, it doesn't break anything whatsoever. You can fix it with:

```
sudo apt-key adv --recv-keys --keyserver [pool.sks-keyservers.net]("http://pool.sks-keyservers.net/") 6E871C4A881574DE
```Then run:
```
sudo apt-get update
```

---

### Post by mr.scissorkick on 2010-06-23
Okay, you made quick work of that GPG error, but I still didn't get the ubuntulooks engine in the package manager. :confused:

---

### Post by nilarimogard on 2010-06-24
Read again, it's been merged into gtk2-engines

---

### Post by mr.scissorkick on 2010-06-24
Is it supposed to be available in the Synaptic Package Manager?

---

### Post by mr.scissorkick on 2010-06-24
Apparently, I have the gtk2-engines package:

 [IMG]http://i836.photobucket.com/albums/zz288/ubuntuscreenshots/Screenshot.jpg[/IMG]

But... I still have my original problem:

[IMG]http://i836.photobucket.com/albums/zz288/ubuntuscreenshots/scrshot.png[/IMG]

---

### Post by mr.scissorkick on 2010-06-28
*bump*
Still scratching my head.  I haven't found a solution anywhere else in the forums.  Should I just submerge my laptop in water?

---

### Post by mr.scissorkick on 2010-06-29
Maybe throw it in the microwave on high for 1:45?

---

### Post by mr.scissorkick on 2010-07-01
Maybe I could take my motherboard out and hold in in my hands while I shuffle around in circles on a trampoline in my socks...

---

### Post by flipNasty on 2010-07-17
I, too, am having this problem... same deal... tried installing gtk-engines with apt-get, but it was already the newest version. tried installing gtk-engines-ubuntulooks, but that directed me to human-theme, which I *did* sucessfully download and install, but that hasn't solved anything. I'm getting the same error message as in the screenshot above, and it's driving me nuts.

I'm gonna try and figure out how to install it from source, but in the meantime, this is annoying.

---

### Post by lepadatu.lucian on 2010-07-18
i have the same problem with a theme. no solution yet...

---

### Post by theozzlives on 2010-07-18
gnome-looks is a website, you can get stuff like ubuntulooks, clearlooks, etc. there. Some engines are in Synaptic.

---

### Post by lepadatu.lucian on 2010-07-18
found a solution. it worked on lucid lynx :) **[http://gnome-look.org/content/show.php?content=43255](http://gnome-look.org/content/show.php?content=43255)**

P.S. theozzlives, the problem was more complicated than that and you didn't bother to read all the replies

---

### Post by chuckh1958 on 2010-11-03
I'm having the same issue. Tried to install a theme from gnome-looks and it says it won't display properly because the required gtk+ theme engine "ubuntulooks" is not installed. I already have gtk2-engines installed.

---

### Post by Loan_Refi on 2010-11-04
lepadatu.lucian, it worked for me too!

Here is the readme.txt file;

====================
Ubuntulooks Engine
Packaged by Viper550
====================

======
Includes
======
- Ubuntulooks GTK2 Engine and Theme


=============================
Ubuntulooks Engine Installation Instructions
=============================
Step 1.
Copy libubuntulooks.so and libubuntulooks.la to /usr/lib/gtk-2.0/2.*.*/engines as root (substitute "2.*.*" with your version number)

Step 2.
Copy the Human folder to /usr/share/themes/ as root (or to ~/.themes , but it will only be on your account)

Step 3.
Go into your Gnome Theme Prefrences and select Human (or any other Ubuntulooks enabled GTK theme, Human is just included as an example) as your theme under Controls and Window Border. The metacity theme used on Human is a modified version of ClearLooks 2.0 if you wonder, but any other will do too!


===============
System Requirements
===============
Simple:
Requires a GTK version with support for Cairo rendering, or if you can do ClearLooks 2/CVS or other Cairo engines like Murrine, you can use this theme.

---

### Post by valhollen on 2010-12-06
I have been having this same problem. When i try to install SlicknesS black, i get this response at the terminal/ chmod: cannot access `/usr/share/themes/SlicknesS-black/Sluckness-black.jpg': No such file or directory
i extracted the files into Desktop. Anyone have any suggestions on what i am doing wrong?

---

### Post by MrGreen on 2010-12-07
You need to read install instructions again, you have to change permission on that file for it too work.

---

### Post by MrGreen on 2010-12-07
Go

[http://gnome-look.org/content/show.php?content=43255](http://gnome-look.org/content/show.php?content=43255)

Download...

Extract 

Open Readme.txt

Follow and enjoy

MrG

---

### Post by giantpune on 2010-12-31
i had the same issue...  tried using the SlicknessBlack theme in ubuntu 10.04.4 x86_64, same error as in the first post, missing images in some programs... yada yada.

i had already installed "gtk-engines" from synaptic and it didnt fix the error.  heres how i fixed it...
copy the contents of /user/local/lib/gtk-2.0/2.10.0/engines to /user/lib/gtk-2.0/2.10.0/engines.

everything is working as expected now...  no more errors when starting programs and no more missing images in some programs.

---

