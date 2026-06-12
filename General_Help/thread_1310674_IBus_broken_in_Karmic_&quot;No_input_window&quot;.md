---
title: "IBus broken in Karmic &quot;No input window&quot;"
date: 2009-11-02
forum: General Help
---

### Post by totsubo on 2009-11-02
I've just updated my Ubuntu to Karmic Koala and am trying tu use IBus for an IME (since it is now the recommend IME).

I start IBus from System|Preferences and have installed both English and Japanese (Anthy) as input methods. However when I click on the IBus icon it always says "No input window". I've tried opening a simple text editor, Firefox, and other applications but IBus always says 'No input window".

I've tried clicking on the IBus icon or using the hotkey (Ctrl-Space) but IBus never lets me select and input method.

Is there a bug with IBus in Karmic?

Any and all is appreciated! I'm totally unable to continue with my Japanese studies now that I have upgraded! :(

---

### Post by ubun_two on 2009-11-02
I am having the exact same issue.

So far, the only way around that I found is that I manually start ibus from the terminal by typing:

ibus-daemon -d

I tried putting this line in Session for automatic start, but I get "No input window" if I did that.  The only way it works seems to be by excuting it from the terminal...weird.

You can find this issue on the bug page for iBus.  Please elevate this issue by clicking on the star.

[http://code.google.com/p/ibus/issues/detail?id=519&q=9.10&colspec=ID%20Component%20Type%20Status%20Priority%20Milestone%20Owner%20Summary](http://code.google.com/p/ibus/issues/detail?id=519&q=9.10&colspec=ID%20Component%20Type%20Status%20Priority%20Milestone%20Owner%20Summary)

---

### Post by alexyz on 2009-11-02
I think there may be two separate problems here...

I had a similar auto-start problem, only worked when I ran from terminal.  See fix here

[http://ubuntuforums.org/showthread.php?p=8226110#post8226110](http://ubuntuforums.org/showthread.php?p=8226110#post8226110)

---

### Post by totsubo on 2009-11-02
I fixed the issue but not sure how. I removed IBus, and removed scim, and im-switch.

I reinstalled both, multiples, individually and seperately and with multiple reboots just to be sure. I think the problem *might* have been  that IBus was missing the input method service for whatever language you want to use. In my case it was ibus-anthy. (But that being said I am pretty sure I had already loaded it!)

Hope that helps.

---

### Post by simynona on 2009-11-02
I'm encountering the same problem. I tried to add Chinese (PinYin) as an input method, but IBus will not recognise anything as an input window, no matter if I start it manually or not.

---

### Post by daqron on 2009-11-04
This is infuriating. What the hell was wrong with SCIM that they felt the need to completely break it in favor of something that doesn't work?

ARGH.

Anyway ... so I followed the instructions I could find, including reinstalling iBus and removing SCIM, but nothing works. I currently have NO input methods available in the iBus preferences, even though I have enabled English and Chinese in my Language Support preferences.

Even when I did have languages available in iBus, all I ever got from the iBus icon in my tray was "No Input Window". 

What gives, Ubuntu overlords?

**Edit:** Removed iBus and SCIM, then reinstalled scim and scim-pinyin in Synaptic Package Manager. Everything works again now. Maybe I'll give iBus another try in the next release when they've (hopefully) worked the bugs out.

---

### Post by Shiranami on 2009-11-04
Unfortunately I can't provide a solution, rather I have the same problem myself. The only difference is that iBus (with Anthy) seems to work for me in Firefox (after a lot of random tinkering, I'm not even sure what finally did it), but it's the only application that doesn't give me the "no input window" -message. So far I've tried it in kate, openoffice and amsn, but to no avail. It's a little tiresome to have to type everything in Firefox and then copy & paste...

Also, I have to start the daemon manually, and am not sure what I'm supposed to do to get it to auto-start. There's a message every time I start it and I followed the instructions, but that did absolutely nothing. :/ I'm at a loss. Will appreciate any information and/or help with these issues.

---

### Post by wildweathel on 2009-11-04
I had this problem intermittently when I had IBus installed but not properly set up.  Try going to "System -> Administration -> Language Support" and make sure the input method is set to IBus.  Then log out, log in.  Does that fix it?  If you're missing some language components, Language Support will try to install them, too.

---

### Post by simynona on 2009-11-06
Setting the input to IBus in the language support menu solved my problems!
&#38750;&#24120;&#22909;&#65281;&#25105;&#21487;&#20197;&#25171;&#23383;&#20013;&#25991;&#65281;&#35874;&#35874;&#20320;&#12290;

---

### Post by s.jegen on 2009-11-10
I have the "No input Window"-problem as well, even after setting the input option in the Language Support Menu to "Ibus". Interestingly Firefox seems to be the only program on my current 9.10 installation that works with Ibus under these settings without any problems.

---

### Post by xyepblra on 2009-11-15
IBus does not work in OpenOffice.org and Skype. Need help.

---

### Post by bknecht on 2009-11-17
I have a similar problem. Though iBus sometimes works with all applications. However it somehow blocks my input into Java applications after some time. That's when I quit the daemon to fix the problem with the Java app.

Now iBus usually starts when I login and works flawlessly. But when I restart it, after quitting it earlier iBus shows a behavior similar to the one explained in this thread. iBus works with Firefox, Epiphany and Terminal. However not with other apps like Anki, Acrobat Reader, Kile and Skype.

Now that I think about it, it could be connected to the GUI manager associated with the application. As everything seems to work fine with Gnome Apps while Anki and Kile are Qt Apps..
I hope my input helps you to figure it out the problem. I'd be thrilled to hear about a workaround or fix of this problem.

EDIT:
I found a way to fix my problem with Qt Apps. I installed the package "ibus'qt4" and manually started the ibus daemon with those arguments:
--xim GTK_IM_MODULE=ibus QT_IM_MODULE=ibus

I'll now try to put those arguments in .bashrc in my home directory to see if it works with this as well.

---

### Post by Goren on 2010-01-01
I have the same problem: ibus works in some applications, but not in the others. Of applications I use regularly, where it doesn't work (and that are rendered all but useless by the inability to use input methods) I have to name OpenOffice.org, Lyx and Emacs. I searched a lot through the internet, and apparently there's no solution.

---

### Post by Bernard Hurley on 2010-01-03
First make sure ibus-qt4, and any other ibus packages you need for your particular language are installed.

Now try the following:

1]

Under System->Administration->Language Support

For "Keyboard input system" choose "ibus"

2]

Under System->Preferneces->Startup Applications
Click on "Add" and fill min dialog box as

Name: iBus
Command: ibus-daemon -drx
Comment: the ibus demon

Now click "Add"

Note: all options in -drx are needed.
-d makes ibus-daemon actually run as a deamon.
-x starts the ibus xim server so that applications that only use xim can use it
-r this is more subtle. It re-starts ibus. If you don't have this, ibus will work OK the first time you log in. However when you log out ibus will still be running. When you log in again, "ibus-daemon -dx" will be called and will think "I'm already running so I don't need to do anything". The problem is that the running version of ibus expects a different gnome session (the one you logged out of) and as a result you won't see the ibus applet. It's actually still usable in this state, but its much nicer to have the applet.

3]
Open .bashrc in an editor (e.g. gedit) and add the following lines:

export GTK_IM_MODULE=ibus
export XMODIFIERS="@im=ibus"
export QT_IM_MODULE=ibus

Note: You can probably get away without [3], as far as I can make out it is only needed for some legacy apps that run in a terminal. But, what the hell, it doesn't do any harm!

---

### Post by Hilko on 2010-02-18
Hi

I have a very weird problem and really need some help. IBus seems to almost work.
It runs at startup. I can select input method with the shortcuts, it recognizes input windows. The only problem is this:

Whenever i try to type a Chinese character, i see the character appear and the moment i hit 'enter' it is replaced by english tekst.

As a result i cannot type anything but English. Please help...

[edit]
Ok Ok Ok. forget the above. I just need to type a 'space' instead of hitting 'enter'. That was all.

---

### Post by rory526 on 2010-02-27
Thanks Bernard, that fixed it for me. &#44048;&#49324;&#54644;&#50836;!

---

### Post by BurakUeda on 2010-04-04
None of the above worked for me, but this solution did:
[http://code.google.com/p/ibus/issues/detail?id=613](http://code.google.com/p/ibus/issues/detail?id=613)

Solution:
Change the /etc/X11/xinit/xinput.d/default contents into these:
XIM=ibus
XIM_PROGRAM=/usr/bin/ibus-daemon
XIM_ARGS="--xim"[FONT=Verdana]

[/FONT]GTK_IM_MODULE=ibus      
QT_IM_MODULE=ibus

DEPENDS="ibus, ibus-gtk, ibus-qt4"

of course, make sure you have ibus, ibus-gtk, ibus-qt4 packages installed..
and restart X...

Hope this helps :)

---

