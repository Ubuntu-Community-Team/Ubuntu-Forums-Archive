---
title: "Customising Login/Greeter Screen 10.04"
date: 2010-06-03
forum: General Help
---

### Post by bbqau on 2010-06-03
Hello,

I am trying to change my login screen for 10.04 system wide unsuccesfully at the moment. I have searched the web multiple times and in the process have installed a range of programs to do so each being unsuccessful.

So far i have installed [http://www.miketech.net/gnome-art/](http://www.miketech.net/gnome-art/)
Splash Manger
Ubuntu Tweak
Using Stock Installed System->Admin->Login Screen ( no option shown for theme )

None of these have worked. I have downloaded the following Splash Screens
[http://www.junauza.com/2009/04/15-beautiful-ubuntu-gdm-themes.html](http://www.junauza.com/2009/04/15-beautiful-ubuntu-gdm-themes.html)
And would like to use the very first one however i cannot get it working. Installing it as a Theme does not work as i receive unrecognised file format, supposedly using Splash Manager you install the Screenshot.png and thats it, however clicking the install does absolutely nothing. As of current my login splash screen is Edubuntu which i installed via apt-get when installing a bunch of themes. 

Just so you know i can change the background image using Ubuntu Tweak ( [http://blog.ubuntu-tweak.com/2010/02/02/ubuntu-tweak-0-5-1-released-support-10-04-lucid.html](http://blog.ubuntu-tweak.com/2010/02/02/ubuntu-tweak-0-5-1-released-support-10-04-lucid.html) ) however i cannot apply the changes that full themed logins such as the one above apply.

I have looked through 
**/usr/share/gdm** for configuration files that suggest or make reference to the login screen with no success. 

I have also looked through 
**/usr/share/gnome-splashscreen-manager** and found that a glade interface file, which is of no use in this instance.

All i wish to do is change the login/splash screen for my install - not my grub one but the normal Ubuntu one - which i cannot seem to be able to achieve.

Just so you know the splash screen theme (Ubuntu Black) i have downloaded from - [http://www.junauza.com/2009/04/15-beautiful-ubuntu-gdm-themes.html](http://www.junauza.com/2009/04/15-beautiful-ubuntu-gdm-themes.html) 

Is of the .tar.gz file format and contains the following files

```

aurora-theme.xml
background.jpg
btn1.png
btn1_pressed.png
btn2.png
btn2_pressed.png
btn3.png
btn3_pressed.png
GdmGreeterTheme.desktop
screenshot.png
window_shadow.png

```So how do i install this and set it as my login screen in replacement of the current one.

---

### Post by dcstar on 2010-06-03
> **bbqau said:**
> Hello,

I am trying to change my login screen for 10.04 system wide unsuccesfully at the moment. I have searched the web multiple times and in the process have installed a range of programs to do so each being unsuccessful.
........

Use the **ubuntu-tweak** package.

---

### Post by bbqau on 2010-06-03
I have Installed the Ubuntu-Tweak Package, it does not allow GDM from gnome-look to be installed. All it allows is to change the background image and the Icon. Not the Layout of the Login Screen 

eg... [http://3.bp.blogspot.com/_UqUwVPikChs/SfBmiBXgooI/AAAAAAAAI4o/VbHr8lzXmmY/s1600/Ubuntu-Black.jpg](http://3.bp.blogspot.com/_UqUwVPikChs/SfBmiBXgooI/AAAAAAAAI4o/VbHr8lzXmmY/s1600/Ubuntu-Black.jpg)

Thanks for the Suggestion Anyway

---

### Post by Spr0k3t on 2010-06-03
I hear you bbqau.  The problem is, ever since the changes made to GDM it b0rk3d the theming.  The only way I have found to be able to do a retheme is to build the theme yourself using the information found withing the many dizzying web sites.  However, the best graphical application I've found for the new GDM was [GDM2](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html).  It covers a bit, but not enough... at least it's a start in the right direction. 

@dcstar: Ubuntu-Tweak is not the answer.

---

### Post by bbqau on 2010-06-03
Yeap i hear you to mate, i just installed that and it certainly does not provide the information needed. I have downloaded a nice tutorial booklet on customising however i don't think its relevant to lucid either. That GDM2 manager does not provide the real ability to modify the login screen.

As i mentioned previously i found a glade file which i assume is the login interface making use of the Gtk. I am considering hacking it and determining whether or not it makes any difference to the login panel. If it does then there may be a manual hack of some kind to customise the login theme.

Its a real annoyance when some of the most common things ( theme changes ) to the entire system are a really not a simple matter. There is no relevant documentation as of yet on how this can be done. All of the Current Utility Applications also seem not to be working. I cannot even find the simple image that is currently used on my login screen. At least if i could find that i would be able to begin working backwards and work out what does what etc...

The file i am interested in is gtkrc found in /usr/share/gdm/themes/Edubuntu which i have determined to be the current login screen **i am pretty sure** it contains the following code
```
# Ubuntu Human Colorscheme
#
# Authors:
# Richard Stellingwerff <remenic@gmail.com>
# Daniel Borgmann <daniel.borgmann@gmail.com>
# Billy Cantrell <bvcmdk@yahoo.com>
#
# Feel free to modify and share!

gtk-icon-theme-name = "gartoon"

style "clearlooks-default"
{
    GtkButton      ::default_border    = { 0, 0, 0, 0 }
    GtkRange       ::trough_border     = 0
    GtkPaned       ::handle_size       = 6
    GtkRange       ::slider_width      = 15
    GtkRange       ::stepper_size      = 15

    GtkScrollbar   ::min_slider_length = 35
    GtkCheckButton ::indicator_size    = 14
    GtkMenuBar     ::internal-padding  = 0
    GtkTreeView    ::expander_size     = 14
    GtkExpander    ::expander_size     = 16
    GtkScale       ::slider-length     = 31
    # GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
    # GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
    # GtkScrollbar   ::has-secondary-forward-stepper = 1
    # GtkScrollbar   ::has-secondary-backward-stepper = 1

    GtkButton      ::child-displacement-x = 0
    GtkButton      ::child-displacement-y = 0

    xthickness = 1
    ythickness = 1

    GtkTreeView::odd_row_color = "#F4F0EC"
    GtkTreeView::even_row_color = "#FFFFFF"

    fg[NORMAL]        = "#101010"
    fg[PRELIGHT]      = "#000000"
    fg[ACTIVE]        = "#000000"
    fg[SELECTED]      = "#ffffff"
    fg[INSENSITIVE]   = "#B3AFAB"

    bg[NORMAL]        = "#efebe7"
    bg[PRELIGHT]      = "#f5f3f0"
    bg[ACTIVE]        = "#E1D9D1"
    bg[SELECTED]      = "#a0180f" # d6722d
    bg[INSENSITIVE]   = "#EBE7E3"

    base[NORMAL]      = "#ffffff"
    base[PRELIGHT]    = "#ffffff"
    base[ACTIVE]      = "#E1D9D1"
    base[SELECTED]    = "#fb8b00" # FFD799
    base[INSENSITIVE] = "#EBE7E3"

    text[NORMAL]      = "#000000"
    text[PRELIGHT]    = "#000000"
    text[ACTIVE]      = "#000000"
    text[SELECTED]    = "#000000"
    text[INSENSITIVE] = "#B3AFAB"

    engine "ubuntulooks" 
    {
        menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
        menuitemstyle     = 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
        listviewitemstyle = 1       # 0 = flat, 1 = 3d-ish (gradient)
        progressbarstyle  = 1       # 0 = candy bar, 1 = fancy candy bar, 2 = flat
        animation         = FALSE
    }
}

# Evolution (and some deprecated widgets) use bg and fg for its listview instead of 
# base and text like they should, so we override it.
style "evolution-hack" = "clearlooks-default"
{    
    bg[ACTIVE]   = "#E1D9D1"
    bg[SELECTED] = "#FFD799"
    fg[ACTIVE]   = "#000000"
    fg[SELECTED] = "#000000"
}


style "clearlooks-wide" = "clearlooks-default"
{
    xthickness = 2
    ythickness = 2
}

style "clearlooks-wider" = "clearlooks-default"
{
    xthickness = 3
    ythickness = 3
}

style "clearlooks-button" = "clearlooks-wider"
{
    bg[PRELIGHT] = "#f5f3f0"
    bg[ACTIVE]   = "#d9d3cc"
}

style "clearlooks-notebook" = "clearlooks-wide"
{
    bg[NORMAL]      = "#efebe5"
    bg[ACTIVE]      = "#d0c8c1"
    bg[INSENSITIVE] = "#efebe5"
}

style "clearlooks-tasklist" = "clearlooks-default"
{
    xthickness = 5
    ythickness = 3
}

style "clearlooks-menu" = "clearlooks-default"
{
    xthickness = 2
    ythickness = 1
    bg[NORMAL] = "#f8f5f2"
}

style "clearlooks-menubar-item" = "clearlooks-button"
{
    fg[PRELIGHT] = "#000000"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
    xthickness = 2
    ythickness = 3
    bg[SELECTED] = "#fb8b00" # FFD799
    fg[PRELIGHT] = "#000000"
    text[PRELIGHT] = "#000000"
}

style "clearlooks-tree" = "clearlooks-wide"
{
}

style "clearlooks-frame-title" = "clearlooks-default"
{
    fg[NORMAL] = "#404040"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
    xthickness = 4
    ythickness = 4
    bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-progressbar" = "clearlooks-wide"
{
    xthickness = 2
    ythickness = 2
    fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

style "metacity-frame" = "clearlooks-default"
{
    bg[SELECTED] = "#a0180f" # CC863E
}


# widget styles
class "GtkWidget"      style "clearlooks-default"
class "GtkButton"      style "clearlooks-button"
class "GtkCombo"       style "clearlooks-button"
class "GtkRange"       style "clearlooks-wide"
class "GtkFrame"       style "clearlooks-wide"
class "GtkMenu"        style "clearlooks-menu"
class "GtkEntry"       style "clearlooks-wider"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
class "MetaFrames"     style "metacity-frame"
class "GtkWindow"      style "metacity-frame"

widget_class "*MenuItem.*" style "clearlooks-menu-item"
widget_class "*MenuItem.*ProgressBar*" style "clearlooks-default"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton"    style "clearlooks-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget "gtk-tooltips" style "clearlooks-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "clearlooks-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "clearlooks-notebook"

# these should really use base and text colors instead
widget_class "*GtkCTree*" style "evolution-hack"
widget_class "*GtkList*" style "evolution-hack"
widget_class "*GtkCList*" style "evolution-hack"
widget_class "*.ETree.*" style "evolution-hack"
```

---

### Post by Spr0k3t on 2010-06-03
I believe it is a glade file which houses all of the data.  Especially since the system does use the GTK interface.  Here's a quick hack I've found that might help:

> 1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using Ctrl+ALT+F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM&#8217;s font, theme and background image.
9. Close the gnome-control-center and login normally.

Perhaps finding/creating the GTK theme and then modifying the theme as mentioned would get you closer.

---

### Post by bbqau on 2010-06-03
Yep thats what i am working towards at the moment. I found a nice tutorial written that i might work through and try developing my own theme 

[http://www.mediafire.com/?2yimyo3ow3t](http://www.mediafire.com/?2yimyo3ow3t)

You can download the pdf from there 

Original thread can be found [http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by bbqau on 2010-06-03
Just installed Glade and opened up the /usr/share/gnome-splashscreen-manager/glade/gnome_splashscreen_manager.glade and it is not what i thought it was. Its the splash screen manger ui
[img]http://i47.tinypic.com/24cb041.png[/img]

So yep, thats a dead end now :(

---

### Post by bbqau on 2010-06-05
Just an update i have searched tirelessly and still have not found a solution for this customisation issue. If anyone has anything i have not tried in the above thread - please let me know ;)

---

### Post by wojox on 2010-06-05
Did you try Spr0k3t suggestion?

You can't install login wallpaper from Gnome or anyplace else.

But you can change the wallpaper with Spr0k3t's post.

---

### Post by rotten777 on 2010-06-05
This kind of issue is exactly the loose end that makes Ubuntu and linux in general look bad.

I hope the change to gdm was worth losing functionality.

---

### Post by bbqau on 2010-06-05
Yea it is quite annoying - sure there is a way to do it - it is simply not super duper simple and may require some extra skills ;)

---

### Post by Carlo1973 on 2010-07-29
I to have ran into this issue.

 From what discovered, this isn't a feature that was removed by any distribution. Its a feature that was either accidentally or intentionally removed from GDM 2.28.  Ubuntu, Mint, or any distribution using the latest gdm stable version, will experience difficulties with changing the login theme.  Gnome has a listing on their website which shows which distributions are using what version of GDM. I don't think its possible to revert to an older GDM version without breaking things in Gnome. Mind you I've never tried it so don't quote me on this. 

I'm okay if this feature is going to be gone for awhile, only if they plan on re-implementing it in a future update, or if they are currently doing a re-write of the theme code for gdm 3.0. I'm not sure what the developers are planning at this moment. I know - based on what I've read, that they have gotten a lot of heat over the issue. It would be awesome to get some feedback on this to see if a planned gdm 2.3x+ version will have capabilities re-instated, or if we need to wait for Gnome 3.0, or if we're just holding our breaths for a feature that will never be placed back. If thats the case, I'm going KDE LOL For that matter might as well go Enlightenment (E17). Just wish E17 was Compositing - or is it?

Gnome 3.0 (aka Gnome Live!) should be tentatively released by November based on the information I'm seeing on their website: [http://live.gnome.org/TwoPointThirtyone](http://live.gnome.org/TwoPointThirtyone)   - However when it's adopted by Ubuntu or any other distribution is another matter entirely.

---

### Post by bbqau on 2010-07-31
Yea after delving into this again i discovered the same things you mentioned. I have done what i can as of current and will not bother going any further. It is something that would be nice for users to be able to do, particularly those that develop themes for gnome. I am certain that they enjoy an integrated and polish theme system and as of current its 90% there but just lacking in the last few little customisation options.

---

### Post by Carlo1973 on 2010-08-19
I suspect the feature will get reinstated by version 3.0 with additional functionality.  Gnome knows that it's users want high customization, while retaining stability and user friendliness. True to my word, I installed KDE (actually I have KDE and Gnome running on the same machine). Using KDE's display manager - KDM - I can now customize the login screen. However doing desktop configurations isn't so easy. Plasma makes things look good, but it took me way to long to get it to look the way I wanted it. Customization is great. User friendlessness - needs a bit of work. Stability is mostly there, but with all the graphical enhancements done and the introduction of Plasma, well it uses a lot of resources and it's not as stable as it could be. However, I've rarely had the actual desktop or plasma crash. It was apps that tried to utilize plasma features incorrectly that became unstable. 


So now I find I'm back in Gnome. Why? Gnome - despite appearing to be minimalist, is quite well put together. I've not had any real issues with the display manager (outside the lack of customization to the login screen), and I haven't had any real application crashes. It looks good. Its fast. Functional. To get to the software I need is quick, intuitive, and smartly laid out. I don't need my taskbar/desk-bar to look like XP or Windows 7. There is a reason why I use linux primarily over Windows. Its cause I want more functionality over glam. Having said that, I would still like to have the ability to customize my desktop, login screen, sounds, taskbar, etc etc etc, the way I want it - when I want it. Call it a matter of personal preference, personal style or identity, or whatever. To make things look the way you want it to look, without having a masters in programing.

---

### Post by red.lynx on 2010-10-06
Hey guys, maybe i skipped a post but i don't believe anyone has posted this solution yet. 
try using this in the terminal, worked for me.

gksudo -u gdm dbus-launch gnome-appearance-properties

then select the background you wish to use for your login screen. I know it looks like your typical appearance menu but trust me its for your splashscreen. Hope this helps. Unless i completely missed the point.. although I am personally concerned with changing the actual login greeting "box"? whatever you call it..

---

### Post by Carlo1973 on 2010-10-06
Hey Red.Lynx!

Good suggestion!

I to however would like to change more than just the background. I've found resources to do that, but to actually gain control of the log in dialog box, and change its appearance and screen position is what I think everyone is looking for. 

I know you can do it with KDE, but that doesn't really solve the problem.  

I'm sure the option was removed due to configuring of the knew GNOME system which is bound to be released in a few months. I'm sure once they have all the sub-systems dealing with the graphics and ensure compatibility with Compiz, that they will re-introduce something similar to what they originally had in place.  From what I've gathered from their blog, they are re-writing the code from the ground up. 

If they introduce something which is configurable, highly efficient, and basically back to what they were known to be best at, then I'll be happy with the wait until the next release of Gnome. Patience is a virtue. Also, complaining in a forum that is not on the Gnome website doesn't appear to be working, so lets try another approach lol

---

