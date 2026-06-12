---
title: "how to use ibus?"
date: 2009-09-08
forum: General Help
---

### Post by beemzet on 2009-09-08
Hi all,

I want to use russian, korean and english with iBus. These are the shortcuts to control ibus:
Enable or Disable: Control + space
Next input method: Control + Alt + space

Input methods are Russian-kbd and Korean-Hangul, in the order presented.


Now, when I want to type in russian, then I have to hit Control + space, but when I want to use Korean I have to hit Control + Alt + space. And when I want to switch to english, I have to hit Control + space, which, in my opinion, is inconsistent. Is there a way that I can set up ibus to function the same way as windows or mac os x?

Any help would be appreciated.
Thanks

---

### Post by khughitt on 2009-09-09
I'd also be interested to see if anyone is successfully using this on Ubuntu 9.04/9.10, specifically for Traditional Chinese Pinyin input?

---

### Post by jastonas on 2009-10-12
What is Ibus?

---

### Post by khughitt on 2009-10-12
ibus ([http://code.google.com/p/ibus/](http://code.google.com/p/ibus/)) is software for inputting foreign characters (Chinese, Korean, etc), similar to SCIM. 

I've actually been using it for the past several months, and I really like it.

---

### Post by davescafe on 2009-10-31
I am completely new to IBus, but I need to input Korean and so I have been experimenting with IBus tonight. I am using Ubuntu 9.10.
[B]
Start IBus [/B]
Navigate to the menu:
[INDENT]System >> Preferences >> IBus Preferences[/INDENT]

You will see a message which reads:
> IBus daemon is not started. Do you want to start it now?
Click, "Yes"
After clicking yes, I received the following message:
> 
IBus has been started! If you can not use IBus, please add below lines in $HOME/.bashrc, and relogin your desktop.
  export GTK_IM_MODULE=ibus
  export XMODIFIERS=@im=ibus
  export QT_IM_MODULE=ibus
I have not been able to see any difference that these lines make in the ~/.bashrc file. I added these lines and rebooted and then did some testing. Then I took the lines out, rebooted again, and tested again. The behavior of IBus is the same for me either way.

**IBus Preferences**
Here is what I selected for Korean input:
_General (tab)_
Check: Show input method name on language bar
_Input Method (tab)_
Select an input method: Korean >> han2
Click the button: Add

**PROBLEM: IBus doesn't start automatically when I restart my computer**
Here is how I solved the problem:
Go to the menu:
System >> Preferences >> Startup Applications
Click the button: Add
Name: IBus daemon
Command: /usr/bin/ibus-daemon -d
Comment: start IBus daemon when Gnome starts

**IBus usage tips**
[LIST]
[*]Input methods can be selected by clicking on an icon (of a keyboard and a tiny globe) in the notification area (the upper right part of the top edge panel)
[*]If you click on the icon and it says, "No input window" that just means that there is no window currently selected where text can be entered. Open up a text editor or click some place where text can be entered, and then go back to the IBus icon. You should see the selection of input methods.
[/LIST]

Edit: added full path to ibus-daemon

---

### Post by Frantic_Earthling on 2009-11-01
Davescafe, many thanks for your tip on how to get iBus to start automatically. Works perfectly!



[I]PROBLEM: IBus doesn't start automatically when I restart my computer
Here is how I solved the problem:
Go to the menu:
System >> Preferences >> Startup Applications
Click the button: Add
Name: IBus daemon
Command: /usr/bin/ibus-daemon -d
Comment: start IBus daemon when Gnome starts[/I]

---

### Post by bruno.braga on 2009-11-02
> **pwnedd said:**
> I'd also be interested to see if anyone is successfully using this on Ubuntu 9.04/9.10, specifically for Traditional Chinese Pinyin input?

I did actually, after some work (just follow what people wrote here). If you want it to work without rebooting or logging out, just restart the ibus daemon:
```

$ killall ibus-daemon 2>/dev/null
$ ibus-daemon -d &

```

---

### Post by alexyz on 2009-11-02
**edit**:  actually below is wrong. You do not need to run ibus as a startup program if you set it to the default input system:  System > Administration > Language Support

I was having trouble with the iBus panel applet.  When auto-started, the daemon was running, input worked, but no panel applet.  When I ran it manually the panel applet showed up.  Fixed after I did this setting in iBus preferences:

> **davescafe said:**
> 
_General (tab)_
Check: Show input method name on language bar


In other words, you MUST select "show input method name on language bar" to make the applet show up when auto-started.  Apparently this is not necessary when running it manually.

huh, is that THE davescafe??  :-D

---

### Post by T4K3Z0U on 2009-11-03
> **davescafe said:**
> 

I have not been able to see any difference that these lines make in the ~/.bashrc file. I added these lines and rebooted and then did some testing. Then I took the lines out, rebooted again, and tested again. The behavior of IBus is the same for me either way.

Could you tell me where exactly those 3 lines of text go? I have searched and searched, but don't have any file/folder labeled .bashrc hidden or otherwise. I have no clue what I should do. 
SCIM isn't working for me which is why I am trying IBus.

> **davescafe said:**
> 
[LIST]

[*]If you click on the icon and it says, "No input window" that just means that there is no window currently selected where text can be entered. Open up a text editor or click some place where text can be entered, and then go back to the IBus icon. You should see the selection of input methods.
[/LIST]



I get this message in the search bar on google and in Open Office. So it seems for now, I do not have the ability to use other languages.

I'm running 9.10

---

### Post by alexyz on 2009-11-03
> **T4K3Z0U said:**
> I have searched and searched, but don't have any file/folder labeled .bashrc hidden or otherwise

.bashrc is in your home folder - the full path is /home/yourusername/.bashrc 

If you don't have one then it either got deleted or somehow was not installed, which is rather strange.  In any case if it's not there just create a new file with that name, but I'd recommend figuring out why it's not there.

You need to log out and log in for this to take effect.

BTW the tilde character ~ is a handy shortcut for your home directory, and files whose name begins with a dot are hidden.

---

### Post by T4K3Z0U on 2009-11-03
> **alexyz said:**
> If you don't have one then it either got deleted or somehow was not installed, which is rather strange.  In any case if it's not there just create a new file with that name, but I'd recommend figuring out why it's not there.


I am a dunce. I was looking for a folder, not a file (even though file was clearly indicated.) Leaving my stupidity aside. Do I go to the bottom of the page type # and the lines? Or perhaps there is no space after #?

---

### Post by alexyz on 2009-11-03
> **T4K3Z0U said:**
> Do I go to the bottom of the page type # and the lines? Or perhaps there is no space after #?

yes, just paste the three lines at the bottom of the ~/.bashrc file.  The initial # sign makes the line a comment (the system ignores comments).  So add text like this:

# these environment variables required to run iBus
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus 

The comment line is a handy place to explain in plain English (or the language of your choice) just what the *#*&# this garbage means.  And T4K3Z0U, you are not a dunce, you've just never done this before. ):P

---

### Post by T4K3Z0U on 2009-11-03
Well I sure wish I had waited for your reply before trying the idea below. Because now, in IBus under input method, there is nothing. I didn't touch IM switch, but removed, then re-installed scim and ibus. ETA: The reinstall must have gone wrong. When I went to remove IBus, it was being used by 3 pieces of installed software. Now only 1.

> **totsubo said:**
> I fixed the issue but not sure how. I removed IBus, and removed scim, and im-switch.

I reinstalled both, multiples, individually and seperately and with multiple reboots just to be sure. I think the problem *might* have been  that IBus was missing the input method service for whatever language you want to use. In my case it was ibus-anthy. (But that being said I am pretty sure I had already loaded it!)

Hope that helps.

---

### Post by T4K3Z0U on 2009-11-03
> **T4K3Z0U said:**
> Well I sure wish I had waited for your reply before trying the idea below. Because now, in IBus under input method, there is nothing. I didn't touch IM switch, but removed, then re-installed scim and ibus. ETA: The reinstall must have gone wrong. When I went to remove IBus, it was being used by 3 pieces of installed software. Now only 1.

Just to give a bit of detail to my previous post. When IBus was there, the input method had all the languages under the sun in there. But after removing then reinstalling IBus and SCIM, the input method for IBus was empty, absolutely nothing there. 

I don't know why, but started to think about the problem, and went to the Ubuntu software center (formally known as add/remove programs) and did a search using keywords "input method" and there was one program that looked promising but wasn't installed. I installed it, rebooted my machine, and now the language I wanted is available in IBus, it's the only one there, but that's all good. I am happy, and for me, this problem is now fixed. 

I'd like to just add, that I changed from SCIM after the language I wanted to use disappeared after upgrade to 9.10, and under the SCIM input method setup I could not, and still cannot find an option to add said language. Then discovered that IBus is a new feature for languages.

Anyway, thanks everyone in this thread for the help which led me to getting the problem fixed.

---

### Post by alexyz on 2009-11-04
on T4K3Z0U's problem:  scim is a different software package.  It's also an input method system like iBus, but a different one.  You can install both scim and iBus at the same time, and this can be confusing because you can change the settings even when the system is not actually in use.  iBus settings are:

main menu > System > Preferences > iBus Preferences

---

### Post by xyepblra on 2009-11-15
Guys, please share your experience using ibus with OpenOffice.org and Skype.

---

### Post by T4K3Z0U on 2009-11-20
> **xyepblra said:**
> Guys, please share your experience using ibus with OpenOffice.org and Skype.

It's absolutely great. Before Ibus I couldn't use other languages in skype. Have never had an issue with openoffice.

---

### Post by xyepblra on 2009-11-20
> **T4K3Z0U said:**
> It's absolutely great. Before Ibus I couldn't use other languages in skype. Have never had an issue with openoffice.So how did you manage making Ibus work with Skype and OpenOffice.org? I really need to do the same.

---

### Post by T4K3Z0U on 2009-11-20
> **xyepblra said:**
> So how did you manage making Ibus work with Skype and OpenOffice.org? I really need to do the same.

Once I managed to get it to install the language I wanted, it worked by itself in skype. Have you upgraded to Karmic 9.10? This is when I first discovered Ibus. I think I bus may have been around before Karmic, but I never saw it, and it was after the upgrade, I lost use of SCIM and finally got Ibus working. Never looked back.

If your talking about how to switch between languages, the keys are Ctrl + Space. Used to be Ctrl + Shift using the old fashioned SCIM.

Karmic is great on so many levels. I love it, can't wait to see how they improve things next.

---

### Post by xyepblra on 2009-11-20
> **T4K3Z0U said:**
> Once I managed to get it to install the language I wanted, it worked by itself in skype. Have you upgraded to Karmic 9.10? This is when I first discovered Ibus. I think I bus may have been around before Karmic, but I never saw it, and it was after the upgrade, I lost use of SCIM and finally got Ibus working. Never looked back.

If your talking about how to switch between languages, the keys are Ctrl + Space. Used to be Ctrl + Shift using the old fashioned SCIM.

Karmic is great on so many levels. I love it, can't wait to see how they improve things next.

Thing is, I know how to launch Ibus to type Chinese in the applications, except it does not launch in OO.o and Skype. Did you modify ~/.bashrc? How did you set up Ibus? Are there other settings to be modified in order to make Ibus launchable with OO.o and Skype?

---

### Post by gabarice on 2009-11-20
I have tried all the various methods mentioned above until it worked. I retraced the steps and confirm that the installation steps is simple. Here are the steps from fresh install :

1)     At System/Language Support:
1a)  Select and install the languages which you required
1b)  Apply changes and the required language will be download from the repository. Make sure you are connected to the Internet.
1c) At ¨Keyboard Input System¨, select ¨ibus¨.

2) Reboot. Upon rebooting, an icon of a keyboard with a small globe can be seen at the top right. Let call this the Language Input Method or LIM icon.

3) Right-click that LIM icon , select ¨Preference¨.

3a). At the ¨General¨ tab, tick ¨show input method name on language bar¨.

3b) At the ¨Input Method¨ tab, click the drop down window ¨Select an Input Method¨. Select and Add the language you required. You can select as many languages you required. Always ¨Select¨ and ¨Add¨ each required language.

4) There the installation is completed.

5) If you left-click the LIM icon, it will show ¨No input window¨. No problem.

6) Open, example, OpenOffice Writer, left-click the LIM icon, it will list the input methods which you have selected in 3b.

7) Alternatively for step 3, you can do the same changes in System/Preferences/iBus Preferences.

I have test the Language Input Method in OpenOffice, Text Editor and Firefox and it works great for me in Chinese Pinyin. I do not have skype so I do not know whether it works or not.

Thank you to all who have contributed.:p

---

### Post by T4K3Z0U on 2009-11-20
> **xyepblra said:**
> Thing is, I know how to launch Ibus to type Chinese in the applications, except it does not launch in OO.o and Skype. Did you modify ~/.bashrc? How did you set up Ibus? Are there other settings to be modified in order to make Ibus launchable with OO.o and Skype?

Oh I see. I really can't recall how I actually got Ibus to run in the end. I think I may have modified the bashrc file, but that would have been to get the languages working. I didn't modify anything to type in Open Office or Skype.

Sorry I can't help you further than this.

---

### Post by arquisto on 2009-11-22
I freshly installed Karmic a couple days ago and installed the IME's right away.  After installation there was a the installation there was a pop-up window with the following advice:

IBus has been started! If you can not use IBus, please add below lines in $HOME/.bashrc, and relogin your desktop.
  export GTK_IM_MODULE=ibus
  export XMODIFIERS=@im=ibus
  export QT_IM_MODULE=ibus
 
I followed the advice and now iBus works perfectly fine.

Hope this helps.

---

### Post by gabarice on 2009-11-22
It is not necessary to add those lines. See my installation steps above.

> **arquisto said:**
> I freshly installed Karmic a couple days ago and installed the IME's right away.  After installation there was a the installation there was a pop-up window with the following advice:

IBus has been started! If you can not use IBus, please add below lines in $HOME/.bashrc, and relogin your desktop.
  export GTK_IM_MODULE=ibus
  export XMODIFIERS=@im=ibus
  export QT_IM_MODULE=ibus
 
I followed the advice and now iBus works perfectly fine.

Hope this helps.

---

### Post by simon_w on 2009-12-07
fwiw, I had some difficulties with iBus, specifically in relation to using a hàny&#468; p&#299;ny&#299;n keyboard to type Traditional Chinese (libchewing).  I found it would frequently lose my keyboard setting and revert to zhùy&#299;n ([bug report here]("https://bugs.launchpad.net/ubuntu/+source/ibus-chewing/+bug/475061")).  I could work around the issue, by cycling through all my (seven!) input methods, but it was annoying as hell, and in QT etc. application, such as Skype, I could never get the right keyboard.

So I gave up and went back to scim - all is well now :) :popcorn:

---

### Post by JAwuku on 2009-12-31
Thanks to all, for the tips in setting up IBus.

It works *almost* perfectly on my Karmic 9.10 system.

The only problem, is that Karmic does not have a default input method for Ukrainian transliteration, that I was used to on Jaunty.

Just thought I would share how I set up Ukrainian input on Karmic.

So, to solve, it, you can get the package **[[COLOR="Blue"]ibus-table-translit[/COLOR]]("http://packages.ubuntu.com/lucid/all/ibus-table-translit/download")** from the Ubuntu Lucid package page. (click bold blue letters)

[URL="http://packages.ubuntu.com/lucid/all/ibus-table-translit/download"][COLOR="Blue"]**http://packages.ubuntu.com/lucid/all/ibus-table-translit/download**[/COLOR]
[/URL]
and install it.

It works fine on Karmic.

Just restart IBus (right-click on the keyboard symbol at the top of the screen),

and add Ukrainian translit in the options.

---

### Post by ghormax on 2010-01-29
I am generally happy with ibus. However, I cannot select a character with the mouse (I have to type the number). Does anyone know if this is merely a problem with my installation or a general problem (bug)? I am using the latest Ubuntu 9.10 fully updated.

---

### Post by lannatwin on 2010-02-12
> **T4K3Z0U said:**
> Just to give a bit of detail to my previous post. When IBus was there, the input method had all the languages under the sun in there. But after removing then reinstalling IBus and SCIM, the input method for IBus was empty, absolutely nothing there. 

I don't know why, but started to think about the problem, and went to the Ubuntu software center (formally known as add/remove programs) and did a search using keywords "input method" and there was one program that looked promising but wasn't installed. I installed it, rebooted my machine, and now the language I wanted is available in IBus, it's the only one there, but that's all good. I am happy, and for me, this problem is now fixed. 

I'd like to just add, that I changed from SCIM after the language I wanted to use disappeared after upgrade to 9.10, and under the SCIM input method setup I could not, and still cannot find an option to add said language. Then discovered that IBus is a new feature for languages.

Anyway, thanks everyone in this thread for the help which led me to getting the problem fixed.

Umm, I am having the same problem as you.  Any chance you could share what the "one program that looked promising" is??  Thanks.

---

### Post by computermacgyver on 2010-04-09
FYI:
The new version of Ibus (1.2.99) has a feature to share input method between applications. 

Ubuntu packages are at [https://launchpad.net/~ibus-dev](https://launchpad.net/~ibus-dev)

(Thanks to tin_truc22 for noting this [http://ubuntuforums.org/showthread.php?p=9096735#post9096735](http://ubuntuforums.org/showthread.php?p=9096735#post9096735) )

---

### Post by xyepblra on 2010-06-20
Call me stupid, but ibus doesn't type Chinese in my Skype, no matter if there are or there are no three magic lines there in ~/.bashrc. Any other magic tricks I am missing?

---

### Post by xyepblra on 2010-07-07
> **xyepblra said:**
> Call me stupid, but ibus doesn't type Chinese in my Skype, no matter if there are or there are no three magic lines there in ~/.bashrc. Any other magic tricks I am missing?
What I did to solve the iBus not working with Skype problem:
[LIST=1]
[*]Uninstalled Skype completely
[*]Installed Skype again after reload
[*]installed ibus-qt4 module
[/LIST]
After fullfilling the procedure described above my iBus still hasn't been willing to type Chinese in the Skype message text input field. A lucky guess told me to click the right button on the Skype message text input area and I found "Input method" option in that menu. By changing "XIM" to "ibus" I enabled ibus input in Skype.

---

### Post by lonetree on 2011-01-30
> **xyepblra said:**
> What I did to solve the iBus not working with Skype problem:
[LIST=1]
[*]Uninstalled Skype completely
[*]Installed Skype again after reload
[*]installed ibus-qt4 module
[/LIST]
After fullfilling the procedure described above my iBus still hasn't been willing to type Chinese in the Skype message text input field. A lucky guess told me to click the right button on the Skype message text input area and I found "Input method" option in that menu. By changing "XIM" to "ibus" I enabled ibus input in Skype.

It seems like the input option is not available in 64 bits version. I'm using 10.10 64 bits, chinese input in skype is not available,. Any thoughts?

regards

---

### Post by samMD on 2011-05-26
Im trying to start ibus so I can use Heimdall the Linux alternative to ODIN on windows for flashing kernel's and ROM's onto android devices..how would I start it?

Thanks

---

