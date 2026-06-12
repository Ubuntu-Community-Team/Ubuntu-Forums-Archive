---
title: "Adding plugins to Gedit."
date: 2009-07-07
forum: General Help
---

### Post by Swerve1000 on 2009-07-07
Hi,

I am following [THIS]("http://http://www.eng.tau.ac.il/~atavory/gedit-plugins/html-tidy/#checking_probs") tutorial to try and add a plugin to Gedit.

I used the command:

```
sudo apt-get install tidy
```

Now, when I open Gedit > Edit > Preferences > Plugins

I see HTML Tidy listed, but it is greyed out. I cannot select the tickbox for it to try and activate the plugin.

What I did was download the ```
html-tidy-gedit-plugin.tar.gz
``` file to the Desktop, extract it into a folder, then I copied the file into both of these locations:

```
~/.gnome2/gedit/html-tidy.gedit-plugin
```
```
~/.gnome2/gedit/plugins/html-tidy.gedit-plugin
```

but neither works:

Then I tried to open Gedit, trying both:

```
gedit
```
```
sudo gedit
```

But it is still greyed out

How can I activate the plugin?

Thanks for any help! :)

---

### Post by fragos on 2009-07-07
You may need to use the "external tools" plugin to get access to Tidy. You will find some help Google. Search for "gedit plugins tidy". There were a number of useful looking hits on that search.

---

