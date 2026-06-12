---
title: "Language support problem"
date: 2009-12-03
forum: General Help
---

### Post by guriinii on 2009-12-03
When I open Language Support it wants to install new packages and gives me the error: 

Could not apply changes!
Fix broken packages first.

But I have no broken packages. I then ran 'gnome-language-selector' in Terminal and got this:

richard@richard-desktop:~$ gnome-language-selector
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/SimpleGtkbuilderApp.py:40: RuntimeWarning: missing handler 'on_combobox_locale_chooser_changed'
  self.builder.connect_signals(self)
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/SimpleGtkbuilderApp.py:40: RuntimeWarning: missing handler 'on_button_apply_system_wide_clicked'
  self.builder.connect_signals(self)
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:871: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:838: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]

Can anyone help?

---

### Post by gabo.cr on 2009-12-03
Did you check Synaptic for any broken packages?
I think a bug was reported with a similar or same problem?

---

### Post by guriinii on 2009-12-03
I've already done that. There wasn't any. I'm stumped

---

### Post by guriinii on 2009-12-04
I know this sounds desperate but, help me, please!

---

### Post by gabo.cr on 2009-12-04
Try this commands in Terminal one by one:
(It will ask you for your password)

sudo apt-get --configure -a

sudo apt-get -f install

sudo apt-get --fix-missing install

sudo apt-get clean

sudo apt-get update


Let me know if that helped.
;)

---

### Post by guriinii on 2009-12-05
NOPE, I got this after trying language support:

E: Could not open file /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_i18n_Translation-en%5fGB - open (2: No such file or directory)
E: Could not open file /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_jaunty_universe_i18n_Translation-en%5fGB - open (2: No such file or directory)
E: Could not open file /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_i18n_Translation-en%5fGB - open (2: No such file or directory)
E: Could not open file /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_jaunty_main_i18n_Translation-en%5fGB - open (2: No such file or directory)
E: Internal error opening cache (3). Please report.


Does this mean this repo doesn't exist and therefore can't update lang support?

---

### Post by gabo.cr on 2009-12-05
Did you get this problem after an upgrade of Ubuntu or a new installation?

---

### Post by guriinii on 2009-12-05
It was a new installation.

---

### Post by bodidd on 2009-12-14
Same error here on two upgrades.  Upgraded a Sony Vaio and an Asus X71SL together.  Both had the same issue but the Sony recovered gracefully when i clicked on System->Administration->Language Support

On the Asus, i tried to run /usr/bin/gnome-language-support and got the same gtk errors listed here and then the entire system froze.

---

### Post by rykel on 2010-09-06
I am also unable to install additional languages in Lucid - this is a terrible BUG!!!

Same error message - "Unable to install... fix broken packages first" - but there are NO broken packages.

---

### Post by rykel on 2010-09-06
I found the solution. I had an OpenOffice PPA and the Ubuntu Language packages are unable to work with it. I removed the PPA and solved the problem already.    ):P

---

