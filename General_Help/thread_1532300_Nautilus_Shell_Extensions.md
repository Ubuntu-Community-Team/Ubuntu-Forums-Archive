---
title: "Nautilus Shell Extensions?"
date: 2010-07-16
forum: General Help
---

### Post by JoeSolo on 2010-07-16
In development on Micro$oft platforms, there is the concept of registering shell extensions for linking particular files with an application and including context menu items specific to file types.

I have written a simple Perl script for decrypting my bank statements using the CLI ecrypt utility.  However, I cannot successfully open these *.emc files with my Perl script from my email or from Nautilus (works perfectly if I do it via Terminal).

Do you guys know of a guide or tutorial on writing programs and linking these into Gnome / Nautilus as a "Shell Extension"; and please tell me what the right terminology is.

Thanks

---

### Post by gzarkadas on 2010-07-16
In any nautilus window, select the `Help' menu. When the help window opens go to the `Extending Nautilus' item of the list that shows up.

You should also install the nautilus-actions package. After the installation there will be a new item, `Configure Nautilus Actions' (or similar) in your `System|Preferences' menu

There are a lot of ready-made scripts for nautilus; see [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php) for a starter. 

You can also find information in the nautilus-actions project page, [http://www.grumz.net/index.php?q=taxonomy/term/2/9](http://www.grumz.net/index.php?q=taxonomy/term/2/9).

You can also have a look at [thread]1522635[/thread], where there are some practical examples.

In your case you just have to make a nautilus action for *.emc files that will call your script (make it executable with #!/usr/bin/perl ). Use `%M' as the script's command line in the relevant field of the nautilus actions gui; there is a `legend' button on the right of this textbox that describes the possible nautilus-actions parameters.

---

