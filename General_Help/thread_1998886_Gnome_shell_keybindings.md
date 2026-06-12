---
title: "Gnome shell keybindings"
date: 2012-06-07
forum: General Help
---

### Post by morits on 2012-06-07
I'm trying to change keybinding for moving through workspaces in gnome 3, from the default (ctrl + alt + down / up) to something else.

I've tried googling a while however I've been unable to find a solution.

Ive tried changing the keyboard shortcuts in system settings, and in ccsm but this does not work. Does anyone know how to change these keybindings? any help would be appriciated :)

thanks

---

### Post by traditionalist on 2012-06-07
The "standard" tool in GNOME for this is Gconf -editor;

```
sudo apt-get install gconf-editor
```[http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME](http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME)

 


You can also change some keybindings using compiz . Get it here;

[[IMG]http://img233.imageshack.us/img233/9936/ubuntusoftwarecenter006.th.png[/IMG]]("http://img233.imageshack.us/i/ubuntusoftwarecenter006.png/")

You need to use the CompizConfig Settings Manager.  It is not that easy to use, and  can crash occasionally. You will get a warning when you start it;

[[IMG]http://img39.imageshack.us/img39/5543/40433058.th.png[/IMG]]("http://img39.imageshack.us/i/40433058.png/")

It is best to heed that warning and not try to do too much at once.

Click on "General Options" first for more info;

[[IMG]http://img59.imageshack.us/img59/9255/compizconfigsettingsman.th.png[/IMG]]("http://img59.imageshack.us/i/compizconfigsettingsman.png/")

Sometimes it seems not to work, but you can  change a lot with it. Often a restart is required before changes take effect.

---

### Post by Frogs Hair on 2012-06-07
The Gnome Shell wont work with the CCSM .  I have no key bindings listed in the move to workspace down option on the Gnome shell title bars . I do have a workspace switcher extension and also use the right pain in the overview for changing work spaces.

---

### Post by traditionalist on 2012-06-07
> **Frogs Hair said:**
> The Gnome Shell wont work with the CCSM .  I have no key bindings listed in the move to workspace down option on the Gnome shell title bars . I do have a workspace switcher extension and also use the right pain in the overview for changing work spaces.

Works for me.  But gconf-editor is better.

---

### Post by traditionalist on 2012-06-07
Also a good idea to get GConf cleaner;

[[IMG]http://img339.imageshack.us/img339/6880/ubuntusoftwarecenter009.th.png[/IMG]](http://img339.imageshack.us/i/ubuntusoftwarecenter009.png/)

---

### Post by Frogs Hair on 2012-06-07
> **traditionalist said:**
> Works for me.  But gconf-editor is better.

I know it works in classic , but the last I read the CCSM was incompatible with the shell . That must have changed . ;)

---

### Post by traditionalist on 2012-06-07
> **Frogs Hair said:**
> I know it works in classic , but the last I read the CCSM was incompatible with the shell . That must have changed . ;)

Some of these things change daily!  I am constantly being surprised, and sometimes frustrated, because something that worked yesterday doesn't work today! :)

I spent almost an hour looking for a utility I knew I had only to discover that the last update changed the name!  You can't find something if you don't know what it is, ( one of my major gripes with Unity).

---

### Post by morits on 2012-06-07
Thanks for the tips :)

> **traditionalist said:**
> The "standard" tool in GNOME for this is Gconf -editor;

```
sudo apt-get install gconf-editor
```[http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME](http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME)


So I tried this, and looked for the keybinding at: 
/->apps->metacity->global_keybindings

Where I found that switch_to_workspace_up and switch_to_workspace_down where already set to <super>UP / <super>DOWN, however ctrl + alt + down still switches workspace and super + down does nothing

Am I looking at the wrong place? none of the other keybindings at: /->apps->metacity->* seems related.

---

