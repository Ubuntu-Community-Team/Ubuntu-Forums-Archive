---
title: "Japanese Input"
date: 2009-11-07
forum: General Help
---

### Post by BeingLostMayVary on 2009-11-07
Hello all. I was needing some help with a problem today. That being Japanese input as you might of guessed from the title. I've tried SKIM but it does not work very well. Now I found a thing called Im-Ja which I tried the instructions from here <https://help.ubuntu.com/community/ImJa> . Although I got the first step done, I tried to then do the part about the gtk-2.0. This didn't work. I had to find the file for it in usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules. I tried to edit that file but it said it wouldn't write even though I had the permissions. I'll give you what it said to me "For file /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules no back up copy could be created before saving . If an error occurs while saving, you might lose the data of this file. A reason could be that the media you write to is full or the directory of the file is read-only for you." Then it has options such as 'Try to Save Nevertheless'. So right now I'm at a loss of what I can do. Any possible ideas to why this is? If this doesn't work is there another besides SKIM and Im-Ja for Japanese input out there? Thanks for any help in the future.

---

### Post by vambo on 2009-11-07
Don't know which version you're running, but new with Karmic is Ibus, a new input method for Linux - so it says. I run Xubuntu, it's under settings. I don't know the Gnome equivalent. I found SCIM to be OK, if a little clunky in use. I tried Im-Ja ages ago, but could never stop it conflicting with SCIM.
Note the new Ibus thingy needs a package called Ibus-Anthy. To be honest I can't see much improvement over SCIM/Anthy. Then again I've only used it briefly.
As for editing the immodules file, all I can think of is that you'll have to be root to edit it. I don't recall having this problem when I tried im-ja.

---

### Post by BeingLostMayVary on 2009-11-07
> **vambo said:**
> Don't know which version you're running, but new with Karmic is Ibus, a new input method for Linux - so it says. I run Xubuntu, it's under settings. I don't know the Gnome equivalent. I found SCIM to be OK, if a little clunky in use. I tried Im-Ja ages ago, but could never stop it conflicting with SCIM.
Note the new Ibus thingy needs a package called Ibus-Anthy. To be honest I can't see much improvement over SCIM/Anthy. Then again I've only used it briefly.
As for editing the immodules file, all I can think of is that you'll have to be root to edit it. I don't recall having this problem when I tried im-ja.

Well I updated to Karmic last night. I saw that IBus thing tried to get it to work but could not get the Japanese input to come up. As well with the im-ja I'm the root at the moment so I don't think thats the problem. So I don't really know.

---

### Post by TWO on 2009-11-30
I never managed to get iBus working under Kubuntu Karmic Koala, so I completely uninstalled it and now I use Scim/Skim instead which is working just fine. 

Firstly, remove all instances of iBus with your package manager. Next, make sure you install Japanese through the **Regional and Language** option in Kubuntu 9.10's settings menu. Next, make sure you have selected all the necessary scim/skim packages especially the ones which enable input into qt/qt4 programs- handy for skype, etc.

Follow the simple instructions from the following:

[http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu](http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu)

Remember to change the locale to your own when asked to in those instructions. so, whilst en_US is detailed here, change it to en_GB if your system language is set to British English, etc. 

Also, add the following to the bottom of your .bashrc file (accessed by ```
kate .bashrc
``` in Kubuntu) with your prefered text editing program:

```
 
export GTK_IM_MODULE=skim
export XMODIFIERS=@im=skim
export QT_IM_MODULE=skim
```I recommend installing Microsoft fonts for Japanese as found [here]("http://www.linux.ryukent.co.uk/show.php?id=18#External%20Fonts"). The installing the fonts is possible through the settings menu and Font Installer in Kubuntu 9.10. 

Save, then restart and voila, the SKIM bar should appear when you're ready to type in Japanese with a strike of ctrl + spacebar.

&#12415;&#12435;&#12394;&#12373;&#12435;&#12289;&#38929;&#24373;&#12387;&#12390;&#12367;&#12384;&#12373;&#12356;!

TWO

---

### Post by Zorael on 2009-11-30
Your obvious alternatives are **SCIM**/**Skim**, **I-Bus** and **UIM**; each will use **Anthy** to provide support for Japanese.

Skim is a frontend for SCIM, but it's old and based on Qt3. Moreover SCIM is supposedly dead-ish upstream, and has some issues with dead keys not working (^~` etc). SCIM does not otherwise have a Qt4 frontend, so you're stuck with Qt3 or GTK+. If you're not using any other Qt3 apps, you may want to just use the GTK+ one (SCIM's own), so as not to need to install extra libraries you won't otherwise have use for.

I-Bus (Intelligent Input Bus) is the new up-and-coming alternative. I hear it's the new default in Ubuntu 9.10? It's fairly early in development, so it's missing some functionality. Like SCIM it has issues with dead keys, and like SCIM it doesn't have any Qt4 frontend.

UIM seems to have been around for a longer time, and has plenty of functionality. Dead keys work in it, albeit it seems to get some of them wrong when output as standalone characters (umlauts, acute accent). **(edit)** It, however, has a Qt4 frontend (toolbar, settings, ...).

Beware, long - starting with the basics.

--------------------------------------------

For some common app functions - like "web browser", "java", "flash plugin", etc - Ubuntu and other distributions that work under the [Freedesktop.org](http://www.freedesktop.org/wiki/) guidelines keep a set of *alternatives*, to allow a user (or a system administrator) to set the default app which should be used for that app function. In other words, by changing the web browser alternative, you change what web browser should be considered *the default*. The environment (GNOME, KDE, Xfce, ...) may in turn impose its own defaults, which may cause inconsistencies, so these alternatives aren't always followed to the letter.

The current alternative for something, or "which alternative of this thing is currently set to be the default", is saved in **/etc/alternatives** as a symlink to what they refer to. So the symlink **/etc/alternatives/_x-www-browser_** should technically be linking to the web browser you consider to be your default. User-specific settings work in a similar fashion, though they're saved in **~/.alternatives/**. To change an alternative, you use the command **update-alternatives**. Example;
```
$ sudo update-alternatives --config x-www-browser
There are 3 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
  0            /usr/bin/konqueror          100       auto mode
**[COLOR="Green"]* 1            /usr/bin/chromium-browser   40        manual mode[/COLOR]**
  2            /usr/bin/firefox-3.5        40        manual mode
  3            /usr/bin/konqueror          100       manual mode

Press enter to keep the current choice[*], or type selection number:
```
Like "web browser", it also keeps an app function for input methods (there is probably a better word than "app function"). As such, you could install a whole bunch of input methods, and then decide which one should be used by default upon X startup. This setting may be system-wide, requiring sudo permissions to change it, or it may be user-specific. When you install an input method's package, it will also install its own little file into **/etc/X11/xinit/xinput.d/**, and then register it *as an alternative*.

So to set an input method as the default, you merely have to change what alternative is to be used. You can either use update-alternatives, or use **im-switch**, which is a input method-only frontend to update-alternatives. And to follow through, update-alternatives just manages the symlinks, keeping track of what alternatives are available and what priorities they have. Additionally, **im-switch** keeps its user-specific settings in **~/.xinput.d/**, rather than in **~/.alternatives/**.

In the case of input methods, the settings are per locale, so that a Japanese locale can use UIM/SCIM/IBus/etc, while a standard English locale can do without loading it into memory.
```
$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
No private "/home/zorael/.xinput.d/en_US or /home/zorael/.xinput.d/all_ALL" is defined.
=======================================================
[B][COLOR="Green"]The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to uim[/COLOR][/B]
default - priority 10
default-xim - priority 0
ibus - priority 60
none - priority 0
scim - priority 60
scim-bridge - priority 60
uim - priority 0
uim-systray - priority 0
uim-toolbar - priority 0
uim-toolbar-qt - priority 0
Current `best' version is ibus.
=======================================================
The available input method configuration files are:
/usr/bin/find: `/home/zorael/.xinput.d': No such file or directory
default default-xim ibus ibus.dpkg-old none scim scim-bridge scim-immodule th-xim uim uim-systray uim-toolbar uim-toolbar-qt
=======================================================
```

With no input methods installed, the input method alternative points to a file conviently enough named **default** (displayed above) - again, located in **/etc/X11/xinit/xinput.d/**. It doesn't contain any environment variable definitions (or rather, they're empty), and such X just figures that it should use its own standard and dumb input method. And as mentioned earlier, upon installing an input method it installs its own file to the same location, and registers it as an alternative. Depending on what priority the package manager has set it to have, it may become the system-wide default at this point.

So really, after having installed the one you like, you should really just have to do '**im-switch -c**' in a terminal and set it to be your default. Prepend it with **sudo** to make it the system-wide setting.
```
$ im-switch -c

There are 13 candidates which provide IM for /home/zorael/.xinput.d/en_US:

  Selection    Alternative
  -----------------------------------------------
      1        default
      2        default-xim
      3        ibus
      4        ibus.dpkg-old
      5        none
      6        scim
      7        scim-bridge
      8        scim-immodule
      9        th-xim
**[COLOR="Green"] +    10        uim[/COLOR]**
      11        uim-systray
      12        uim-toolbar
      13        uim-toolbar-qt
System wide default for en_US (or all_ALL) locale is marked with [+].
Press enter to keep the current selection[*], or type selection number:
```
Then you pick what you want, log out and back in. If you want to set the alternative for a specific locale *if other than the current*, make the command '**im-switch -z lang_LANG -c**', where **lang_LANG** is the language code for the locale in question.
```
$ im-switch **[COLOR="Green"]-z ja_JP[/COLOR]** -c
```
Now, in the case of Skim, its xinput.d file (meaning; **/etc/X11/xinit/xinput.d/_skim_**) is malconfigured. If you don't correct it, SCIM won't work in certain apps, like OpenOffice.org and xterm. I have reported this to Launchpad, and it strikes me to require only a simple change in the packaging, but it's been hitherto ignored.

The lines in green have to be changed to look like they do here. If you have Skim installed, you'll see that some of them are blank.
```
[B][COLOR="Green"]XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"[/COLOR][/B]

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```

The Ubuntu wiki pages for several of these input methods hype them as the only one that will work with all apps. I have tested SCIM, UIM and IBus, and I can attest that they all seem to work with everything (GTK, Qt, XIM), provided the correct configuration.

To find out if everything seems to be configured correctly, refer to what '**im-switch -l**' says about which xinput.d file is set to be the default alternative, and then see if the variables in that file seem sane (not empty). You can also enter the following in a terminal to see if they have been read properly in that current session.
```
$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
**[COLOR="Green"]GTK: uim, Qt: uim, XMOD: @im=uim[/COLOR]**
```
That output should be the same as what the environment variables in your chosen xinput.d file defines them to be.

---

### Post by TWO on 2009-12-23
Contrary to my previous post, I've just uninstalled **SKIM **due to an annoying problem where I occasionally am unable to input text into certain windows. I remember experiencing this problem intermittently in the past and so I'd recommend going for the other input options. I'm going to try iBus again and failing that, UIM...

---

### Post by ubun_two on 2009-12-23
I am running Karmic with iBus.  The Japanese input works fine for me.

Make sure to choose iBus in Language Support.  Then do iBus Preference where you can choose to load Anthy.

---

### Post by Zorael on 2009-12-23
@**TWO**;

Yeah, I've had that happen with SCIM a few times, which was actually why I started looking into the alternatives. I'm running UIM now and I'm happy with it.

And it *does* have a Qt4 toolbar! Joy.

---

### Post by TWO on 2009-12-26
> **Zorael said:**
> @**TWO**;

Yeah, I've had that happen with SCIM a few times, which was actually why I started looking into the alternatives. I'm running UIM now and I'm happy with it.

And it *does* have a Qt4 toolbar! Joy.

What steps did you take to get UIM up and running. As it stands I have the bar but when I switch the options, I don't get Japanese input...

Edit: Well, I have ubuntu-desktop installed and **iBus** works fine with **Ubuntu**. Why it doesn't work with **Kubuntu** I'll never know. Another example of Kubuntu playing second fiddle to Ubuntu. :-(

---

### Post by Zorael on 2009-12-30
> **TWO said:**
> What steps did you take to get UIM up and running. As it stands I have the bar but when I switch the options, I don't get Japanese input...

Edit: Well, I have ubuntu-desktop installed and **iBus** works fine with **Ubuntu**. Why it doesn't work with **Kubuntu** I'll never know. Another example of Kubuntu playing second fiddle to Ubuntu. :-(
The instructions in my earlier post should be enough to get it going, or so I hope? Maybe I missed something.

Basically you need;
[list=1][*]all necessary packages installed
[*]your xinput alternative set to the input method you want (im-switch -c)
[*]your xinput file properly configured (usually non-issue, causes it to work in some apps but not all)
[*]your input method properly set up in its configuration tool
[*]panel/toolbar running if it isn't autostarted[/list]

The '**echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS**' command should tell you if you have steps 2 and 3 done. As for packages, you'll just have to scan what's available in KPackageKit or Synaptics or whatever. UIM needs uim-qt for Qt apps, uim-xim for XIM apps, uim-gtk2.0 for GTK apps - and similar for IBus/SCIM. Configuration tools are input method-specific, and panel/toolbar behavior varies.

---

