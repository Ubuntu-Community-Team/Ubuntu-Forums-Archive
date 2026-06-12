---
title: "Certain type of tooltip is unreadable"
date: 2012-07-01
forum: General Help
---

### Post by Paddy Landau on 2012-07-01
I have found a certain type of tooltip to be unreadable. I found this in Audacity. The following screen-shots show what I mean.

__________________________________________________


[SIZE=3][COLOR=DarkSlateBlue]**Tooltip type 1: Hover the mouse**[/COLOR][/SIZE]

This type of tooltip, where the mouse hovers over the item, is readable. Here are two screen-shots showing how it works in both Windows and Ubuntu.

**Windows**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=220494&stc=1&d=1341138658[/IMG]

**Ubuntu**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=220495&stc=1&d=1341138658[/IMG]
 
__________________________________________________


[SIZE=3][COLOR=DarkSlateBlue]**Tooltip type 2: Move the mouse**[/COLOR][/SIZE]

This type of tooltip, which changes as I drag the item, is unreadable. Again, two screenshots, showing how Windows works correctly whereas Ubuntu does not.

**Windows**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=220496&stc=1&d=1341138658[/IMG]

**Ubuntu**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=220497&stc=1&d=1341138658[/IMG]

__________________________________________________


I have tested this in both Ubuntu 3D and Gnome Classic (No Effects). They both show the same problem.

Do you have any idea how to fix this or if it has already been reported as a bug somewhere?

I'd also like to know if there are examples in applications other than Audacity.

---

### Post by vasa1 on 2012-07-01
> **Paddy Landau said:**
> I have found a certain type of tooltip to be unreadable. I found this in Audacity. ...
I'm not seeing that happen in an Xfce 4.10 session.

---

### Post by Paddy Landau on 2012-07-01
Interesting. Thanks for the feedback.

I decided to try on Lubuntu 12.04, and there it is black writing on dark grey. It is readable, but only with difficulty.

On Ubuntu, the theme obviously is black-on-black.

EDIT: I also tried on 11.04, but it too was black-on-black.

What colours do you have on XFCE?

---

### Post by vasa1 on 2012-07-01
> **Paddy Landau said:**
> ...
What colours do you have on XFCE?
I don't know if this answers your question but here's the image ...

---

### Post by Paddy Landau on 2012-07-01
Thanks.

I wish I could find another application with the same type of moving tool-tip. This would tell me immediately if it were a fault specifically with Audacity or (more likely) with the Ubuntu theme.

Then I could raise a bug report for it.

---

### Post by vasa1 on 2012-07-01
I'm wondering if Audacity has its own built-in styling for tooltips. What I see is not what I see for other apps, whether they're gtk2 or gtk3. Is Audacity *something else*?

---

### Post by Paddy Landau on 2012-07-01
Good question.

For the normal hover tool-tips, Audacity is consistent with other applications, from the Launcher to Nautilus to GIMP.

It is only with the moving-mouse version, where the tool-tip changes, that I have this problem. (What is the correct name for that type of tool-tip?)

I find it frustrating that I cannot find another application with the same type of moving-mouse tool-tip! Perhaps you are right, and that type of tool-tip is specific to Audacity.

I think I'll raise a question on the Audacity forum.

EDIT: I have raised this as a [question on the Audacity forum]("http://forum.audacityteam.org/viewtopic.php?f=48&t=66514").

---

### Post by vasa1 on 2012-07-01
> **Paddy Landau said:**
> ...
For the normal hover tool-tips, Audacity is consistent with other applications, from the Launcher to Nautilus to GIMP.
...
Now that you mention it, I (purposely) have different tooltip styles for gtk2 and gtk3. The normal hover tooltip of Audacity is the one I have for gtk2.

---

### Post by Paddy Landau on 2012-07-01
> **vasa1 said:**
> I (purposely) have different tooltip styles...
Ah. You can change tooltip styles? Perhaps this is the way forward. I don't know how to do it, and I guess the process on Unity is different from that on XFCE, so I'd have to ask people who use Unity.

---

### Post by vasa1 on 2012-07-01
> **Paddy Landau said:**
> Ah. You can change tooltip styles? Perhaps this is the way forward. I don't know how to do it, and I guess the process on Unity is different from that on XFCE, so I'd have to ask people who use Unity.
No, that hasn't anything to do with Xfce. Give me some time to collect my marbles and I'll be back ;)

---

### Post by vasa1 on 2012-07-01
Standard precautions apply of backing up files before messing with them.

To change the tooltip in **gtk3** apps (using the Ambiance theme as an example):

```
gksudo gedit /usr/share/themes/Ambiance/gtk-3.0/settings.ini
```

You should see:
```
[Settings]
gtk-color-scheme = "base_color:GREEN\nbg_color:#4573A0\ntooltip_bg_color:#000000\nselected_bg_color:#003263\ntext_color:black\nfg_color:#003263\ntooltip_fg_color:#666666\nselected_fg_color:LightBlue\nlink_color:#f07746\nbg_color_dark:#333333\nfg_color_dark:red"
gtk-auto-mnemonics = 1
```

All one has to do is to fiddle with the hex values corresponding to tooltip_bg_color and tooltip_fg_color. In the example above, it gives grayish text on a black background. That's it.

The same applies for gtk2 apps, except that the file to edit is
```
gksudo gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
```

Staying with the stuff right at the top of the file, we have:
```
gtk-color-scheme = "base_color:#4573a0\nfg_color:black\ntooltip_fg_color:#a2e5fb\nselected_bg_color:#003263\nselected_fg_color:#a2e5fb\ntext_color:black\nbg_color:#4573a0\ntooltip_bg_color:#000000\nlink_color:#f07746"

```
Here, I have pale blue text on gray.

---

### Post by Paddy Landau on 2012-07-01
For Unity, it seems that the file to use is
[FONT=Lucida Console]/usr/share/themes/Ambiance/gtk-2.0/gtkrc[/FONT]

I changed my background to [FONT=Lucida Console]#5f5f5f[/FONT], and that has made it visible. Unfortunately, of course, it has changed *all* tool-tips, but it seems that that is the price to pay to view the tool-tip in Audacity.

Thank you.

EDIT: Fiddling with the colours, it seems that Audacity decides that the "moving" tooltip must have black writing.

---

### Post by vasa1 on 2012-07-01
> **Paddy Landau said:**
> ... Unfortunately, of course, it has changed *all* tool-tips....
If you want, just for the "fun" of it, you can edit the other file, settings.ini, differently, and thus have two sets, one for gtk2 and one for gtk3. You will then see the difference with something like gedit which is gtk3 as opposed to Firefox, Chrome, LibreOffice and Audacity which are all gtk2.

These settings will work across Unity 2D and 3D, as well as Xfce, and GNOME.

---

### Post by Paddy Landau on 2012-07-01
> **vasa1 said:**
> If you want, just for the "fun" of it, you can edit the other file, settings.ini, differently, and thus have two sets, one for gtk2 and one for gtk3. You will then see the difference with something like gedit which is gtk3 as opposed to Firefox, Chrome, LibreOffice and Audacity which are all gtk2.
Well, I've just learned something new!

Thanks.

---

### Post by vasa1 on 2012-07-01
> **Paddy Landau said:**
> Well, I've just learned something new!

Thanks.
You're welcome :)

---

### Post by Paddy Landau on 2012-07-01
Aargh. I've just found that changing the tooltip also changes the warning message on Thunderbird about loading images; with red writing in that area, the background becomes too light.

Oh dear. Changing the tooltip background affects too many things! I shall revert to the default black background, and do without the Audacity tooltip in question.

---

### Post by vasa1 on 2012-07-01
> **Paddy Landau said:**
> Aargh. I've just found that changing the tooltip also changes the warning message on Thunderbird about loading images; with red writing in that area, the background becomes too light.

Oh dear. Changing the tooltip background affects too many things! I shall revert to the default black background, and do without the Audacity tooltip in question.

Specifically for Firefox (and presumably for TBird), you can have distinct tooltips if you want. That is done using regular CSS. I'm not at my regular PC now or I could have given you code for Firefox, hoping it would work for TBird as well.

---

### Post by vasa1 on 2012-07-02
In case you aren't thoroughly disgusted with this tooltip stuff ...

You can make Firefox have a distinctive tooltip. If you search userstyles.org for **tooltips**, you'll end up with more than you need.

I'm hoping that Thunderbird, being from Mozilla, uses similar notations.

The simplest way is to ensure that you have a folder called chrome (case-sensitive), in your Profile folder and, within that folder, a file called userContent.css (also case sensitive).

Then, at its simplest, you can have the following line:
tooltip { color: yellow !important; background: black !important; }

There are more [selectors]("http://www.w3schools.com/css/css_syntax.asp") than plain **tooltip** but this seems to do it for most of what I'm coming across in Firefox. For example, there are:
```

#btTooltip,
#un-toolbar-tooltip,
#tooltip,
.tooltip,
#aHTMLTooltip,
#urlTooltip,
tooltip,
#aHTMLTooltip,
#urlTooltip,
#brief-tooltip,
#btTooltipTextBox,
#un-toolbar-tooltip
```
according to [this style]("http://userstyles.org/styles/47626/remove-tooltips-everywhere").
I don't use TBird or any e-mail client so I don't know how complex things are there.

I'll stop here ;)

---

### Post by Paddy Landau on 2012-07-02
> **vasa1 said:**
> In case you aren't thoroughly disgusted with this tooltip stuff ...
Wow. How amazing is that! It seems you can customise just about anything.

I was a bit confused, though: where should the Profile folder go? In my home folder?

Thanks for all your information.

---

### Post by Paddy Landau on 2012-07-02
I see that this has been [reported on Audacity]("http://bugzilla.audacityteam.org/show_bug.cgi?id=518") as a bug.

The tooltip type is called click-to-see there.

---

### Post by vasa1 on 2012-07-02
> **Paddy Landau said:**
> ... where should the Profile folder go? In my home folder? ...
Speaking of Firefox and Seamonkey, the profile folder is within a dot folder, .mozilla. For example,
/home/username/.mozilla/firefox/ian3h6lc.default
and
/home/username/.mozilla/seamonkey/g8xlnvrc.default

And using the Seamonkey example, we have:
/home/userContent/.mozilla/seamonkey/g8xlnvrc.default/chrome/userContent.css

[This site]("http://www-archive.mozilla.org/unix/customizing.html") has old information but much of the basics still hold.

(I've to go back and fix _C_hrome! It should be _c_hrome!)

---

### Post by vasa1 on 2012-07-02
> **Paddy Landau said:**
> I see that this has been [reported on Audacity]("http://bugzilla.audacityteam.org/show_bug.cgi?id=518") as a bug.

The tooltip type is called click-to-see there.

My sympathies lie with the Audacity people. So many desktops, so many themes. Gale's suggestion of double-clicking works: "A workaround for now is to double-click the slider to open the fine adjustment dialogue."

And there are more bugs involving tooltips!

---

### Post by Paddy Landau on 2012-07-02
> **vasa1 said:**
> My sympathies lie with the Audacity people.
Yes, they are all volunteers. But the simplest route for them is to use the tooltip theme for tooltips instead of specifying the colour. I have already suggested that in an Audacity forum post, but perhaps I should suggest it in the bug itself.

---

