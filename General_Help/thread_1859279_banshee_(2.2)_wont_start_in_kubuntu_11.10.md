---
title: "banshee (2.2) wont start in kubuntu 11.10"
date: 2011-10-13
forum: General Help
---

### Post by labatts on 2011-10-13
I get the following message in the terminal:

Gtk-Message: Failed to load module "canberra-gtk-module"
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 545 error_code 10 request_code 155 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Running the --sync command produced the same error message.  Any help is appreciated.

---

### Post by D0nJ0seph on 2011-10-25
I have the exact same problem. Does anybody knows how to fix it or  any other program that re-organize folders and rename files like banshee does? That's the only reason i want banshee running in kubuntu.

---

### Post by oldtimer7777 on 2011-10-25
> **D0nJ0seph said:**
> I have the exact same problem. Does anybody knows how to fix it or  any other program that re-organize folders and rename files like banshee does? That's the only reason i want banshee running in kubuntu.

Yes, I have the same issue in 11.10..  Wasn't like that in 11.04 though. Banshee is hanging after running it in Ubuntu 11.10 lately. Have you installed the Banshee PPA yet to see if it has any team upgrades?


sudo add-apt-repository ppa:banshee-team/ppa 
sudo apt-get update 
sudo apt-get install banshee banshee-extension-ubuntuonemusicstore banshee-extension-appindicator banshee-extension-lyrics banshee-extension-mirage

---

### Post by labatts on 2011-10-25
Funny we liked it for different reasons.  I simply wanted the ubuntuone music store, but decided that it wasn't worth it.  I moved to clementine and love it (minus the absence of the music store).  

I am still interested in a resolution, i guess.  mostly, though, I just want a dedicated ubuntuone music store for kde (add me to the wishlist for that one, eh?)

---

### Post by MatteoR on 2011-10-26
Hi there ):P.

I come from the italian ubuntu-it forum (sorry for my bad english, but I want to help you)

I found a workaround to run Banshee in Kubuntu. :D

You have to go into System settings > Application appearance > GTK+ Appearance and in "object style" select the "Raleigh" option. Then you click ok button. 
Enjoy :p

---

### Post by labatts on 2011-10-26
MatteoR,

No need to apologize.  Thank you very much!!

---

### Post by MatteoR on 2011-10-27
Thanks.
It's a KDE's function bug. This function (theoretically) masks the appearance of your GTK+ programs such like a QT native program. Sometimes it makes problems with some GTK softwares and programs crash.

I'm happy to help you ;)

Goodbye from Italy

---

### Post by ianmillington on 2011-10-28
Not wishing to be too controversial here but isn't the "proper" solution to make a ubuntu one client that will work with KDE with appropriate plugins for Amarok etc? Blimey I can't even buy albums from Amazon either without downgrading so there must be an opportunity here. Maybe the official line is "we don't care", but they've done it for Windows, why not their own stepchild? 

If there is one thing that will ultimately make me leave 'buntu, it will be that "second best" feeling - I'm clearly getting it on this issue. 

rant over

---

### Post by hypertyper on 2011-11-11
> **MatteoR said:**
> Hi there ):P.

I come from the italian ubuntu-it forum (sorry for my bad english, but I want to help you)

I found a workaround to run Banshee in Kubuntu. :D

You have to go into System settings > Application appearance > GTK+ Appearance and in "object style" select the "Raleigh" option. Then you click ok button. 
Enjoy :p

Thank you! I had tried different suggestions but this got it to work!

---

### Post by Topheman on 2011-12-01
" "object style" select the "Raleigh" option. Then you click ok button. "

I don't have "object style" under application, only "gtk styles" and "gtk fonts" do I miss something? please help :(

---

### Post by Mr.Goose on 2011-12-01
The *correct* location in System Settings is actually:-

[INDENT]**Common Appearance and Behavior ->  Application Appearance -> GTK+ Appearance -> Widget Style**[/INDENT]

Also, it seems you can pick any widget style you like, **_except_ oxygen-gtk!**

The idea of Oxygen-GTK was to give GTK & KDE apps the same look and feel. But I think it looks horrible! So it's no great loss IMHO. However if you desire a common widget set for both GTK and KDE applications, then you may wish to install the elegantly simple QtCurve widget set. Personally I think it is one of the nicest Linux widget sets ever. Moreover, unlike Oxygen-GTK, QTCurve works perfectly with Banshee! OK, here's how...

[INDENT]1. Firstly, you need to download a little software from the *'Bunty* repositories. So please type the following into a terminal window (e.g. Konsole) and hit the return key:-
```
sudo apt-get install gtk2-engines-qtcurve kde-style-qtcurve
```

2. To select GTK style part, please open System Settings and go:-
**Common Appearance and Behavior ->  Application Appearance -> GTK+ Appearance **

3. Click **Widget style** picklist and select **QTCurve**

4. Click **Apply**

5. To select matching KDE style, in System settings please go:-
**Common Appearance and Behavior ->  Application Appearance -> Style**

6. Click **Widget style** picklist and select **QTCurve**

7. Click **Apply**[/INDENT]

Obviously you also need to restart any open applications in order to see the new widgets. But you **don't** need to restart your computer or XWindow system. That's it! Now you can enjoy crash-free Banshee in Kubuntu, whilst enjoying a very elegant-looking and properly-matching set of widgets across your various applications. 

:guitar:

Enjoy. G.

---

### Post by CentralCaFan on 2011-12-20
Mr. Goose,

Very helpful post! I had been using GTK+ theme and never was happy with Raleigh. So I started using Akregator and Clementine instead of Banshee, although became perfectly happy doing so. John.

---

### Post by FatAngus on 2012-03-08
Thank you Mr Goose

As CentralCaFan mentioned earlier changing to Raleigh wasn't really working for me either, it made my Firefox and other applications look very ugly.

Anyway thanks again :)

---

