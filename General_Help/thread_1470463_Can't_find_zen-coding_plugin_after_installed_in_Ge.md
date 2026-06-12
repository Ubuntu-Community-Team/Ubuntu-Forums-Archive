---
title: "Can't find zen-coding plugin after installed in Gedit"
date: 2010-05-02
forum: General Help
---

### Post by jazzi on 2010-05-02
[Zen-coding]("http://code.google.com/p/zen-coding/") is a great gedit plugin for html & css development

I download the [files]("http://github.com/mikecrittenden/zen-coding-gedit") and unpack them into ~/.gnome2/gedit/plugins/

After open gedit I can't find zencoding in the Gedit Preference.

how can I make it show up?

Thanks 
jazzi

---

### Post by michaelzap on 2010-05-03
> **jazzi said:**
> [Zen-coding]("http://code.google.com/p/zen-coding/") is a great gedit plugin for html & css development

I download the [files]("http://github.com/mikecrittenden/zen-coding-gedit") and unpack them into ~/.gnome2/gedit/plugins/

After open gedit I can't find zencoding in the Gedit Preference.

how can I make it show up?

Thanks 
jazzi

You have to enable it in Edit->Preferences->Plugins.

---

### Post by jazzi on 2010-05-03
Thanks Michael, but I can't find it in the Edit->Preferences->Plugins

that's weired.

---

### Post by MCrittenden on 2010-05-03
> **jazzi said:**
> Thanks Michael, but I can't find it in the Edit->Preferences->Plugins

that's weired.

What's your folder structure? You should have a zencoding.gedit-plugin file AND and zencoding/ folder in ~/.gnome2/gedit/plugins, so it's like:

```
.gnome2 (folder)
  gedit (folder)
    plugins (folder)
      zencoding (folder)
      zencoding.gedit-plugin
```

P.S. Thanks for using the plugin! I'm Mike Crittenden, the maintainer.

---

### Post by jazzi on 2010-05-03
Wow you're Mike? Thanks for your excllent work.

My file structer is ~/.gnome2/gedit/plugins/zencoding

The zencoding directory includes the following files:
> 1,zencoding (folder)
2,README.md
3,UNLICENSE.md
4,zencoding.gedit-plugin

```
#ls .gnome2/gedit/plugins/zen-coding/zencoding
filters		 my_zen_settings.py  zen_actions.py  zen_settings.py
html_matcher.py  plugin.py	     zen_core.py
__init__.py	 stparser.py	     zen_editor.py
```

anything wrong?

---

### Post by MCrittenden on 2010-05-03
> **jazzi said:**
> My file structer is ~/.gnome2/gedit/plugins/zencoding

Ahh yes, that's the problem. You're supposed to everything INSIDE the top level zencoding folder into the plugins folder, not the folder itself.

So here's what you have right now which isn't working:

```
.gnome2
  gedit
    plugins
      zen-coding
        zencoding
        zencoding.gedit-plugin
```

And here's what you need:

```
.gnome2
  gedit
    plugins
      zencoding.gedit-plugin
      zencoding/
        __init__.py
        plugin.py
        everythingelse.py
```
      
See what I mean? Just move everything in that top level zencoding folder up one level. Basically, Gedit doesn't see any plugins unless the plugin's .gedit-plugin file is a direct child of the plugins folder.

---

### Post by jazzi on 2010-05-03
It works Mike, thanks so much.

Now I can remove the Quantas Plus and use Gedit instead for coding Html.

I'll buy you a tea drink when you come to China:)

---

### Post by MCrittenden on 2010-05-03
Haha, glad it's working :). I'd love some tea!

If you spot any issues while using it, feel free to post them in the issue tracker on GitHub.

---

### Post by jazzi on 2010-05-03
> **MCrittenden said:**
> 
If you spot any issues while using it, feel free to post them in the issue tracker on GitHub.

I will thanks. Maybe someday I can send you some excellent loose leaf teas.

jazzi

---

### Post by michaelzap on 2010-05-03
Hey there, Mike. Love the plugin. Just started playing with it last night and I am really in awe of the whole concept and how much it can speed up coding.

Any chance you'll do a Geany version? Gedit is the standard text editor for Gnome, but Geany is much more comfortable for coding imho. It's listed in the wishlist on the Geany page, but that list goes on for a mile and a half.

Maybe if I can figure out how to do multi-line search and replace without having to use regedit syntax in Gedit (using \n, etc.) I can switch to it, but that's something I need to do daily and it's easy in Geany.

---

### Post by MCrittenden on 2010-05-10
> **michaelzap said:**
> Any chance you'll do a Geany version?

Probably not, just because I'm not a geany user myself. If geany supports python plugins then it should be a fairly easy port, though, if someone else wants to git it a shot.

---

### Post by michaelzap on 2010-05-10
> **MCrittenden said:**
> Probably not, just because I'm not a geany user myself. If geany supports python plugins then it should be a fairly easy port, though, if someone else wants to git it a shot.

I actually started using Gedit for coding just so that I can use your plugin. I used to use it, but a while back it developed a nasty bug when opening files over Samba. That bug seems to finally be fixed in Lucid (and I figured out that Gedit allows escape characters in regular searches and replaces), so I'm pretty happy with it at the moment.

I repeat - It's a great plugin! THANKS!

---

### Post by johnsnails on 2010-05-15
GREAT WORK!

Followed your instructions on
[http://github.com/mikecrittenden/zen-coding-gedit](http://github.com/mikecrittenden/zen-coding-gedit)

**Installation**

  
[LIST=1]
[*]Download [zip]("http://github.com/mikecrittenden/zen-coding-gedit/zipball/master")  or [tar]("http://github.com/mikecrittenden/zen-coding-gedit/tarball/master")  source and unpack it.
[*]Move zencoding.gedit-plugin and the zencoding  folder into ~/.gnome2/gedit/plugins/
[*]In Gedit, go to Edit &#8594; Preferences &#8594; Plugins to enable the plugin.
[*]Try it out using the shortcut keys listed above.
[/LIST]
Working a charm!

---

