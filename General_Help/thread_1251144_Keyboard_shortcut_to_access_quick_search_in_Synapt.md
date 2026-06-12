---
title: "Keyboard shortcut to access quick search in Synaptic"
date: 2009-08-27
forum: General Help
---

### Post by darthmob on 2009-08-27
Hi, folks! I have got a rather simple question but did not find any answers on the net. Is it possible to access the Synaptic quick search with a keyboard shortcut? It's the small field in the toolbar:

[IMG]http://www.basicconfig.com/files/imagepicker/j/jinlusuh/Screenshot-Synaptic%20quick%20search%20seamonkey.png[/IMG]

You can do normal searches with CTRL+f but they are awfully slow. A normal search can take 10-15 seconds whereas a quick search brings the results in 2-5 seconds.

Thanks a lot in advance. :)

---

### Post by darthmob on 2009-08-28
Giving this a gentle push. I know there are lots of console cowboys out there. Somebody has to know a solution!

---

### Post by nothingspecial on 2009-08-28
Does`t really answer your question but what about a keyboard shortcut to open a terminal then



```
apt-cache search [COLOR="Red"]keyword_here[/COLOR]
```

---

### Post by DaithiF on 2009-08-28
I don't think its possible -- the application doesn't define a keyboard accelerator for quick search.

below are the accelerators that are defined.  it would be simple to add a new one
```
apt-get source synaptic

```then see
```
synaptic-<version>/gtk/glade/window_main.glade
```
perhaps raise a feature request with the synaptic maintainers, attaching a patch?

```
menu_exit<accelerator key="Q" modifiers="GDK_CONTROL_MASK" signal="activate"/>
undo1<accelerator key="Z" modifiers="GDK_CONTROL_MASK" signal="activate"/>
redo1<accelerator key="Z" modifiers="GDK_CONTROL_MASK | GDK_SHIFT_MASK" signal="activate"/>
menu_find_name:q<accelerator key="F" modifiers="GDK_CONTROL_MASK" signal="activate"/>
update_package_entrys1<accelerator key="R" modifiers="GDK_CONTROL_MASK" signal="activate"/>
upgrade1<accelerator key="G" modifiers="GDK_CONTROL_MASK" signal="activate"/>
menu_proceed<accelerator key="P" modifiers="GDK_CONTROL_MASK" signal="activate"/>
menu_keep<accelerator key="N" modifiers="GDK_CONTROL_MASK" signal="activate"/>
menu_install<accelerator key="I" modifiers="GDK_CONTROL_MASK" signal="activate"/>
menu_upgrade<accelerator key="U" modifiers="GDK_CONTROL_MASK" signal="activate"/>
menu_remove<accelerator key="Delete" modifiers="0" signal="activate"/>
menu_purge<accelerator key="Delete" modifiers="GDK_SHIFT_MASK" signal="activate"/>
menu_override_version<accelerator key="E" modifiers="GDK_CONTROL_MASK" signal="activate"/>
menu_details<accelerator key="O" modifiers="GDK_CONTROL_MASK" signal="activate"/>
item1<accelerator key="F1" modifiers="0" signal="activate"/>
```

---

### Post by darthmob on 2009-08-29
> **nothingspecial said:**
> Does`t really answer your question but what about a keyboard shortcut to open a terminal then

```
apt-cache search [COLOR="Red"]keyword_here[/COLOR]
```Depending on the search it results in a massive wall of text. Thanks for the tip, though. 

> **DaithiF said:**
> I don't think its possible -- the application doesn't define a keyboard accelerator for quick search.

perhaps raise a feature request with the synaptic maintainers, attaching a patch?That's a lot of effort for such a small problem. Guess I'll take the path with the least resistance and just click the text field whenever I need it. ;)

---

