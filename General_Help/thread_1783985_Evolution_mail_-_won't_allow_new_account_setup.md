---
title: "Evolution mail - won't allow new account setup"
date: 2011-06-16
forum: General Help
---

### Post by Quackers on 2011-06-16
I have been using evolution for my email for about a year.
It currently has 2 accounts set up.
I want to create a third account so I went to Edit > Preferences > Accounts > Add
On the first page I click on "forward" and on the second page enter the new details. New name, new email address and when I'm finished I click on forward again and the second screen comes up. It has some server details on it iirc. 
Sadly after 2 seconds or so this screen disappears and the very first screen re-appears (where the only thing to click on is "forward").

What's happening? Is 2 accounts the maximum? Any clues please?
Thanks.

---

### Post by Quackers on 2011-06-16
I didn't find anything about 2 being the maximum accounts for evolution yet. It can't be, surely?

---

### Post by plucky on 2011-06-17
> **Quackers said:**
> I didn't find anything about 2 being the maximum accounts for evolution yet. It can't be, surely?

I have 2 POP and 2 IMAP

You could try to start evolution in a terminal and see if that produces any error messages when you try to create a new account.

Good Luck

---

### Post by Quackers on 2011-06-17
As I'm using Oneiric Ocelot maybe I should post in that forum.
This is what I get from opening evolution in the terminal
```
ocelot2@ocelot2-VGN-AR51SU:~$ evolution
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)


(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 755x0, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EAlertBar's child GtkBox 0x7f991b1d1d80. Allocation is 755x1, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkBox's child GtkHBox 0x7f991b1d1e60. Allocation is 12x1, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkHBox's child GtkVBox 0x7f991b1ee080. Allocation is 1x1, but minimum required size is 0x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 755x0, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 1660x0, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EAlertBar's child GtkBox 0x7f991b1d1d80. Allocation is 1660x1, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkBox's child GtkHBox 0x7f991b1d1e60. Allocation is 12x1, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkHBox's child GtkVBox 0x7f991b1ee080. Allocation is 1x1, but minimum required size is 0x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 1660x0, but minimum required size is 12x45.
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)


(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 1660x0, but minimum required size is 12x45.

(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 1660x0, but minimum required size is 12x45.
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)


(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 1660x0, but minimum required size is 12x45.
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

(evolution:7255): Gtk-WARNING **: Failed to load type module: (null)


(evolution:7255): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate EMailShellContent's child EAlertBar 0x7f991b1b06a0. Allocation is 1660x0, but minimum required size is 12x45.
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': evolution: undefined symbol: menu_proxy_module_load

```
but the evolution screen opens up ok!
When trying to set up a new account I still get the same screen for 2 seconds then it reverts to the first screen again.
Thanks for the info plucky :-)

---

