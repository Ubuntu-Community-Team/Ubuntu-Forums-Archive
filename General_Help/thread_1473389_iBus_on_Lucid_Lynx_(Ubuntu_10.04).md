---
title: "iBus on Lucid Lynx (Ubuntu 10.04)"
date: 2010-05-05
forum: General Help
---

### Post by bruno.braga on 2010-05-05
Just to share with everyone. One of the first things I set up on my machine is input method support (for both japanese and chinese). I just installed the new Ubuntu on a clean machine, and noticed that iBus (the new default input method editor since 9.04, I guess) did not work properly.

The main things you need to worry about (and fix manually) are:  

1) First time start
iBus does not start automatically, so the first time you get it running, you will probably do so by going to **Menu > System > Preferences > iBus Preferences**. Then a message will popup informing to do some updates on the ~/.bashrc file. Please do that accordingly (this will guarantee you to use iBus on GTK based windows, for example).

2) Automatic start on boot

Don't forget to force it to run automatically. There are lots of ways to do that, but a very simple one is to add the application to **Menu > System > Preferences > Startup Applications**. There you just add a new one by naming it as *iBus* and pointing to ibus location: **/usr/bin/ibus-daemon**

This should do the trick for you.

3) iBus is running, but something is not right
Once you have it running, you may see an icon on the top right panel of your screen. So you can left-click on it, and go to preferences. This will allow you to add the languages you want and define how you want to change them from the keyboard. I usually leave the default which is similar to other input methods from Windows and Mac.

The trick here was that even though I could add the languages, I could not use them (for japanese, for instance, you should type phonetically, and then choose the ideograms from a list, which was not available to me).

I fixed this problem by manually installing the packages for ibus (ibus-anthy for japanese and ibus-pinyin for chinese). Once I did that and restarted it, everything was again working smooth.

Maybe for "human beings", the suggestion would be to automatically install the language packages once the language is selected. 
 
Cheers,

---

### Post by zaphod777 on 2010-05-05
actually you need to goto system -> administration -> language support.

to install the languages. A little more automatic would be nice though. 

You should suggest it in launchpad.

---

### Post by bruno.braga on 2010-05-05
Actually, if I am not mistaken, this installs primarily the support for languages in terms of the whole operating system, and probably the iBus stuff would come along. So, unless you need your OS in another language, I don't see much use of that.

---

### Post by zaphod777 on 2010-05-05
> **bruno.braga said:**
> Actually, if I am not mistaken, this installs primarily the support for languages in terms of the whole operating system, and probably the iBus stuff would come along. So, unless you need your OS in another language, I don't see much use of that.

This is how I have it configured on mine my main OS is in English and I can type &#26085;&#26412;&#35486; just fine.

---

### Post by zaphod777 on 2010-05-05
Here are some screenshots Also I found it very convenient to use Ctrl+Shift to enable and disable plus the super key to switch between English and Japanese input. 

[IMG]http://lh4.ggpht.com/_sjlVRfKJcmw/S-FcvTVhYWI/AAAAAAAABAw/A8jOEPsBSnc/s400/Screenshot.png[/IMG]

[IMG]http://lh4.ggpht.com/_sjlVRfKJcmw/S-FcwBpqyBI/AAAAAAAABBA/TkmMJUsaa1w/s800/Screenshot-Language%20%26%20Text.png[/IMG]

[IMG]http://lh4.ggpht.com/_sjlVRfKJcmw/S-Fcv7svFbI/AAAAAAAABA8/0UQxSMxKnew/s800/Screenshot-IBus%20Preferences-1.png[/IMG]

[IMG]http://lh4.ggpht.com/_sjlVRfKJcmw/S-Fcvj_kssI/AAAAAAAABA4/AQH0Rv1JzLY/s800/Screenshot-IBus%20Preferences.png[/IMG]

[IMG]http://lh6.ggpht.com/_sjlVRfKJcmw/S-FcvleeBsI/AAAAAAAABA0/EiJVNkLjEUE/s800/Screenshot-Edit%20Startup%20Program.png[/IMG]

---

### Post by yufengz on 2010-05-08
> **zaphod777 said:**
> actually you need to goto system -> administration -> language support.

to install the languages. 

This works for me as well. 

bruno.braga's went a curved way, which should be blamed on Ubuntu as the system should give warnings when a language input has not been installed yet, rather than pretending its existence.

Thank you for you two!

Cheers,
Yufeng

---

### Post by jasontan6 on 2010-05-09
> **bruno.braga said:**
> 
2) Automatic start on boot

Don't forget to force it to run automatically. There are lots of ways to do that, but a very simple one is to add the application to **Menu > System > Preferences > Startup Applications**. There you just add a new one by naming it as *iBus* and pointing to ibus location: **/usr/bin/ibus-daemon**

This should do the trick for you.


I followed a few other threads which told me to use
```
ibus-daemon -d
```
but then iBus would start without the keyboard icon. Removing the -d argument (as in yours) works, thanks!

---

### Post by bruno.braga on 2010-05-09
> **jasontan6 said:**
> I followed a few other threads which told me to use
```
ibus-daemon -d
```
but then iBus would start without the keyboard icon. Removing the -d argument (as in yours) works, thanks!

Wow, that's weird. The --help indicates that the -d argument is just to "daemonize" the ibus in background (but in terms of startup applications, this kind of has no meaning).

But, glad it solved your problem! :P

---

### Post by keroro on 2010-05-12
I upgraded from Karmic and like always spend hours figuring out why Japanese input is not working. I used skim before. For Lucid I uninstalled skim and try to use ibus. 
I open a text editor, type some hiragana, can select the kanji, but as soon as I hit return, it is deleted.
Anybody has any idea?

---

### Post by zaphod777 on 2010-05-12
make sure you have Japanese language installed under system languages. If you don't then that will happen if I remember correctly.

---

### Post by keroro on 2010-05-12
Japanese language is installed. Used it before under Karmic.
I can type it, see the word and as soon as I press return, it is gone.

---

### Post by zaphod777 on 2010-05-12
hmm I would probably try completely removing ibus (with config settings) and then re-installing it.

---

### Post by bruno.braga on 2010-05-13
Just noticed that my default font is messing up the ideograms (for Japanese)... some korean chars are appearing instead (see attached file).

---

### Post by hihihi100 on 2010-05-13
Hi there:  I have a related question regarding IBUS and 10.04...  I also use it to write in Chinese and Japanese,and it works flawlessly. However, I cannot see any icon in the IM list: for instance, if I want to use tone pinyin, I can read the words &quot;tone pinyin&quot;, but there is a blank space on the left, exactly where the icon should be... Same applies to Anthy, (Japanese) I cannot see the crown...  Thoughts?

---

### Post by kryssix on 2010-05-14
After using ibus with 10.04 for about a month and a half, I now suddenly can't type Japanese. As the default language on my system is Japanese and a lot of what I do requires the language, it's more than a little annoying. I can still type in Korean which makes me wonder if it's an Anthy-related problem.

I have all Japanese support packs installed and the language appears as on option on ibus, but nothing happens when any of them are selected. It used to work fine just pressing the zenkaku key (to the left of 1 on a Japanese keyboard).

Yesterday I was trying to use VLC to record streaming video and there must have been an overflow somewhere as my entire 80GB Ubuntu partition got used up, making VLC player unresponsive and I had to kill the process. My disk space appeared again but ibus would only let me use Korean, even after restarting.

I tried completely removing and reinstalling ibus, including the config files that I could find in my home folder.

Any help would be greatly appreciated.

Edit::

Well, after thinking it was Anthy's fault I removed the .anthy folder from my home folder, uninstalled it, reinstalled it, logged out and back in and it worked.

---

### Post by bruno.braga on 2010-05-15
> **hihihi100 said:**
> Hi there:  I have a related question regarding IBUS and 10.04...  I also use it to write in Chinese and Japanese,and it works flawlessly. However, I cannot see any icon in the IM list: for instance, if I want to use tone pinyin, I can read the words &quot;tone pinyin&quot;, but there is a blank space on the left, exactly where the icon should be... Same applies to Anthy, (Japanese) I cannot see the crown...  Thoughts?

Same with me here...

---

### Post by hihihi100 on 2010-05-16
> **bruno.braga said:**
> Same with me here...

Could it be we need some other app's? any icon related package?

---

### Post by zaphod777 on 2010-05-16
depending on what type of GUI the application uses you may need to install the qt4 modules. 

"ibus-qt4" module might help also using "ibus-daemon --xim" for the startup command might help.

---

### Post by liming on 2010-05-17
Hi!

I just installed 10.04 last night and haven't have time to play it a lot yet but for my disappointment I noticed that now pinyin doesn't do guess working. Previous one usually got right combination ie if I wrote haojiubujian you got &#22909;&#20037;&#19981;&#35265;&#12290;There seems to be less options from which to choose. I will have another look when I get home from work. Still using 9.10 at office.

---

### Post by liming on 2010-05-17
> **keroro said:**
> Japanese language is installed. Used it before under Karmic.
I can type it, see the word and as soon as I press return, it is gone.
In some of the inputs you hit the space to write the character down. Maybe that is something that you can configure. For example mine does now like this I write something and it shows it on the screen if I hit the return it write's it in pinyin but if I hit space it will write the characters instead.

---

### Post by jon.reeve on 2010-05-30
I can't get pinyin to work with more than one character at a time--it's maddening. Is there something I'm doing wrong? 

For example, if I type "beijing" I get &#34987;&#32463;. If I type "pinyin" I get &#21697;&#22240;. If I don't choose each character individually, it will go with the first character in the list, which is often wrong in context. To type &#21271;&#20140; I have to type "bei," stop, choose #4, type "jing," stop, click through three screens of options, choose the correct one, etc. 

It didn't used to be like this. With SCIM I remember I could type "beijing" and instantly get &#21271;&#20140;. 

I'm using an out-of-the-box English Lucid. I've tried all the chinese IMEs that come with ibus, and still no luck.

---

### Post by bruno.braga on 2010-05-31
@jon,

Did you followed the first steps written here? I had similar problem until I manually installed the ibus language packages (only selecting the ibus language on the interface is not enough). 

If so, maybe there is something broken or missing, then better you redo this process once again (re-install).

---

### Post by jon.reeve on 2010-05-31
Ok, I got it to work by installing every package I could with "pinyin" in the name. Now I get the option to use an input method called "pinyin." Before I was using py(m17n) which doesn't like to lookup words of more than one character.

However, for some reason I've lost anti-aliasing with Chinese characters, and so now everything Chinese I type looks really ugly. What's up with that?

---

### Post by Steven Edwards on 2010-06-06
I installed iBus and Anthy a couple of days ago and had a little trouble.  I switched {En,Dis}able to only Alt+grave and Next Input Method to Ctrl+Alt+Shift+n.  The Enable/Disable shortcut would work, but the Next Input Method one wouldn't.

I then read a thread suggesting *sudo im-switch -c*, ran it, and am now paying the price as switching to Anthy (via click En, click Japanese - Anthy) and trying the Next Input Method shortcut both disable iBus.  (Even after complete removal of ibus via Synaptic, reboot, install, reboot.)

To get a "fresh" install of iBus, will I need to purge any packages other than ibus?

---

### Post by bruno.braga on 2010-06-06
Steven,

I think by default the uninstall actions in Ubuntu do not remove configuration files, only the packages. This means, if you install the same packages again, or sometimes even an upgraded package, there is a high probability it will use the existing configuration file(s). 

Try to find it on your filesystem:

```

# to update the database of files in your filesystem
sudo updatedb

# search for keyword "ibus" containing keyword "home"
locate ibus | grep home

```

Note: Before deleting files you are not sure what they do, better creating backup first (a simple "mv file file.old" will suffice).

---

### Post by Steven Edwards on 2010-06-12
Bruno,

Thank you.  I had also tried apt-get purge to no avail, which may have been due to ibus still being my input method system.  Re-purging, switching input method to scim, moving the ibus folders, rebooting, reinstalling Japanese via Language Support, and re-enabling ibus restored my ability to enter &#26085;&#26412;&#35486; characters.  The next input method shortcut still fails, but I sidestepped that by moving Anthy to the top of the list.

Now if only I could switch between hiragana and katakana with the keyboard. *sigh*

Best,

Steven

---

### Post by simosx on 2010-06-14
Some generic advice.

Ubuntu 10.04 uses 'IBus' instead of SCIM which was used in previous versions.
So, if you want to do this the proper way, do it with IBus and do not install any SCIM packages.
Not many people can master Japanese or Chinese, so it is left to those few who can, and can provide the simplest configuration settings to get those scripts enabled.

---

### Post by lesterness on 2010-06-16
I need polytonic Greek. Ibus in Lucid gives me 2 Greek keyboards, but neither seems to have a convenient way to add the accents to the alphabetic letters.  Am I missing something?

Thanks.

lesterness

---

### Post by lesterness on 2010-06-16
How do I change the default font in IBUS? I don't like the default Greek font.

Thanks.

lesterness

---

### Post by simosx on 2010-06-19
> **lesterness said:**
> I need polytonic Greek. Ibus in Lucid gives me 2 Greek keyboards, but neither seems to have a convenient way to add the accents to the alphabetic letters.  Am I missing something?

You can have Greek Polytonic using the default input method in Ubuntu; that is, you do not need to enable IBus. As far as I know, people do not use IBus for Greek Polytonic or even Greek.

Have a look at the instructions for Greek Polytonic in Ubuntu,
[http://simos.info/blog/archives/888](http://simos.info/blog/archives/888)
The instructions are for Ubuntu 9.10. The difference with Ubuntu 10.04 is that now you need to go first to System»Preferences»Keyboard»Layouts and add the default Greek layout. Since you have two keyboard layouts, the 'Keyboard Indicator applet' appears automatically on the panel, and you can follow the rest of the guide above.

Some people that use Greek Polytonic prefer a different keyboard layout that comes from something called the TLG(?) and is common to those who study biblical Greek. Have a look at [http://ntresources.com/unicode.htm](http://ntresources.com/unicode.htm) and [http://www.frame-poythress.org/poythress_articles/2007KeyboardGreekHebrew.htm](http://www.frame-poythress.org/poythress_articles/2007KeyboardGreekHebrew.htm) for more.

---

### Post by Catbells on 2010-09-23
I'm working under a couple of difficulties :-?. I'm not very used to Ubuntu and I'm just starting to learn Japanese.

It wasn't easy to find this thread using the Yahoo search engine.  I started with the Ubuntu Help pages where the latest instructions are for version 8 and I installed lots of SCIM.  I've uninstalled SCIM, maybe not enough, maybe too much.  When I first opened iBus Preferences, I copied all the text from the warning message to clipboard without really understanding what I was going to do with it.  iBus Preferences opened fine and I thought that all was well and used copy and paste do some searches for the images that didn't appear in the posts.  Re-opening  iBus Preferences didn't bring back the message, neither did re-installing so I can't do as recommended by Bruno.Braga.

My problems: I want to write 'watashi wa' so that it looks like [SIZE=4]&#31169;&#12399;[/SIZE] but I get[SIZE=5] &#31169;&#36650; [/SIZE]:confused: and repeatedly pressing Alt+Shift+L won't get Japanese characters into this post, though the words are highlighting as I type as though iBus is doing something.  Otokonohito comes out fine as &#30007;&#12398;&#20154;  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]


:)  Bruno.Braga thank you, thank you for providing your wonderful How To.  :)

---

### Post by bruno.braga on 2010-09-23
> **Catbells said:**
> When I first opened iBus Preferences, I copied all the text from the warning message to clipboard without really understanding what I was going to do with it.  iBus Preferences opened fine and I thought that all was well and used copy and paste do some searches for the images that didn't appear in the posts.  Re-opening  iBus Preferences didn't bring back the message, neither did re-installing so I can't do as recommended by Bruno.Braga.

Hum... there are some tricky parts for the iBus to work fine in Ubuntu, as it is not "ready for use" by default. This is kind of expected because multiple languages support is minority among users. If you install the japanese version of Ubuntu, all this problem should be already solved.

I never had probles as you reported, and I re-created my computers many times following the same pattern without any problems. I have a script to do that for me located [here]("http://code.google.com/p/linscripts/source/browse/trunk/ubuntu-fresh-install.sh"), but I extracted the iBus part and pasted here:

1) Install the original Ubuntu from CD
2) Install adiditional packages:
```
sudo apt-get install ibus ibus-table ibus-gtk ibus-anthy
```
3) Setup auto-start for iBus (by script, but you can do it manually as explained in previous comments in this thread):
```

# Fix iBus issues (maybe will need to manually add to startup)
echo '
# fix iBus issues on start
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus' >> ~/.bashrc

# create auto-start for iBus
mkdir -p ~/.config/autostart/
echo '
[Desktop Entry]
Type=Application
Exec=ibus-daemon -d
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=iBus
Name=iBus
Comment[en_US]=
Comment=
' > ~/.config/autostart/ibus-daemon.desktop

```
4) Configure iBus once it is running
Go to the keyboard icon on the top right of the Ubuntu (default location), right-click -> Preferences

This is what I do every time.

> **Catbells said:**
> My problems: I want to write 'watashi wa' so that it looks like [SIZE=4]&#31169;&#12399;[/SIZE] but I get[SIZE=5] &#31169;&#36650; [/SIZE]:confused: and repeatedly pressing Alt+Shift+L won't get Japanese characters into this post, though the words are highlighting as I type as though iBus is doing something.  Otokonohito comes out fine as &#30007;&#12398;&#20154;  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

:)  Bruno.Braga thank you, thank you for providing your wonderful How To.  :)

Hum... the problem here is japanese language input method rules, not Ubuntu. Some typing characteristics differ from the spoken format, in this case, the "watashi wa" actually must be typed as "watasi ha", so that you will get the result you expect. In this case because the "wa" is an exception preposition, which must be written as "ha" instead (even the hiragana is different). Just Google "japanese keyboard input" and you will find information about it.

Bruno

---

### Post by zaphod777 on 2010-09-23
> **Catbells said:**
> I'm working under a couple of difficulties :-?. I'm not very used to Ubuntu and I'm just starting to learn Japanese.

It wasn't easy to find this thread using the Yahoo search engine.  I started with the Ubuntu Help pages where the latest instructions are for version 8 and I installed lots of SCIM.  I've uninstalled SCIM, maybe not enough, maybe too much.  When I first opened iBus Preferences, I copied all the text from the warning message to clipboard without really understanding what I was going to do with it.  iBus Preferences opened fine and I thought that all was well and used copy and paste do some searches for the images that didn't appear in the posts.  Re-opening  iBus Preferences didn't bring back the message, neither did re-installing so I can't do as recommended by Bruno.Braga.

My problems: I want to write 'watashi wa' so that it looks like [SIZE=4]&#31169;&#12399;[/SIZE] but I get[SIZE=5] &#31169;&#36650; [/SIZE]:confused: and repeatedly pressing Alt+Shift+L won't get Japanese characters into this post, though the words are highlighting as I type as though iBus is doing something.  Otokonohito comes out fine as &#30007;&#12398;&#20154;  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]


:)  Bruno.Braga thank you, thank you for providing your wonderful How To.  :)

Your actually over thinking it. When you read &#31169;&#12399; it sounds like "watashi wa" but when typing it you actually type "watashi ha" since the &#12399; = ha.

---

### Post by Catbells on 2010-09-24
Hooray ! Hooray ! Hooray

I'm writing in Japanese and I don't have to cheat in the writing exercises of my course.

Thank you :KS     [SIZE=3]**Zaphod**[/SIZE]     :KS

---

### Post by marwell2 on 2010-09-27
How to make Hanzi (the ones showing up during typing using iBus with pinyin input module) bigger? Changing settings of iBus into another font or another size doesn't change anything here.

I am using Kubuntu 10.4. I use qtcurve as design. Changing fontsizes in KDE doesn't change it. Hmm, I have no idea, where to start. Did anybody change the size of the Hanzi showing up und this is only under my system configurataion a problem?

Found some info about changing [FONT=monospace]"[/FONT].gtrc-2.0-kde4", which I did as well, restarted iBus - but no effect taking place.

&#32769;&#30524;&#26127;&#33457;&#12288;:-)

Thanks! Marcus

---

### Post by putonghua73 on 2010-12-11
Hi folks,

I decided to wipe WinXP from my Samsung NC10 netbook, and install Ubuntu 10.04 since Anki appears to work with this version (complete fail for me using Ubuntu 8.10).

Unfortunately, my issue is with IBus. If the keyboard icon for character input is diplayed, absolutely nothing happens if I select pinyin input i.e. no language bar appears. If I restart IBus, more often than not, I have no input window.

I have already:
1. Installed Chinese language pack via System / Administration / Language Support
2. I have selected the Keyboard input method system as IBus via System / Administration / Language Support
3. I have installed Chinese - Pinyin via System / Preferences / IBus preferences / Input Method
4. I have added the IBus daemon to my Startup Application Preferences
5. I have appended the following to the end of my .bashrc file and rebooted:
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
6. The following are the newest versions (sudo apt-get):
ibus
ibus-table
ibus-gtk
ibus-anthy

It is 02:41 in the morning, and I have spent over an hour trying to get Chinese input to work with IBus and am almost pulling my hair out in frustration, not to mention, in seriously danger of waking up my neighbours by hurling expletives across my apartment.

Any help gratefully accepted! 

Thanks, people :)

---

### Post by zaphod777 on 2010-12-11
> **putonghua73 said:**
> Hi folks,

I decided to wipe WinXP from my Samsung NC10 netbook, and install Ubuntu 10.04 since Anki appears to work with this version (complete fail for me using Ubuntu 8.10).

Unfortunately, my issue is with IBus. If the keyboard icon for character input is diplayed, absolutely nothing happens if I select pinyin input i.e. no language bar appears. If I restart IBus, more often than not, I have no input window.

I have already:
1. Installed Chinese language pack via System / Administration / Language Support
2. I have selected the Keyboard input method system as IBus via System / Administration / Language Support
3. I have installed Chinese - Pinyin via System / Preferences / IBus preferences / Input Method
4. I have added the IBus daemon to my Startup Application Preferences
5. I have appended the following to the end of my .bashrc file and rebooted:
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
6. The following are the newest versions (sudo apt-get):
ibus
ibus-table
ibus-gtk
ibus-anthy

It is 02:41 in the morning, and I have spent over an hour trying to get Chinese input to work with IBus and am almost pulling my hair out in frustration, not to mention, in seriously danger of waking up my neighbours by hurling expletives across my apartment.

Any help gratefully accepted! 

Thanks, people :)

Do you get a little keyboard icon in your upper right hand corner? If so you can click that to change the input language. Then you can select the preferences and bind a key combo to turn it on and off. I have my window key set to enable or disable it.

I have attached some screenshots.

---

### Post by putonghua73 on 2010-12-12
> **zaphod777 said:**
>  Then you can select the preferences and bind a key combo to turn it on and off

Solved! Thank you very much, zaphod777! I didn't realise that you had to bind the input to a key combo to turn it on/off. I was clicking the keyboard icon, *then* selecting the input language and wondering why it wasn't working.

<slaps head>

This problem is eerily similar to the one I had when I first used a live CD of Intrepid Ibex [8.10] on my desktop. My keyboard [input] didn't work. I spent over 4 hours racking my brains why I couldn't get a simple input device to work; hurling expletives across my apartment *before* it dawned upon me to check my peripheral set-up in BIOS. A quick enable/disable USB legacy devices (or something similar) and problem solved!

Lessons learnt:
[LIST=1]
[*]The problem was/is *usually* simple - tendency to overanalyse when it was a simple configuration change
[*]_Never_ attempt any installation in the late evening / early morning
[/LIST]

Cheers!

P.s. Just noticed that you [Zaphod777] live in Japan. Arigatou gozaimasu! &#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;! My ex-girlfriend lived/lives in Japan, and it never failed to amuse her when I used to greet the Watsons staff with 'Ohayo gozaimasu!', or over-use 'Arigato gozaimasu!'.

---

### Post by zaphod777 on 2010-12-12
> **putonghua73 said:**
> Solved! Thank you very much, zaphod777! I didn't realise that you had to bind the input to a key combo to turn it on/off. I was clicking the keyboard icon, *then* selecting the input language and wondering why it wasn't working.

<slaps head>

This problem is eerily similar to the one I had when I first used a live CD of Intrepid Ibex [8.10] on my desktop. My keyboard [input] didn't work. I spent over 4 hours racking my brains why I couldn't get a simple input device to work; hurling expletives across my apartment *before* it dawned upon me to check my peripheral set-up in BIOS. A quick enable/disable USB legacy devices (or something similar) and problem solved!

Lessons learnt:
[LIST=1]
[*]The problem was/is *usually* simple - tendency to overanalyse when it was a simple configuration change
[*]_Never_ attempt any installation in the late evening / early morning
[/LIST]

Cheers!

lol, glad I could help!

---

